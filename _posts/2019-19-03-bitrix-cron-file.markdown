---
layout: post
title:  "Пример файла для cron"
subtitle: "Пример файла для cron"
date:   2019-03-19 09:25:55 +0300
background: '/img/posts/04.jpg'
categories: bitrix
---
Пример файла для cron

{% highlight ruby %}
$_SERVER["DOCUMENT_ROOT"] = realpath(dirname(__FILE__)."/.." ) ;

define("NO_KEEP_STATISTIC", true);
define("NOT_CHECK_PERMISSIONS",true);
define('CHK_EVENT', true);

require_once $_SERVER['DOCUMENT_ROOT'] . '/bitrix/modules/main/include/prolog_before.php';


require_once $_SERVER['DOCUMENT_ROOT'] . '/bitrix/modules/main/include/epilog_after.php';

{% endhighlight %}