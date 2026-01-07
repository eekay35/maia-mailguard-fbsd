PORTNAME=	maia-mailguard
DISTVERSION=	1.0.5
CATEGORIES=	security

MAINTAINER=	ek@purplehat.org
COMMENT=	Web-based management system based on amavisd-new and SpamAssassin
WWW=		https://github.com/einheit/maia_mailguard_1.05

LICENSE=	GPLv3
LICENSE_FILE=	${WRKSRC}/LICENSE.txt

RUN_DEPENDS=	p5-Archive-Zip>=0.10:archivers/p5-Archive-Zip \
		p5-Convert-TNEF>=0.08:converters/p5-Convert-TNEF \
		p5-Convert-UUlib>=1.08,1:converters/p5-Convert-UUlib \
		p5-Data-UUID>=1.148:devel/p5-Data-UUID \
		p5-forks>=0.34:devel/p5-forks \
		p5-IO-Socket-INET6>=1.27:net/p5-IO-Socket-INET6 \
		p5-IO-Stringy>=1.203:devel/p5-IO-Stringy \
		p5-MIME-Tools>=4.116:mail/p5-MIME-Tools \
		p5-Net-CIDR-Lite>=0.18:net/p5-Net-CIDR-Lite \
		p5-Net-Server>=0.93:net/p5-Net-Server \
		p5-Template-Toolkit>=2.13:www/p5-Template-Toolkit \
		p5-Text-CSV>=1.02:textproc/p5-Text-CSV \
		p5-Unix-Syslog>=0.94:sysutils/p5-Unix-Syslog

USES=		perl5 shebangfix

USE_GITHUB=	yes
GH_ACCOUNT=	einheit
GH_PROJECT=	maia_mailguard_1.05
GH_TAGNAME=	Final

USE_PERL5=	run
USE_RC_SUBR+=	maiad

NO_ARCH=	yes
NO_BUILD=	yes

SUB_FILES=	maiad pkg-message
SUB_LIST+=	ETCDIR="${ETCDIR}" \
		GROUPS="${GROUPS}" \
		USERS="${USERS}"

DOCS=		LICENSE.txt README.md files/maia-mysql-freebsd.sql \
		files/maia-pgsql.sql

USERS=		vscan
GROUPS=		vscan

PEAR_DIR?=	${LOCALBASE}/share/pear
PLIST_SUB+=	GROUPS="${GROUPS}" \
		USERS="${USERS}" \
		WWWGRP="${WWWGRP}" \
		WWWOWN="${WWWOWN}"

OPTIONS_DEFINE=	APACHE ARC ARJ BDB CAB CLAMAV CRYPT DKIM DOCS DOMAINKEYS \
		DOVECOT FILE IPCOUNTRY LHA LIGHTTPD LOCAL LZOP MYSQL NGINX \
		NOMARCH PFA PGSQL POSTFIX RAR RPM SPAMASSASSIN SPF TNEF UNARJ \
		UNRAR UNZOO WEBHOST ZOO

OPTIONS_DEFAULT=	ARC ARJ BDB CAB CLAMAV DKIM DOCS DOMAINKEYS FILE \
			IPCOUNTRY LHA MYSQL RPM SPAMASSASSIN SPF UNRAR ZOO
OPTIONS_SUB=		yes

ARC_DESC=		ARC support with archivers/arc
ARJ_DESC=		ARJ support with archivers/arj
BDB_DESC=		Use BerkeleyDB
CAB_DESC=		CAB support with archivers/cabextract
CLAMAV_DESC=		Use ClamAV anti-virus
CRYPT_DESC=		Encryption support
DKIM_DESC=		SpamAssassin DKIM plugin
DOMAINKEYS_DESC=	SpamAssassin DomainKey plugin
DOVECOT_DESC=		Use Dovecot IMAP/POP3
FILE_DESC=		Use newer file(1) utility from ports
IPCOUNTRY_DESC=		SpamAssassin IP Country plugin
LHA_DESC=		LHA support with archivers/lha
LIGHTTPD_DESC=		Use LighTTPD web server
LOCAL_DESC=		All services/databases hosted locally
LZOP_DESC=		LZOP support with archivers/lzop
MYSQL_DESC=		Use MySQL
NGINX_DESC=		Use Nginx web server
NOMARCH_DESC=		ARC support with archivers/nomarch
PFA_DESC=		Use Postfixadmin
PGSQL_DESC=		Use PgSQL
POSTFIX_DESC=		Use Postfix MTA
RAR_DESC=		RAR support with archivers/rar
RPM_DESC=		RPM support with archivers/rpm2cpio
SPAMASSASSIN_DESC=	Use SpamAssassin
SPF_DESC=		SpamAssassin SPF plugin
TNEF_DESC=		Add external tnef decoder
UNARJ_DESC=		ARJ support with archivers/unarj
UNRAR_DESC=		RAR support with archivers/unrar
UNZOO_DESC=		ZOO support with archivers/unzoo
WEBHOST_DESC=		PHP, PEAR, etc... for Maia web interface
ZOO_DESC=		ZOO support with archivers/zoo

APACHE_USES+=			apache:run
ARC_RUN_DEPENDS+=		arc:archivers/arc
ARJ_RUN_DEPENDS+=		arj:archivers/arj
BDB_RUN_DEPENDS+=		p5-BerkeleyDB>=0:databases/p5-BerkeleyDB
CAB_RUN_DEPENDS+=		cabextract:archivers/cabextract
CLAMAV_RUN_DEPENDS+=		clamd:security/clamav
CRYPT_RUN_DEPENDS+=		p5-Crypt-Blowfish>=0:security/p5-Crypt-Blowfish \
				p5-Crypt-CBC>=0:security/p5-Crypt-CBC \
				p5-Crypt-OpenSSL-RSA>=0:security/p5-Crypt-OpenSSL-RSA
DKIM_RUN_DEPENDS+=		p5-Mail-DKIM>=0:mail/p5-Mail-DKIM
DOMAINKEYS_RUN_DEPENDS+=	p5-Mail-DomainKeys>=0:mail/p5-Mail-DomainKeys
DOVECOT_RUN_DEPENDS+=		dovecot:mail/dovecot
FILE_RUN_DEPENDS+=		file>=4.21:sysutils/file
IPCOUNTRY_RUN_DEPENDS+=		p5-IP-Country>=0:net/p5-IP-Country
LHA_RUN_DEPENDS+=		lha:archivers/lha
LIGHTTPD_RUN_DEPENDS+=		lighttpd:www/lighttpd
LZOP_RUN_DEPENDS+=		lzop:archivers/lzop
MYSQL_RUN_DEPENDS+=		${DBD_MYSQL}
MYSQL_USES+=			mysql:client
NGINX_RUN_DEPENDS+=		nginx:www/nginx
NOMARCH_RUN_DEPENDS+=		nomarch:archivers/nomarch
PFA_RUN_DEPENDS+=		postfixadmin33-${PHP_FLAVOR}>=0:mail/postfixadmin33
PFA_USES+=			php
PGSQL_RUN_DEPENDS+=		p5-DBD-Pg>=0:databases/p5-DBD-Pg
PGSQL_USES+=			pgsql
POSTFIX_RUN_DEPENDS+=		postfix:mail/postfix
RAR_RUN_DEPENDS+=		rar:archivers/rar
RPM_RUN_DEPENDS+=		rpm2cpio.pl:archivers/rpm2cpio
SPAMASSASSIN_RUN_DEPENDS+=	spamassassin>=0:mail/spamassassin
SPF_RUN_DEPENDS+=		p5-Mail-SPF>=0:mail/p5-Mail-SPF
TNEF_RUN_DEPENDS+=		tnef:converters/tnef
UNARJ_RUN_DEPENDS+=		unarj:archivers/unarj
UNRAR_RUN_DEPENDS+=		unrar:archivers/unrar
UNZOO_RUN_DEPENDS+=		unzoo>=4.4_1:archivers/unzoo
WEBHOST_RUN_DEPENDS+=		${LOCALBASE}/lib/php/${PHP_EXT_DIR}/scrypt.so:security/pecl-scrypt@${PHP_FLAVOR} \
				${LOCALBASE}/share/smarty3-${PHP_FLAVOR}/Smarty.class.php:www/smarty3@${PHP_FLAVOR} \
				${PEAR_DIR}/Auth/SASL.php:security/pear-Auth_SASL@${PHP_FLAVOR} \
				${PEAR_DIR}/DB.php:databases/pear-DB@${PHP_FLAVOR} \
				${PEAR_DIR}/Image/Canvas.php:graphics/pear-Image_Canvas@${PHP_FLAVOR} \
				${PEAR_DIR}/Image/Color.php:graphics/pear-Image_Color@${PHP_FLAVOR} \
				${PEAR_DIR}/Image/Graph.php:graphics/pear-Image_Graph@${PHP_FLAVOR} \
				${PEAR_DIR}/Log.php:sysutils/pear-Log@${PHP_FLAVOR} \
				${PEAR_DIR}/Mail/mime.php:mail/pear-Mail_Mime@${PHP_FLAVOR} \
				${PEAR_DIR}/Mail/mimeDecode.php:mail/pear-Mail_mimeDecode@${PHP_FLAVOR} \
				${PEAR_DIR}/Net/IMAP.php:mail/pear-Net_IMAP@${PHP_FLAVOR} \
				${PEAR_DIR}/Net/POP3.php:net/pear-Net_POP3@${PHP_FLAVOR} \
				${PEAR_DIR}/Net/SMTP.php:net/pear-Net_SMTP@${PHP_FLAVOR} \
				${PEAR_DIR}/Net/Socket.php:net/pear-Net_Socket@${PHP_FLAVOR} \
				${PEAR_DIR}/Numbers/Roman.php:textproc/pear-Numbers_Roman@${PHP_FLAVOR} \
				${PEAR_DIR}/Numbers/Words.php:textproc/pear-Numbers_Words@${PHP_FLAVOR} \
				${PEAR_DIR}/Pager/Pager.php:devel/pear-Pager@${PHP_FLAVOR}
WEBHOST_USES+=			php
WEBHOST_USE+=			PHP=bcmath,ctype,dom,gettext,iconv,imap,mbstring,mcrypt,pdo,pdo_mysql,pdo_sqlite,posix,session,simplexml,sockets,sqlite3,tokenizer,xml,xmlreader,xmlrpc,xmlwriter
ZOO_RUN_DEPENDS+=		zoo>=2.10.1_2:archivers/zoo

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MMYSQL} && ${PORT_OPTIONS:MLOCAL}
USES+=		mysql:server,client
RUN_DEPENDS+=	${DBD_MYSQL}
.endif
.if ${PORT_OPTIONS:MMYSQL} && ${PORT_OPTIONS:MWEBHOST}
USE_PHP+=	mysqli
.endif
.if ${PORT_OPTIONS:MPGSQL} && ${PORT_OPTIONS:MLOCAL}
WANT_PGSQL=	server
.endif
.if ${PORT_OPTIONS:MPGSQL} && ${PORT_OPTIONS:MWEBHOST}
USE_PHP+=	pgsql
.endif

.include <bsd.port.pre.mk>

post-patch:
	(cd ${WRKSRC}/freebsd/cfg_template && ${REINPLACE_CMD} \
		-e 's|/usr/local/etc/mail|${LOCALBASE}/etc/mail|g' \
		-e 's|/usr/local/etc/maia-mailguard|${ETCDIR}|g' \
		-e 's|/usr/local/share/maia-mailguard|${DATADIR}|g' \
		-e 's|/usr/local/www/maia-mailguard|${WWWDIR}|g' \
		maiad.conf.tmpl \
		maia.conf.tmpl \
		config.php.tmpl \
	)

do-install:
.if ${PORT_OPTIONS:MWEBHOST}
	${MKDIR} ${STAGEDIR}${WWWDIR} ${STAGEDIR}${WWWDIR}/cache
	cd ${WRKSRC}/php && ${COPYTREE_SHARE} . ${STAGEDIR}${WWWDIR}
	${LN} -s ${PREFIX}/share/smarty3-${PHP_FLAVOR} ${STAGEDIR}${WWWDIR}/libs/Smarty
.for m in ${WRKSRC}/themes/desert_sand ${WRKSRC}/themes/dgm \
	${WRKSRC}/themes/ocean_surf
	${MKDIR} ${STAGEDIR}${WWWDIR}${m}/compiled
.endfor
.endif
	${MKDIR} ${STAGEDIR}${DATADIR} ${STAGEDIR}${DATADIR}/scripts \
		${STAGEDIR}${ETCDIR}/templates
	cd ${WRKSRC}/freebsd/maia_scripts && ${COPYTREE_SHARE} . ${STAGEDIR}${DATADIR}/scripts
	cd ${WRKSRC}/freebsd/scripts && ${COPYTREE_SHARE} . ${STAGEDIR}${DATADIR}/scripts
	cd ${WRKSRC}/freebsd/extras && ${COPYTREE_SHARE} . ${STAGEDIR}${DATADIR}/scripts
.for a in digest.tpl newuser.tpl reminder.tpl
	${INSTALL} -m 644 ${WRKSRC}/maia_templates/${a} ${STAGEDIR}${ETCDIR}/templates
.endfor
	${INSTALL_SCRIPT} ${WRKSRC}/freebsd/sbin/maiad ${STAGEDIR}${PREFIX}/sbin
	${INSTALL} -m 640 ${WRKSRC}/freebsd/cfg_template/maiad.conf.tmpl ${STAGEDIR}${ETCDIR}/maiad.conf
	${INSTALL} -m 640 ${WRKSRC}/freebsd/cfg_template/maia.conf.tmpl ${STAGEDIR}${ETCDIR}/maia.conf
	${INSTALL} -m 640 ${WRKSRC}/freebsd/cfg_template/config.php.tmpl ${STAGEDIR}${WWWDIR}/config.php

do-install-DOCS-on:
	${MKDIR} ${STAGEDIR}${DOCSDIR}
.for i in ${DOCS}
	${INSTALL_DATA} ${WRKSRC}/${i} ${STAGEDIR}${DOCSDIR}
.endfor

.include <bsd.port.post.mk>
