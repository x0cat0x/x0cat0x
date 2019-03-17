---
layout: post
title: PHP Relative Path  Problem
subtitle: When a PHP file includes another PHP file which itself includes yet another file — all being in separate directories
tags: [PHP]
comments: true
---

|b.php

|dir_a/a.php

|dir_c/c.php

When b.php includes a.php from /dir_a/a.php

```php
#b.php
include("./dir_a/a.php");
```
it would be ok.

but then when c.php also includes b.php 
```php
#/dir_c/c.php
include("../b.php");
```
there will be an error
```php
Warning: include(./dir_a/a.php): failed to open stream: No such file or directory in ...
Warning: include(): Failed opening './dir_a/a.php' for inclusion (include_path='.:') in ....
```
 since c.php doesn't know where a.php located
 
 Solution:

```php
#b.php
#include(dirname(__FILE__) . "/dir/script_name.php");
include(dirname(__FILE__) . "/dir_a/a.php");
```
will work well.
