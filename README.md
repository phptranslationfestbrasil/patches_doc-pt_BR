patches_doc-pt_BR
=================

[PHP Translation Fest Brasil 2014!](https://phptranslationfestbrasil.github.io/)
==================================

Patches da documentação php_BR do PHP (https://wiki.php.net/doc/translations/pt_br)

Baixar e instalar o Oracle Virtual Box
--------------------------------------
Utilize a página abaixo para instalar o Virtual Box na sua máquina.

https://www.virtualbox.org/wiki/Downloads

Máquina Virtual para utilização
-------------------------------
Baixe a máquina virtual no endereço abaixo. A senha é translationfest

https://drive.google.com/file/d/0BzJtYovThzl_ZEdlTVVvQXpWR2c/view?usp=sharing (3,8 Gb)

Instalar as dependências Ubuntu like
------------------------------------
Caso não esteja usando a máquina virtual, utilize o script abaixo para instalar as dependências numa máquina Ubuntu like:

    $ wget -O build-machine-translation_fest https://gist.github.com/royopa/599259ebeffa6ab7b1cb/raw/
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
