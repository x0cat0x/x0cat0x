---
layout: post
title: PHP Relative Path  Problem
subtitle: When a PHP file includes another PHP file which itself includes yet another file — all being in separate directories
tags: [PHP]
comments: true
---

|/a/a.php
|b.php
|/c/c.php

If b.php 

```php
#b.php
include(../a/a.php);
```

but if c.php also *includes* b.php 
```php
#c.php
include(./b.php);
```


```php
include(dirname(__FILE__) . "/dir/script_name.php");
```

