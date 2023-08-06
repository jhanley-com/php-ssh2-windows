PECL SSH2 extension compiled for Windows
=================================

August 6, 2023

This repository contains `php_ssh2` extension compiled for Windows to support XAMPP.

As of this date, an official compiled version for PHP 8.2 or 8.3 Windows x64 has not been released.

**You are encouraged to use official PECL build of version 1.4 once released at [pecl.php.net](https://pecl.php.net/package/ssh2).**

Purpose
--------------------
I built this release to support Windows [XAMPP](https://www.apachefriends.org/download.html) / PHP 8.2 and PHP 8.3 Beta1.

I only built the x64 thread-safe version as that what XAMPP requires. If someone needs a different build for Windows, let me know.

PHP 8.2
--------------------
July 26, 2023

Based on pecl/ssh2 the source code version 1.4 releasd on 2023-04-20 from [pecl.php.net](https://pecl.php.net/package/ssh2). A copy of the source is included in this repository [ssh2-1.4.tgz](PHP_8.2/src).

#### Compiler version: VS16 - Visual Studio 2019 (16.11.26)

Built with PHP 8.2.8 source and SDK

Linked with [LIBSSH2](https://www.libssh2.org/) version 1.10.0

| Architecture | x86 | x64 |
|---|---|---|
| TS (thread-safe) | not included | [php_ssh2.zip](https://github.com/jhanley-com/php-ssh2-windows/raw/master/PHP_8.2/vs16-x64-ts/php_ssh2.zip) |
| NTS (non-thread-safe) | not included | not included |

PHP 8.3 Beta 1
--------------------
August 1, 2023

Based on pecl/ssh2 the source code version 1.4 releasd on 2023-04-20 from [pecl.php.net](https://pecl.php.net/package/ssh2). A copy of the source is included in this repository [ssh2-1.4.tgz](PHP_8.3/src).

#### Compiler version: VS16 - Visual Studio 2019 (16.11.28)

Built with PHP 8.3.0 Beta1 source and SDK

Linked with [LIBSSH2](https://www.libssh2.org/) version 1.10.0

| Architecture | x86 | x64 |
|---|---|---|
| TS (thread-safe) | not included | [php_ssh2.zip](https://github.com/jhanley-com/php-ssh2-windows/raw/master/PHP_8.3/vs16-x64-ts/php_ssh2.zip) |
| NTS (non-thread-safe) | not included | not included |

Notes on compiling - commands used
-------------------
`configure --disable-all --enable-cli --with-ssh2=shared --enable-zlib --with-openssl`

To see how I build PHP see this [page](BUILD.md).
