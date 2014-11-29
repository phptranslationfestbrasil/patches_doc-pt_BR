patches_doc-pt_BR
=================

Patches da documentação php_BR

Fazer o checkout da docuemntação
--------------------------------

```
svn co https://svn.php.net/repository/phpdoc/modules/doc-pt_BR
cd doc-pt_BR
```

Aplicando o patch na documentação:
----------------------------------

Se tiver usando o SVN >= 1.7 é só chamar 

```
svn patch $file
```

Se não tiver o comando svn patch usem o patch mesmo: 

```
patch -p0 < $file
```

Compilando o manual
------

```
php doc-base/configure.php --enable-xml-details --with-lang=pt_BR
phd -d doc-base/.manual.xml -o output_dir -f php -P PHP
```