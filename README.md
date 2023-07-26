PECL SSH2 extension compiled for Windows
=================================

July 26, 2023

This repository contains `php_ssh2` extension compiled for Windows to support XAMPP.

As of this date, an official compiled version for PHP 8.2 Windows x64 has not been released.

**You are encouraged to use official PECL build of version 1.4 once released at [pecl.php.net](https://pecl.php.net/package/ssh2).**

Purpose
--------------------
I built this release to support Windows [XAMPP](https://www.apachefriends.org/download.html) 8.2.x.

I only built the x64 thread-safe version for PHP 8.2 as that what XAMPP requires. If someone needs a different build for Windows, let me know. I plan to do work on PHP 8.3, so I will probably release a build for 8.3 soon.

PHP 8.2
--------------------
Based on pecl/ssh2 the source code version 1.4 releasd on 2023-04-20 from [pecl.php.net](https://pecl.php.net/package/ssh2). A copy of the source is included in this repository [ssh2-1.4.tgz](PHP_8.2/src).

#### Compiler version: VS16 - Visual Studio 2019 (16.11.26)

Built with PHP 8.2.8 source and SDK

| Architecture | x86 | x64 |
|---|---|---|
| TS (thread-safe) | not included | [php_ssh2.zip](https://github.com/jhanley-com/php-ssh2-windows/raw/master/PHP_8.2/vs16-x64-ts/php_ssh2.zip) |
| NTS (non-thread-safe) | not included | not included |

Notes on compiling - commands used
-------------------
`configure --disable-all --enable-cli --with-ssh2=shared --enable-zlib --with-openssl`
