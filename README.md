# 4d-plugin-curl
This is a 4D plugin implementation of [libcurl and cURL](http://curl.haxx.se).

Important
---
This plugin project is a forked subset of what was published as [OAuth](https://github.com/miyako/4d-plugin-oauth).

Existing cURL@ commands have the same name and functionality, but their tokens (internal IDs) have changed.

To migrate existing methods, do the following:

1. Comment the code that calls cURL@ plugin commands.
2. Close 4DB.
3. Replace the plugin.
4. Uncomment the code.
 
New
---
**cURL Get executable**

Returns the path to the curl executable embedded in the plugin. You can use this with LAUNCH EXTERNAL PROCESS.

Example
---
```
$version:=cURL Get version 
  //libcurl/7.40.0 OpenSSL/1.0.1j zlib/1.2.8 libidn/1.28 libssh2/1.4.3

$path:=cURL Get executable 

$stdOut:=""
$stdIn:=""
$stdErr:=""

LAUNCH EXTERNAL PROCESS($path+" -V";$stdIn;$stdOut;$stdErr);
  //curl 7.40.0 (x86_64-apple-darwin14.0.0) libcurl/7.40.0 OpenSSL/1.0.1j zlib/1.2.8 libidn/1.29 libssh2/1.4.3\nProtocols: dict file ftp ftps gopher http https imap imaps ldap ldaps pop3 pop3s rtsp scp sftp smb smbs smtp smtps telnet tftp \nFeatures: IDN IPv6 Largefile NTLM NTLM_WB SSL libz TLS-SRP UnixSockets \n
```

Version
---
* v14 is for v14 and above, Windows & OS X 10.8+ 32/64 bits.
* v11 is for v11 and above, Windows 32/64 bits, OS X 10.6+ 32 bits (Intel only)

Dependencies
---

The libary version has been updated.

**Mac OS X**

* libcurl/7.40.0
* OpenSSL/1.0.1j 
* zlib/1.2.8 
* libidn/1.29 
* libssh2/1.4.3
 
**Windows**

* libcurl/7.40.0
* OpenSSL/1.0.1j
* zlib/1.2.8
* libidn/1.29
* libssh2/1.4.3

|Protocol|Mac OS X|Windows|
|:-------:|:-:|:-----:|
|dict|◯|◯|
|file|◯|◯|
|ftp|◯|◯|
|ftps|◯|◯|
|gopher|◯|◯|
|http|◯|◯|
|https|◯|◯|
|imap|◯|◯|
|imaps|◯|◯|
|ldap|◯|◯|
|ldaps|◯|◯|
|pop3|◯|◯|
|pop3s|◯|◯|
|rtsp|◯|◯|
|scp|◯|◯|
|sftp|◯|◯|
|smtp|◯|◯|
|smtps|◯|◯|
|telnet|◯|◯|
|tftp|◯|◯|

|Feature|Mac OS X|Windows|
|:-----:|:-:|:-----:|
|IDN|◯|◯|
|IPv6|◯||
|Largefile|◯|◯|
|NTLM|◯|◯|
|SSL|◯|◯|
|libz|◯|◯|

Remarks
---
On Mac, SSH2 is linked to the system OpenSSL located at /usr/lib/, not the one embedded in the plugin. [This is to avoid crash with SFTP](http://forums.4d.fr/Post/FR/15200699/1/15251183).

LIBCURL is modified so that it will yield to 4D during a long operation (easy.c).
