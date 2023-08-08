# Build SSH2 for PHP

This documentation covers PHP 8.3 Beta 2.

Last Update: August 8, 2023

### Setup build environment for PHP 8.3

Follow the steps in this [document](BUILD-PHP-8.3beta2.md).

### Download SSH2 source code
 - `cd C:\php-dev`
 - `wget https://pecl.php.net/get/ssh2-1.4.tgz`
 - `mkdir C:\php-dev\php-8.3.0beta2-src\ext\ssh2`
 - `tar xvfz ssh2-1.4.tgz -C C:\php-dev\php-8.3.0beta2-src\ext\ssh2 --strip-components 1`

### Configure PHP build
 - `cd C:\php-dev\php-8.3.0beta2-src`
 - `buildconf --force`
 - `configure --enable-cli --enable-zlib --with-openssl --enable-apache2-4handler --with-ssh2=shared`
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
	| ssh2       | shared |
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


	Type 'nmake' to build PHP
```

### Build PHP
 - `nmake`

### php_ssh2.dll location
 - x64/Release_TS/php_ss2.dll

### Package PHP build into zip file
 - `nmake snap`
 - File is located at:
   - x64/Release_TS/php-8.3.0beta2-Win32-vs16-x64.zip
