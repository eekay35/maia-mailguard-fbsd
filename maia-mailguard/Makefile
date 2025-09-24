PORTNAME=	maia-mailguard
DISTVERSION=	1.0.5-alpha3
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
GH_TAGNAME=	alpha3

USE_PERL5=	run
USE_RC_SUBR+=	maiad

SHEBANG_FILES=	files/maiad maia_scripts/configtest.pl \
		maia_scripts/detectvba.pl \
		maia_scripts/expire-quarantine-cache.pl \
		maia_scripts/load-sa-rules.pl maia_scripts/maiadbtool.pl \
		maia_scripts/process-quarantine.pl maia_scripts/resend.pl \
		maia_scripts/send-quarantine-digests.pl \
		maia_scripts/send-quarantine-reminders.pl \
		maia_scripts/stats-snapshot.pl scripts/inline-edit.sh

NO_ARCH=	yes
NO_BUILD=	yes

SUB_FILES=	maiad pkg-message
SUB_LIST+=	ETCDIR=${ETCDIR} \
		GROUPS=${GROUPS} \
		MAIAHOME=${MAIAHOME} \
		MAIAQUARANTINE=${MAIAQUARANTINE} \
		USERS=${USERS}

DOCS=		LICENSE.txt README.md cfg_tpl/maiad.conf.tmpl \
		files/maia-mysql.sql files/maia-pgsql.sql \
		cfg_tpl/maia.conf.tmpl

USERS=		vscan
GROUPS=		vscan

MAIAHOME=		/var/maiad
MAIAQUARANTINE?=	/var/maiad/virusmails

PEAR_DIR?=	${LOCALBASE}/share/pear
PLIST_SUB+=	GROUPS="${GROUPS}" \
		USERS="${USERS}" \
		WWWGRP="${WWWGRP}" \
		WWWOWN="${WWWOWN}"

OPTIONS_DEFINE=	APACHE ARC ARJ BDB CAB CLAMAV CRYPT DKIM DOCS DOMAINKEYS \
		DOVECOT2 FILE IPCOUNTRY LHA LIGHTTPD LOCAL LZOP MYSQL NGINX \
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
DOVECOT2_DESC=		Use Dovecot 2.x IMAP/POP3
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

APACHE_USES=			apache:run
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
DOVECOT2_RUN_DEPENDS+=		dovecot:mail/dovecot
FILE_RUN_DEPENDS+=		file>=4.21:sysutils/file
IPCOUNTRY_RUN_DEPENDS+=		p5-IP-Country>=0:net/p5-IP-Country
LHA_RUN_DEPENDS+=		lha:archivers/lha
LIGHTTPD_RUN_DEPENDS+=		lighttpd:www/lighttpd
LZOP_RUN_DEPENDS+=		lzop:archivers/lzop
NGINX_RUN_DEPENDS+=		nginx:www/nginx
NOMARCH_RUN_DEPENDS+=		nomarch:archivers/nomarch
PFA_RUN_DEPENDS+=		postfixadmin-${PHP_FLAVOR}>=0:mail/postfixadmin
PFA_USES=			php
PGSQL_RUN_DEPENDS+=		p5-DBD-Pg>=0:databases/p5-DBD-Pg
PGSQL_USES=			pgsql
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
WEBHOST_USES=			php
WEBHOST_USE=			pdo_sqlite,posix,session,simplexml,sockets,sqlite3,tokenizer, \
				PHP=,bcmath,ctype,dom,gettext,iconv,imap,mbstring,mcrypt,pdo \
				xml,xmlreader,xmlrpc,xmlwriter
ZOO_RUN_DEPENDS+=		zoo>=2.10.1_2:archivers/zoo

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MMYSQL} && ${PORT_OPTIONS:MLOCAL}
USES+=		mysql:server,client
RUN_DEPENDS+=	${DBD_MYSQL}
.endif
.if ${PORT_OPTIONS:MMYSQL} && !${PORT_OPTIONS:MLOCAL}
USES+=		mysql:client
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
.for m in maia_scripts/configtest.pl maia_scripts/detectvba.pl \
	maia_scripts/expire-quarantine-cache.pl maia_scripts/load-sa-rules.pl \
	maia_scripts/maiadbtool.pl maia_scripts/process-quarantine.pl \
	maia_scripts/resend.pl maia_scripts/send-quarantine-digests.pl \
	maia_scripts/send-quarantine-reminders.pl maia_scripts/stats-snapshot.pl
	${REINPLACE_CMD} -e "s|/etc/maia/maia.conf|${ETCDIR}/maia.conf|" \
		${WRKSRC}/${m}
.endfor

.for i in maia_templates/digest.tpl maia_templates/newuser.tpl \
	maia_templates/reminder.tpl
	${MV} ${WRKSRC}/${i} ${WRKSRC}/${i}.dist
.endfor

	${REINPLACE_CMD} -e "s|daemon_user  = 'maia'|daemon_user  = '${USERS}'|" \
		-e "s|daemon_group = 'maia'|daemon_group = '${GROUPS}'|" \
		-e "s|/var/lib/maia|${MAIAHOME}|" \
		${WRKSRC}/cfg_tpl/maiad.conf.tmpl

	${REINPLACE_CMD} -e "s|/etc/maia.conf|${ETCDIR}/maia.conf|" \
		-e "s|username = 'maia'|username = '${USERS}'|" \
		-e "s|/var/lib/maia|${DATADIR}|" \
		-e "s|/usr/bin/sa-learn|${PREFIX}/bin/sa-learn|" \
		-e "s|local_cf_dir = undef|local_cf_dir = '${PREFIX}/etc/mail/spamassassin'|" \
		-e "s|user_rules_dir = undef|user_rules_dir = '${MAIAHOME}/.spamassassin'|" \
		-e "s|template_dir = '/etc/maia/templates/'|template_dir = '${ETCDIR}/templates/'|" \
		${WRKSRC}/cfg_tpl/maia.conf.tmpl

	${REINPLACE_CMD} -e "s|/etc/maia/maiad.conf|${ETCDIR}/maiad.conf|" \
		-e "s|/var/lib/maia|${DATADIR}|" \
		${WRKSRC}/files/maiad

	${FIND} -E ${WRKSRC} \( -iregex '.*(bak|~)$$' -o -iregex '.*(git|~)$$' \
		-o -iregex '.*(orig|~)$$' \) -delete

do-install:
	${MKDIR} ${STAGEDIR}${WWWDIR} ${STAGEDIR}${WWWDIR}/web
	cd ${WRKSRC}/php && ${COPYTREE_SHARE} . ${STAGEDIR}${WWWDIR}
.if ${PORT_OPTIONS:MWEBHOST}
	${LN} -s ${PREFIX}/share/smarty3-${PHP_FLAVOR} ${STAGEDIR}${WWWDIR}/libs/Smarty
.endif
	${MKDIR} ${STAGEDIR}${DATADIR}
	cd ${WRKSRC}/maia_scripts && ${COPYTREE_SHARE} . ${STAGEDIR}${DATADIR}/scripts
	cd ${WRKSRC}/scripts && ${COPYTREE_SHARE} . ${STAGEDIR}${DATADIR}/scripts
	${MKDIR} ${STAGEDIR}${ETCDIR}/templates
.for a in digest.tpl newuser.tpl reminder.tpl
	${INSTALL} -m 644 ${WRKSRC}/maia_templates/${a}.dist ${STAGEDIR}${ETCDIR}/templates
.endfor
	${INSTALL_SCRIPT} ${WRKSRC}/files/maiad ${STAGEDIR}${PREFIX}/sbin
	${INSTALL} -m 640 ${WRKSRC}/cfg_tpl/maiad.conf.tmpl ${STAGEDIR}${ETCDIR}/maiad.conf.dist
	${INSTALL} -m 640 ${WRKSRC}/cfg_tpl/maia.conf.tmpl ${STAGEDIR}${ETCDIR}/maia.conf.dist

do-install-DOCS-on:
	${MKDIR} ${STAGEDIR}${DOCSDIR}
.for i in ${DOCS}
	${INSTALL_DATA} ${WRKSRC}/${i} ${STAGEDIR}${DOCSDIR}
.endfor

.include <bsd.port.post.mk>
