phpDox
======

*phpDox* is a documentation generator for PHP projects.
This includes, but is not limited to, API documentation. The main focus is on enriching
the generated documentation with additional details like code coverage, complexity information
and more.

About this repository
---------------------

phpDox upstream code doesn't work on PHP 8.1 or PHP 8.2. This repository contains:
  - phpDox upstream
  - fDOMDocument upstream in lib/ folder, with Git history fully preserved (without tags)
  - fixes for PHP 8.1 and 8.2

Our goal is to be able to run phpDox on our Jenkins CI infrastructure, under PHP 8.x.

This repository only pretends to offer a working version of both libraries for PHP 8.x,
and doesn't aim to stay compatible with PHP 5 or PHP 7.1 code.

It can be especially helpful for users of the now unmaintained jenkins-php template
by PHPUnit author Sebastian Bergmann  (sebastianbergmann/php-jenkins-template)
as we test PHP 8 compliance with the CI jobs defined by this template.


Requirements
------------

- PHP Version 7.4+
  - ext/dom
  - ext/xsl
  - ext/iconv and [libiconv version >= 2.12](http://www.gnu.org/software/libiconv/documentation/libiconv/iconv.1.html)
- PHPParser [PHP Parser API](https://github.com/nikic/PHP-Parser)
- [DirectoryScanner](http://github.com/theseer/DirectoryScanner)
- [fXSL](http://github.com/theseer/fXSL)
- [PHP_Timer](http://github.com/sebastianbergmann/php-timer)


Developer Installation
----------------------

First, clone this repository:

    git clone git://github.com/nasqueron/phpdox.git
    composer install

If you wish a phpdox command in your system:


    ln -s /path/to/phpdox/phpdox /usr/local/bin/phpdox

Usage Examples
--------------

You can run phpDox like this:

    phpdox --help

As of version 0.4 phpDox requires an xml configuration file. In case a project you want to generate documentation for does not come with one, you can create it by calling

    phpdox --skel > phpdox.xml.dist


Sample invocation to parse and generate output based on the default phpdox.xml configuration file

    phpdox

or you can tell `phpdox` what configuration file to use by calling switch `--file` or in short

    phpdox -f path/to/phpdox.xml
