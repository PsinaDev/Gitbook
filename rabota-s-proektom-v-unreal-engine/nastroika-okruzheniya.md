---
description: >-
  Для успешной работы с проектом на Unreal Engine 5.4 необходимо правильно
  настроить окружение. Следуйте инструкциям ниже.
---

# Настройка окружения

***

## **1. Установка Unreal Engine 5.4**

1. **Epic Games Launcher:**
   * Скачайте и установите **Epic Games Launcher** с [официального сайта](https://www.unrealengine.com).
   * Войдите в свой аккаунт Epic Games или создайте новый.
2. **Установка Unreal Engine:**
   * Перейдите на вкладку **Unreal Engine** → **Library**.
   *   Нажмите кнопку **+** рядом с версией движка и выберите **5.4**.\


       <figure><img src="../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>
   * Укажите путь установки (желательно использовать SSD для повышения производительности).
   * После загрузки нажмите **Launch** для запуска Unreal Engine.

***

## **2. Установка необходимых инструментов**

* [**Visual Studio (или IDE):**](#user-content-fn-1)[^1]
  * Скачайте и установите **Visual Studio 2022** с [официального сайта](https://visualstudio.microsoft.com/).\
    Бесплатно распространяется Community Edition. Чтобы получить ключи на Enterprise или Professional версию, обратитесь к[ Lead Code.](../readme/obshie-svedeniya.md#kontakty-komandy)
  * В окошке Visual studio installer отметьте следующие галочки: \
    [Видеоинструкция](https://www.youtube.com/watch?v=HQDskHVw1to)
    *

        <figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXc9bOg5t2edHM1FJaL3p2rIJb6l3H8OWihrUg-AwFb8pyNTtevm4nh9IPydErLbZHodvO8gf0RtaM6_Tf400wRsJNI7aqbJwJGK1rQzFxDupN0iEZDDw5bDboJf46xErpWM_VCHc204rGKqx9ySdH6JLHQ?key=MFvsAmq73t2EaIJsyKb_tA" alt=""><figcaption></figcaption></figure>
    *

        <figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcLG4DwOsIMZRlH8r8Sjay4oghgdro-lORc-Amg6DQ_PmqxqsK309misTdbmGthvb4ChgqXFCbE4Ls5sFCQ8h5fFjqxHpDaCAAXAqdPgvjuxtgtKKtVRxsG19Qi3aewheptRlTCgzFre1-wtcCoqOMpYytp?key=MFvsAmq73t2EaIJsyKb_tA" alt=""><figcaption></figcaption></figure>
    *

        <figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXefN_iNOSR3k-DF1w2HJgpyVccUCff4A3G4baJLHQvHH-sNjLy1uo-uyGgvn7l60Xib3QS5frw_LK5kXMWH1qWOXwlZyKXXJ_7s1HrebbDmVzbSi7_s1R0pzOBTeAJ263KylBPRN3_KvlMYgRxdZpUzSAU?key=MFvsAmq73t2EaIJsyKb_tA" alt=""><figcaption></figcaption></figure>
    *

        <figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXf_pLr0JCo6XZjgQeMN9jd49UNAReXmdzNfd9LGXFafLVeUA1ADhL4CDDchcrt6ITtJnVkhKzYMDsxVxvjCyXHxYDlng7EHjEOjUbBsATOK9rBKHsBrlf1w3OVP4StG2hsK6n4Wn1ifXftvyOz2HvQPKHc?key=MFvsAmq73t2EaIJsyKb_tA" alt=""><figcaption></figcaption></figure>


    *

        <figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdvMuba-7t0V--SsiZzFmgqigvtt7o3iBDZ69_qxtO-g71uXGMnAQu549LCqtJJ_dby7OXXZuAkB_9_FWYDZQM1Ao-K8Oi3CMOXiEVKsTYF04UShsPrsQQItLpjs2hAFQb2wvs-H4p5nbzWsOfQr0UB9sN-?key=MFvsAmq73t2EaIJsyKb_tA" alt=""><figcaption></figcaption></figure>


    *

        <figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXepm089vs9jm8Aj7kaJOD5U4-Ge2xor4gV3M_S8-4ZtbcW_erErOjAJ3x7DedRMtgRYLRZJcQAzgZioxG-pNHf77lbRUe1VLp-peLDm4MxYsRo-s65WvHHpaChcZ-r4GmVPFpLJXVYVjm1aZXNOoRRROSfy?key=MFvsAmq73t2EaIJsyKb_tA" alt=""><figcaption><p>Отдельно выберите пакет SDK для Windows, соответствующей вашей версии Windows или младше.</p></figcaption></figure>

## **3. Клонирование репозитория проекта**

{% content-ref url="../rabota-s-git-i-serverom-gitlab/osnovnye-deistviya-v-git/osnovnye-deistviya-v-sourcetree/klonirovanie-repozitoriya.md" %}
[klonirovanie-repozitoriya.md](../rabota-s-git-i-serverom-gitlab/osnovnye-deistviya-v-git/osnovnye-deistviya-v-sourcetree/klonirovanie-repozitoriya.md)
{% endcontent-ref %}

***

## 4. Доустановка плагинов.

Со списком требуемых для доустановки плагинов можно ознакомиться в README проекта. Сторонние плагины перечисленные там они бесплатные. Основные необходимые плагины находятся в репозитории.&#x20;

## **5. Настройка Unreal Engine проекта**

1.  **Первый запуск проекта:**

    * Генерация файлов

    после скачивания проекта нажмите ПКМ по .uproject и выберите пункт “Generate Visual Studio Project Files”\


    <figure><img src="../.gitbook/assets/image (59).png" alt=""><figcaption><p>После этого в проекте должен появиться .sln - файл.</p></figcaption></figure>

***

## **6. Сборка и полная пересборка.**

### <mark style="color:red;">Во время сборки закрывайте проект!</mark>

### Сборка

Откройте .sln - файл, лежащий в корневой папке проекта.

Во вкладке Solution Explorer должна находиться папка Games.\
В её корне должен находиться объект, который называется так же, как и проект Unreal.\
Нажмите ПКМ по этому объекту и выберите “Собрать” (Build)\


<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXd2CMW0jPzTUKAFvRt_cXlDRhKd0OilWKzALA5O0GigOz-GpXbsxDeEUX2yvSnzAdEGzpIU_TLyfbrQL5DfbAk0wDWQNvbdYI26dUK3yWuz8FNdGCjyatLnG2GgdN7MLKJ0OlVgqnAc9VPdF5f-kzPvPA5z?key=MFvsAmq73t2EaIJsyKb_tA" alt=""><figcaption></figcaption></figure>

Как только начнется сборка, рекомендуется слева выбрать “Вывод”, и во вкладке “показывать выход из” выбрать “Сборка” (Show output from build). В Output Log будет указана причина, по которой не собирается проект. Как исправлять самые частые ошибки, указано ниже в пункте 7.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXchqHe_6LNwLLwQGzQMM1G0HlTTqhumgiOFAEggntKdNrp-ShK48hdCGTm1vGiSJ4er3rFxILQKBbE6bpjeCGI-PnNzP8C004r6Pi4RUsljdQZ9ZmEBATc7LraL1PSB1l9fAgkP914jx9eqUEZl2VBltsGE?key=MFvsAmq73t2EaIJsyKb_tA" alt=""><figcaption></figcaption></figure>

### Полная пересборка

Иногда становится необходимо пересобрать весь проект целиком. Для этого нужно удалить папки, в которых хранятся временные данные и собранный код.

1.  Из корневой папки проекта удалите следующие файлы и папки:\


    <figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXf22j24YQEzZCLM-nTRyv9B2B5Y5Hx-PzowxJt_5N9170NNM6NaqRhUT6h6yZsLBiAAYSpHtdcV7cRnqgVt_9mmJbIY2vlPlxGWRuWkwe-MJeBDaQ9rlC5P0YNdmrhizrXO6LrDG6EkjpepwiiDkenq9p0?key=MFvsAmq73t2EaIJsyKb_tA" alt=""><figcaption></figcaption></figure>

    Повторите шаги Генерация файлов и сборка.



## **7. Решение типичных проблем**

*   **Ошибка:**  `Unable to build while Live Coding is active. Exit the editor and` \
    `game, or press Ctrl+Alt+F11 if iterating on code in the editor or game`\
    **Решение 1:** закройте все открытые Unreal Engine и подождите некоторое время, пока все процессы не закроются.\
    **Решение 2:** Зайдите в любой проект Unreal этой версии, и во вкладке Editor Preferences выключите Live Coding.

    <figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcpCNWU0Hu5LQT2tuO0K5oDGXv9_M0ajXOYYt6MS8w5H6NzkmAyHReN9FkNI3rVIGBITSa9vCd7KBslRr7Kdb14hMxhK1J4Vs59vy9JGw_5HUTynob4AoHxsyziwP4B-xCxeL7oSLPrnfMD2b8FdDkJxt0Y?key=MFvsAmq73t2EaIJsyKb_tA" alt=""><figcaption></figcaption></figure>


* Ошибка: `Unable to find plugin ... (referenced via .uproject). Install it and try again, or remove it from the required plugin list.`\
  \
  **Решение:** Ознакомьтесь со списком плагинов (Readme), и установите недостающие на движок.

***

## **8. Полезные ссылки**

* [Документация Unreal Engine](https://docs.unrealengine.com/)
* [Сообщество Unreal Engine](https://forums.unrealengine.com/categories?tag=unreal-engine)
* [Уроки и примеры от Epic Games](https://dev.epicgames.com/community/unreal-engine/learning)



[^1]: Альтернативы: \
    **Rider for Unreal Engine** — рекомендуется для C++ (доступно [здесь](https://www.jetbrains.com/rider/)).
