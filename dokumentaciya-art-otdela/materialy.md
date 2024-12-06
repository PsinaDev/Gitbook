# Материалы

Материалы

Не обязательно у вас должен быть один референс на объект и на его материал, чаще это будет отдельный реф материала на совершенно другом объекте. Имейте это в виду! Большая редкость когда вы располагаете исчерпывающей информацией сразу и на примере одного объекта!

Чисто белые и чисто черные цвета в природе не существуют. В игре чистые цвета также будут интерпретироваться некорректно, белый станет неестественным засветом, а черный превратиться в черную дыру. Об этом следует помнить. Поэтому мы используем фиксированные значения, за рамки которых не выходим:

![](https://lh7-us.googleusercontent.com/PYCt5i0k9VzfHNGRA7jyDI7nxtzVzq19FrbvlMgIxWu3SXBUhA0AVRnN3DAebHrM7wdCuuC5KmCm85S0wr4FWN8driu0BZvT3MLRM9JGCE1nl8XoHNohB20NqWEumvy1r9veVUGW7rTabLR9_7gfprFAMtOXVy5IUXTXdSIDqe1sJkEWG70cJGzyt63uaQ)

Об этом следует помнить всегда.

Base color

Нейтральный серый:

&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/5apqBGffaQYmAffxMCQ2FRIehUVE78SoQNJiLRcEQceGQYeBaDM1eDMiF8-f_Z3KkG5rjzWUz1wwDXXe15yHO8YQY7Zd29wv99v9X2Ng6ptjWMr12PO-jrCHO9zyO_Va7fLsYgGnbZsiYJyE2S_qtvnx44EsPwPcH0znaztsWUFHu2MSMz9uCAU40GKHOQ" alt=""><figcaption></figcaption></figure>

\


Цвета для разных материалов:

![](https://lh7-us.googleusercontent.com/t_ud0DAvJ1rZHxoOOF-7sZBXOJJ_TaX6hrNrgFY8y0INMYMHlZ5xVf0rLgH5URvlBFm2UHP_QUY59IQCjLl77vXzT95boTJt-L2uaQrMJM5oE9TPA1G6JXNwquTYjKeC-Aky5VTGOgpmNWctfdvjCiIdag3AxftNp0u5UkGqAHhSWiPMmpfOs3HdyfT8Aw)

Также может помочь:

![](https://lh7-us.googleusercontent.com/vaxaCv-CJGvrGaC_TwYagcH3sQg21RMIvKarzW9TovLqKR6rbVjtgzYI936CGxELeYHh79q8WxwT_kbGEQdMRcfxDUBP8yWlk841Vv4iwgxMUKOrRFoYXLg8HcZ-10WBLEZ8ql1AFdfnTvNU8HYwE15xVVxCpQEs0DwbP6eJE_a21AFtdjq-Cvwrwga3eA)

Вышеприведенные цвета — лишь ориентир, но их желательно использовать.

Metallic

Карта metallic применяется только на металлические материалы. Белый — металл, черный — не металл.

![](https://lh7-us.googleusercontent.com/KMefmqdP8Et6__M4Nqf3t20mYtOKpFAaIUGa6p6WZFH711GQUjdC38AOuPn_9K3lr0pidu8tl1TmHudlYwk9LS1gvP8NpmZhAsSOv23yavH-f486hVhL2G72c1hx1bNbOaAMOOLGZPsOJfFOUsluOFqXj9fLqssdtzt9IyffWrBGTccS8KRuX0FaAmkmyg)

Metalness у материалов, которые не являются металлами, должна быть полностью черной.

Существует распространенная ошибка подкручивать metalness для того чтобы добиться красивых бликов, но так делать категорически нельзя. Металлом должен быть только металл.

Roughness

Roughness мы используем для создания глянцевости. Ни в коем случае не компенсируем глянцевость картой metallic, это очень грубая ошибка.

![](https://lh7-us.googleusercontent.com/ebNT1zufGpeOzNjzb5zdA4-Kt7TMikOQnPTNbd_pgdiaLkge0FuC5NWUoTbv7RHahPN1EzlCnuvOcMhXEMUEqUGERt6M5MhFBqxtXObI9KGUUNKdJkZBWq-s7qKfO6yfwIY6xugrDLodvS5wrN2Vcg74xqARn6CUg86S1TI4UJHY7Vd4Bt6pk_9HHZrKQw)

\


Гайд по структуре сцены в Substance Painter:

Для того чтобы правильно собрать материалы, сначала нужно понять как все это будет работать в движке. Для большинства ассетов мы используем систему многослойных шейдеров, что позволяет нам красиво смешивать материалы в движке. Это значит что из сабстенса мы получаем только маски. В основном это касается средних и больших объектов, разрешения текстур которых объективно не хватает для достижения оптимального качества картинки. Но даже если объект относительно маленький и мы делаем его со всеми картами, структура создания материалов остается одной.

Итак, максимальное количество материалов на одном объекте - 5. Но желательно делать до 4-х. В идеале должно быть 3 материала. Похожие по типу материалы можно просто группировать (например, разные типы грязи можно сделать одной папкой).

У нас есть папка, для которой мы создаем blackmask, в которой уже создаем fill, paint и прочие корректировочные слои.

Выглядят это так:

![](https://lh7-us.googleusercontent.com/Ou1L88fLEFyScW-K0asa-LyTJbZmy2qMJ5RbgfqvUR4P2x8nKNxEHsZKBgfcJrfbjzo6-qt-64MN-ti3mvG_3LNp5_2EvNvi5q6tgj2XiyrAWoMHdG2OBA5GfEiFNgmcWzyg2SrfalgVu8kbNULMOiHiXfk3MT2ICZ8CaMPLvUjbOP5eWcp3i3ElDQP-mg)

&#x20;

![](https://lh7-us.googleusercontent.com/Vwk4ZWlV9tTrLIU3YajI89jNGctL8agct373MfNkQIzoBaq30DdYsf2gD1K5WPrS8UJk5ZhScrEKu8W8i4UcZZSf5g7AH0JQ3cPMqF6hYekki5Xrdq8mq0qiMAo97lNWxc4r40YBXARfANuSk5JXUEzuNSah2MElB8EI1QnJdZhqvIrHv7DJByF3IIOvCg)

Внутри каждой папки может быть группа материалов.

\


⦁ Хаос в сцене — это плохо. Все материалы следует структурировать согласно логике их расположения на объекте. Не забываем что папок с масками, то есть, групп материалов, у нас может быть до 5.

![](https://lh7-us.googleusercontent.com/S1PsnrgGLKzRM-KUAJhUmozBo3c7Bp8N1brAcjEJY4ZVYQoAmfl0YLYnFvhoMUlD20bHTHlmKG8dilbLeP6F4V7-BAV_Ep4aBjrEtw4ROFcP95zxE_04X0Q95NevrY4roVrQoIlWlpgkc5EktMDJSn7SjFz3yFKNRU_DrKcTFrS-QSFw5QUQZV69PtmZgw)

⦁ Все материалы похожего типа следует группировать по папкам с соответствующим названием. Это значительно упрощает работу.

&#x20;![](https://lh7-us.googleusercontent.com/lXZSaudubQhZIA1OT6dSvSC7HKw0_d3pqRN_u0mapk5ClNqAjg8FdDi7KgDvoM-BByXdFnjzcmGKcUGx1OL6Pym_pORgFgA-v7ubY0WGwx36JqFmUulB3nd6VjZprvFwgPi9ujxnPkHoYf1i27BzCuRE0U_vAXqGeKP0EtC7MPq68Bh46i-DEl0chgLmIw)

Совет: все базовые материалы разного типа, например: краска, пластик, дерево и т.п., можно группировать в одну папку и делать на них общую маску. Это облегчит структуру сцены.

⦁ В каждой папке должны находиться материалы для разных групп, либо разные типы материалов этой категории.

![](https://lh7-us.googleusercontent.com/rIwqRsB9_iU6MocBY_Rrh8z_NaTHnjCPxxUUJ2ef-rPUEkybmVQp7wQ2krolao3kfwZXiNGAP3ZF9BK7I2a2XHiBtwAd1jyLvRGmaiTXjfnwfZx7E0rjBY-m3C7UwqD_0Ca_fS60cwHPRQYwM2CUHGk01fscjz2yo-1ohPpeU5Y174GdhTRq1HGMpeIyhw)

Пример: в папке Dirt может быть много типов грязи, то есть, много папок Dirt с разными материалами грязи, включая разную грязь для отдельных типов материалов со своими масками.

⦁ Маски мы всегда делаем для папок, а не для отдельных слоев. Информацию заносим в них не прямо в маску, а в paint.

![](https://lh7-us.googleusercontent.com/w4fPOUQb9nDMeksq1FCPgssSMqkXkLHSynkaX9vSaRMbunh-ozckIY493ayWQ6ZyvAjVCq2cbOPUjS_s4NOL3KcS30g_gdCZVtGy6B9Zw_61ga3Zx2RBz6eVST3j5UQOUkNQRFU3YZbki4gAn-nYCHBvYzfGnGrFAJj0jKOKh18xJzm7fR563nw-_qC7aQ)

\


**Alpha и ее правильное применение**

Абсолютное значение цвета мы все-таки используем. Но только для того, чтобы пробивать им дырки. Логика такая: в местах, где должны быть дырки, мы не делаем отдельную альфу, а просто на карте albedo рисуем чисто черным цветом (0,0,0). Поскольку у нас нигде не используется чисто черный, то мы в итоге движком отрезаем эти области через cutout.

![](https://lh7-us.googleusercontent.com/y_e_y9ZdZI6y6LjLJF8uXwToZOTCJq_uCJcMHdbsFK0r-1i9xYpMIbmCkYMmtFwb-4IEQJVxgBX_869r7Y8T41TRSyASvLfuy5dfCs5y4FyG9PG34IHX40spjg83y61IMMyTgfWZd_ABIgTjpGgjI7LSdfdXTossDhFPjQMhOsNgqTbNkZ-NLfzWkFe-Mw)

Чтобы альфа была максимально аккуратной, нужно следить за пикселями. Желательно закрашивать только ту область, которая идет с отверстием и больше НИГДЕ(!) на ассете не использовать чисто черный цвет.

\


При аккуратной работе с альфами, мы можем делать так простые небольшие отверстия, что позволяет увеличивать детализацию объектов за счет карт и не делать отдельных альф для простых ситуаций.

Пример:

![](https://lh7-us.googleusercontent.com/PRxAV3Zfrn7tF7cQH-AnkjEtMd58aItchRZSA6ByZvuKpxg-l6V5t0rb3GcENx5Id4-hZKmR-ALixxGSsoOSvjSrxQ-noW1st3cdQ-YFOYGqFrEBWU1e3Ssmw_7aDFaF44cAXqGLBE--IDrZnH149e-dAIt4njaMU4D7K2MWbA-k5EIpYlzWHreKBnlDbQ)

\


А вот в таких ситуациях мы уже используем отдельную альфу:

&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/zf3n7GMOIPGAxYwcatXa6HQwpWiaSIB0tIbjDr3RxuyrbZFuHd14f6lIcvLNhVH3sqVjDX1JQmQEVrYmTishsc7jsikTcJJx2foT9Qn1sOlg60eNOX9v8cyrL45TCk37RmneCCAAP0oLx9ZtmyzF68U-TRuwS0nBptjzM8lfk64rz7YQY3ABfr1jfYCcSw" alt=""><figcaption></figcaption></figure>

\


\
