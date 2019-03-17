---
layout: post
title: PHP Relative Path  Problem
subtitle: When a PHP file includes another PHP file which itself includes yet another file — all being in separate directories
tags: [PHP]
comments: true
---

```php
include(dirname(__FILE__) . "/dir/script_name.php");
```

