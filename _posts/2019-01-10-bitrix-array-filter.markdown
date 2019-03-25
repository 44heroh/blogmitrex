---
layout: post
title:  "Фильтр global для вывода элементов"
subtitle: "Фильтр global для вывода элементов"
date:   2019-01-10 17:31:55 +0300
background: '/img/posts/04.jpg'
categories: bitrix
---
Фильтр global для вывода элементов

{% highlight ruby %}
Массив должен выглядеть так

Array
(
    [0] => Array
        (
            [LOGIC] => OR
            [0] => Array
                (
                    [PROPERTY_BRAND] => 44028
                )

            [1] => Array
                (
                    [PROPERTY_BRAND] => 44029
                )

        )

)

перед коспонетом выведения элементов не забудьте
global $arFilter;(вместо arFilter может быть любое название)

{% endhighlight %}