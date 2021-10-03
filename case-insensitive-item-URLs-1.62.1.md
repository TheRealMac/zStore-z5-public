## Adding support for lower cased ASINs _for z5 v1.62_
... for those coming from bing search engine

after this update your visitors will be able to access the item page additional to

 > https://z5.de.envato.homac.at/itm/B004EYFOGI/scsports-langhantelstange.html (example)
 
with

 > https://z5.de.envato.homac.at/itm/b004eyfogi/scsports-langhantelstange.html (example)
---
##### open 

.htaccess

##### find line beginning with

```
^itm/([0-9A-Z]+)/([a-z0-9\-_]+)\.html$
```

##### replace with

```
^itm/([0-9A-Za-z]+)/([a-z0-9\-_]+)\.html$
```
---
##### open

classes/zstore.class.php

##### find method/function "getProductData"

```php
function getProductData($asin,$id=0,$output="large") {
```

##### in this block find

```php
$add2sql[] = "asin = " . $this->dbquote($asin);
```

##### replace with

```php
$add2sql[] = "lower(asin) = " . $this->dbquote(strtolower($asin));
```
---
you're done
