# About
This is a temporary repo for testing Alpha/Beta Maia-Mailguard version 1.0.5 on FreeBSD.
Once everything is stable (code and port), the port will be submitted to the FBSD ports tree.

# Usage
There are two methods here. Either patch the ports tree or copy the directory. There is no 
need to do both. Just choose whichever is easiest for you. However, the patch is recommended 
as it also provides the security/Makefile addition of the port.

## Patching the Ports Tree
1. Make sure the ports tree is up to date
```
git -C /usr/ports pull
```
2. Apply the patch to the ports tree
```
git -C /usr/ports apply /path/to/maia-mailguard-1.0.5.patch
```

## Copy the port directory
1. Simply copy the "maial-mailguard" directory to /usr/ports/security
```
cp -a /path/to/maia-mailguard /usr/ports/security/
```
