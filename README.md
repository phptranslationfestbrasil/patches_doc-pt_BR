patches_doc-pt_BR
=================

[PHP Translation Fest Brasil 2014!](https://phptranslationfestbrasil.github.io/)
==================================

Patches da documentação php_BR do PHP (https://wiki.php.net/doc/translations/pt_br)

##Prepare um ambiente e ajude a contribuir com a tradução

Você pode utilizar uma máquina virtual com todas as dependências já instaladas. 
Para isso, siga os próximos passos.

Baixar e instalar o Oracle Virtual Box
--------------------------------------
Utilize a página abaixo para instalar o Virtual Box na sua máquina.

https://www.virtualbox.org/wiki/Downloads

Máquina Virtual para utilização
-------------------------------
Baixe a máquina virtual no endereço abaixo. A senha é translationfest

####Máquina Virtual Ubuntu 14.04 32bits (3,8Gb)
https://drive.google.com/file/d/0BzJtYovThzl_ZEdlTVVvQXpWR2c/view?usp=sharing

Instalar as dependências Ubuntu like
------------------------------------
Caso não esteja usando uma máquina virtual, utilize o script abaixo para instalar as dependências numa máquina Ubuntu like:

    $ wget -O build-machine-translation_fest https://gist.github.com/royopa/599259ebeffa6ab7b1cb/raw/
    $ chmod +x build-machine-translation_fest
    $ ./build-machine-translation_fest

Fazer o checkout da documentação
--------------------------------

    $ svn co https://svn.php.net/repository/phpdoc/modules/doc-pt_BR
    $ cd doc-pt_BR

Aplicando um patch na documentação:
----------------------------------
Para aplicar um patch na sua tradução, utilize um dos comandos abaixo:

Se tiver usando o SVN >= 1.7 é só chamar:

    $ svn patch $file

Se não tiver o comando svn patch use o comando:

    $ patch -p0 < $file

##Compilando o manual
Para compilar, existem algumas opções:

###Documentação no formato xHMTL
Gera arquivos no formato xHTML, sem imagens, porém funcional:

```
$ cd ~/doc-pt_BR/
$ php doc-base/configure.php --enable-xml-details --with-lang=pt_BR
$ phd --docbook doc-base/.manual.xml --package PHP --format xhtml --output mydocs_xhtml
$ cd mydocs_xhtml/php-chunked-xhtml/
$ ls
```
Veja esse processo rodando aqui: https://asciinema.org/a/14378

###Documentação no formato PHP:
Gera arquivos no formato php, e depende de outros arquivos explicados em http://doc.php.net/tutorial/local-setup.php:
```
$ cd ~/doc-pt_BR/
$ php doc-base/configure.php --enable-xml-details --with-lang=pt_BR
$ phd --docbook doc-base/.manual.xml --package PHP --format php --output mydocsphp_pt_BR
```
Depois de executar os passos acima, utilize os comandos abaixo para baixar as dependências que o formato de documentação em php possui:
```
$ wget https://github.com/php/web-php/archive/master.zip
$ unzip master.zip
$ rm -rf master.zip
$ rsync -avzC --timeout=600 --delete --delete-after --exclude='distributions/**' --exclude='extra/**' --exclude='backend/notes/**' ./web-php-master/ ./myphpnet/
$ rm -rf web-php-master/
```
Então mova a pasta da versão da documentação que você criou dentro da pasta que será usada pelo servidor web:
```
$ mv mydocsphp_pt_BR/php-web/ myphpnet/manual/pt_BR
```
Agora inicie o servidor web do PHP para acessar a documentação pelo navegador:
```
$ php -S localhost:8000 -t ./myphpnet/
```
E acesse a documentação gerada através do endereço http://localhost:8000/manual/pt_BR/

Veja esse processo rodando aqui: https://asciinema.org/a/14385
