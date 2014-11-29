patches_doc-pt_BR
=================

Patches da documentação php_BR

Instalar as dependências Ubuntu like
------------------------------------

Utilize o script abaixo para instalar as dependências:

.. code-block:: console

    $ composer create-project fabpot/silex-skeleton path/to/install

Composer will create a new Silex project under the `path/to/install` directory.

.. code-block:: console

    $ wget https://gist.github.com/royopa/599259ebeffa6ab7b1cb/raw/f64590a551ab181bdda086819e6c1828d701c548/build-machine-translation_fest
    $ chmod +x build-machine-translation_fest
    $ ./build-machine-translation_fest

Fazer o checkout da documentação
--------------------------------

.. code-block:: console

    $ svn co https://svn.php.net/repository/phpdoc/modules/doc-pt_BR
    $ cd doc-pt_BR

Aplicando o patch na documentação:
----------------------------------

Se tiver usando o SVN >= 1.7 é só chamar 

.. code-block:: console

    $ svn patch $file

Se não tiver o comando svn patch usem o patch mesmo: 

.. code-block:: console

    $ patch -p0 < $file

Compilando o manual
-------------------

.. code-block:: console

    $ php doc-base/configure.php --enable-xml-details --with-lang=pt_BR
    $ phd -d doc-base/.manual.xml -o output_dir -f php -P PHP
