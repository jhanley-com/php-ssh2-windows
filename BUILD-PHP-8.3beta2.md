# Setup build environment for PHP 8.3

This documentation covers PHP 8.3 Beta 2.

Release Date: August 6, 2023

### Create working directory
 - `mkdir c:\php-dev`
 - `cd c:\php-dev`

### Download PHP source code
 - `wget https://windows.php.net/downloads/qa/php-8.3.0beta2-src.zip`
 - `unzip php-8.3.0beta2-src.zip`

### Download PHP development package SDK
 - `wget https://windows.php.net/downloads/qa/php-devel-pack-8.3.0beta2-nts-Win32-vs16-x64.zip`
 - `unzip php-devel-pack-8.3.0beta2-nts-Win32-vs16-x64.zip`

### Download PHP SDK binary tools
 - `git clone https://github.com/php/php-sdk-binary-tools.git php-sdk`

### Setup PHP SDK binary tools
 - `cd php-sdk`
 - `phpsdk-vs16-x64.bat`
 - Command results. Notice the change in command prompt.
```
	[vcvarsall.bat] Environment initialized for: 'x64'

	PHP SDK 2.2.1-dev

	OS architecture:    x64
	Build architecture: x64
	Visual C++:         14.29.30151.0
	PHP-SDK path:       C:\php-dev\php-sdk

	C:\php-dev\php-sdk
	$
```

### Setup PHP build dependencies
 - `cd ..\php-8.3.0beta2-src`
 - `phpsdk_deps --update --branch master`
 - Command results.
```
	Configuration: master-vs16-x64-staging

	Processing package apache-2.4.43-vs16-x64.zip
	Processing package c-client-2007f-1-vs16-x64.zip
	Processing package fbclient-3.0.6-nocrt-x64.zip
	Processing package freetype-2.11.1-vs16-x64.zip
	Processing package glib-2.53.3-1-vs16-x64.zip
	Processing package ICU-72.1-vs16-x64.zip
	Processing package libargon2-20190702-vs16-x64.zip
	Processing package libavif-0.9.0-1-vs16-x64.zip
	Processing package libbzip2-1.0.8-vs16-x64.zip
	Processing package libcurl-7.87.0-vs16-x64.zip
	Processing package libenchant2-2.2.8-vs16-x64.zip
	Processing package libffi-3.3-4-vs16-x64.zip
	Processing package libiconv-1.16-5-vs16-x64.zip
	Processing package libintl-0.18.3-8-vs16-x64.zip
	Processing package libjpeg-turbo-2.1.0-vs16-x64.zip
	Processing package liblmdb-0.9.22-6-vs16-x64.zip
	Processing package liblzma-5.2.5-vs16-x64.zip
	Processing package libonig-6.9.8-vs16-x64.zip
	Processing package libpng-1.6.34-8-vs16-x64.zip
	Processing package libpq-11.4-1-vs16-x64.zip
	Processing package libqdbm-1.8.78-vs16-x64.zip
	Processing package libsasl-2.1.27-3-vs16-x64.zip
	Processing package libsodium-1.0.18-vs16-x64.zip
	Processing package libssh2-1.10.0-2-vs16-x64.zip
	Processing package libtidy-5.6.0-2-vs16-x64.zip
	Processing package libwebp-1.1.0-vs16-x64.zip
	Processing package libxml2-2.10.3-vs16-x64.zip
	Processing package libxpm-3.5.12-8-vs16-x64.zip
	Processing package libxslt-1.1.37-vs16-x64.zip
	Processing package libzip-1.7.1-1-vs16-x64.zip
	Processing package mpir-3.0.0-vs16-x64.zip
	Processing package net-snmp-5.7.3-3-vs16-x64.zip
	Processing package nghttp2-1.51.0-vs16-x64.zip
	Processing package openldap-2.4.47-1-vs16-x64.zip
	Processing package openssl-3.0.8-vs16-x64.zip
	Processing package sqlite3-3.40.0-vs16-x64.zip
	Processing package wineditline-2.206-vs16-x64.zip
	Processing package zlib-1.2.12-vs16-x64.zip
	Updates performed successfully.
```

### Configure PHP build
 - `buildconf --force`
 - `configure --enable-cli --enable-zlib --with-openssl --enable-apache2-4handler`
 - Command results. Configuration details prior to "Enabled extensions" skipped.
```
	Enabled extensions:
	-----------------------
	| Extension  | Mode   |
	-----------------------
	| bcmath     | static |
	| calendar   | static |
	| com_dotnet | static |
	| ctype      | static |
	| date       | static |
	| dom        | static |
	| filter     | static |
	| gd         | shared |
	| hash       | static |
	| iconv      | static |
	| json       | static |
	| libxml     | static |
	| mysqlnd    | static |
	| openssl    | shared |
	| pcre       | static |
	| phar       | static |
	| random     | static |
	| readline   | static |
	| reflection | static |
	| session    | static |
	| simplexml  | static |
	| spl        | static |
	| standard   | static |
	| tokenizer  | static |
	| xml        | static |
	| xmlreader  | static |
	| xmlwriter  | static |
	| zip        | shared |
	| zlib       | static |
	-----------------------


	Enabled Zend extensions:
	----------------------
	| Extension | Mode   |
	----------------------
	| opcache   | shared |
	----------------------


	Enabled SAPI:
	--------------------
	| Sapi Name        |
	--------------------
	| apache2_4handler |
	| cgi              |
	| cli              |
	--------------------


	-----------------------------------------
	|                     |                 |
	-----------------------------------------
	| Build type          | Release         |
	| Thread Safety       | Yes             |
	| Compiler            | Visual C++ 2019 |
	| Target Architecture | x64             |
	| Host Architecture   | x64             |
	| Optimization        | PGO disabled    |
	| Native intrinsics   | SSE2            |
	| Static analyzer     | disabled        |
	-----------------------------------------
```

### Build PHP
 - `nmake`

### Package PHP build into zip file
 - `nmake snap`
 - File is located at:
   - x64/Release_TS/php-8.3.0beta2-Win32-vs16-x64.zip

### Run PHP tests
 - Run all tests
   - `nmake test`
   - Notes:
     - Running all tests takes about two hours.
     - An extension will not be tested if it is not enabled with the configure command.
 - Example: run the zip extension tests
   - `nmake test TESTS=ext/zip/tests`
