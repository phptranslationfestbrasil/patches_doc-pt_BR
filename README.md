patches_doc-pt_BR
=================

Patches da documentação php_BR do PHP (https://wiki.php.net/doc/translations/pt_br)

Instalar as dependências Ubuntu like
------------------------------------

Utilize o script abaixo para instalar as dependências:

    $ composer create-project fabpot/silex-skeleton path/to/install

Composer will create a new Silex project under the `path/to/install` directory.

    $ wget https://gist.github.com/royopa/599259ebeffa6ab7b1cb/raw/f64590a551ab181bdda086819e6c1828d701c548/build-machine-translation_fest
    $ chmod +x build-machine-translation_fest
    $ ./build-machine-translation_fest

Fazer o checkout da documentação
--------------------------------

    $ svn co https://svn.php.net/repository/phpdoc/modules/doc-pt_BR
    $ cd doc-pt_BR

Aplicando o patch na documentação:
----------------------------------

Se tiver usando o SVN >= 1.7 é só chamar 

    $ svn patch $file

Se não tiver o comando svn patch usem o patch mesmo: 

    $ patch -p0 < $file

Compilando o manual
-------------------

    $ php doc-base/configure.php --enable-xml-details --with-lang=pt_BR
    $ phd -d doc-base/.manual.xml -o output_dir -f php -P PHP
