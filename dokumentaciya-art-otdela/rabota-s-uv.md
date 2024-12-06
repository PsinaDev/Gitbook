# Работа с UV

## **Аккуратная развертка — залог качественной карты normal и хороших текстур.**

В создании UV есть несколько важных правил. Когда мы создаем развертку, очень важно не только правильно подготовить геометрию, разрезать и развернуть “ювишки”, но и выполнить пару несложных действий.

Раскладывать UV лучше всего руками. Только так мы можем самым лучшим образом организовать пространство. Адекватно разложенная UV, где учтены все пункты данного параграфа, выглядит как-то так:

<figure><img src="../.gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>

## Тексель и правила хорошего тона

На тексель влияет качественная работа с UV. Это значит, что на данном этапе мы сталкиваемся с необходимостью рациональной организации места. Чтобы это сделать, необходимо подойти к процессу развертки с умом и максимально использовать все UV пространство.\


Для начала нам необходимо развернуть всю модель и понять какими UV-шеллами мы располагаем. Потом уже понять какие части модели являются приоритетными для игрока и будут его точкой внимания, а какие — нет (например детали, которые будут видны лишь частично). Таким образом, имея понимание, как модель будет восприниматься игроком, мы можем значительно увеличить общее разрешение текселя, не меняя разрешение самой карты.\


Пример: допустим, мы имеем автомобиль, который переворачивать в игре не планируется. Поэтому все элементы, включая днище, которые нам сильно видны не будут, следует отскейлить, чтобы дать больше пространства важным деталям.

\


<figure><img src="../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

На развертке днище будет иметь меньший тексель, чем другие детали:

![](https://lh7-us.googleusercontent.com/mL2mGA3BEgfkSkOnspD39FU-wWVeHBq29-gv34ASGsX7mq9fl3Nlmzn5nVGnjrwJIl0T2uD-eE3WQw23N5XUh08UY2WVZjwTlDwAUynej1Q-aBq1dr-e-U2LAk_f-rR9lCrQAA5WZyXNEF62IhRlH7scZlqlIKHnFrNIiCfyP5vcecxFMJFpnAuHf_ZFOA)

&#x20;

\


<figure><img src="../.gitbook/assets/image (63).png" alt=""><figcaption></figcaption></figure>

## Антиалиайзинг, швы и проблемы с местом

На финальное качество модели в игре влияет несколько факторов, которые необходимо учитывать. Это, в основном, касается генерации мипмап. Многие вещи, которые выглядят хорошо в большом разрешении, могут выглядеть плохо на маленьком, после автоматической генерации мипмап движком. Нам нужно учесть это, чтобы избежать проблем на мипмапах в дальнейшем:

Кривые шеллы нужно выравнивать. Держать их в кривом виде плохо как для запекания швов, так и для рационализации пространства. Антиалиайзинг на кривых шеллах в местах швов будет делать нам “лесенки” из пикселей, если мы их не выпрямим. Это особенно ощутимо на картах с маленьким разрешением.

&#x20;

<figure><img src="../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>

Не стоит бросать шеллы на UV-пространстве как попало. Их следует класть так, чтобы прямые линии были прямыми (при скалировании и генерации мипмап прямая превращается в красивый ряд пикселей, в то время, как кривая становится рубленой и в месте шва начинаются проблемы).

&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/CYz2XO6ofEsktnlAZcc098IDdjOIoySgKM2P_Gq4rAX0Yy-h-EF0xlflNmA3ADfx5Pw3yTBFDfFrSKTvW9bLQUUUnNQ9_H6tonExBd0p5_nnIlEl8pHlelKbXNYzxTKHzqTpccS-pVF9J_sR-aCbfNdR7i0XqLqW6iRTztPrcoAnFDrtYbQhlnI9tilZiA" alt=""><figcaption></figcaption></figure>

Нужно постоянно следить за тем, чтобы UV не были кривыми. Чекер на модели должен выдавать ровные квадраты.

![](https://lh7-us.googleusercontent.com/lPyvgXaXs7w2ELAc7depcgtElRikuqp9RFStskTRELF9ZgBX64yBdzJi8VYc0rQiVKbCRmclYYkVF8dfaFDBgAQz_eQqYBP0TqZ9D4AI3Vo9yTQvlKyTBMQeLD4-d1ML4bt4rnE-0Yru93Lsn0HbpqHI9XD0HatcXZfEuNO2iYp7stwDj55Op3yvLsFQEQ)

## Направление UV шеллов

Иногда так случается, когда нам нужно наложить в движке процедурную текстуру чего-нибудь на модель. Чтобы такая текстура легла ровно и без проблем, нужно не только чтобы все части модели, на который планируется назначить конкретный материал, имели одинаковый тексель, но и чтобы направления этих шеллов были одинаковыми. Например, все смотрели вверх и не были флипнутыми.

## Overlap и паддинг

Экономить нужно с умом. Например, используя оверлаппинг важно понимать что реюзать нужно только те части текстуры, которые одновременно не попадают в поле зрения игрока. Когда мы смотрим на объект, то видим максимально 3 его стороны:

![](https://lh7-us.googleusercontent.com/ct_CidLVzrdJu4h5NpkgR2d0iWMuffp6ds81Lsu-_x8iiii9X2p9K1rgy9byCi7bpjSW5kTa84Vsbm-fe73rkfn10Dp-oiVFfUAaSK2bam7Bd2bF9rksjEGjQI8WVlUqprzySUby1Ao5R_xgjwJYN98qmZRriQxzJWz1FstiIxmNYAjfkKZRu9MNztQPog)

В теории все эти 3 стороны можно оверлапнуть. Но на примере выше мы видим что верхняя и нижняя части сильно отличаются, а вот боковые есть прямой смысл зеркалить. Оверлапинг сильно экономит место на развертке и позволяет нам получить лучший тексель при том же разрешении текстуры.

![](https://lh7-us.googleusercontent.com/hiJfkQEgkRK0Lx-2O5SERRBsyMVSpVeEzc8dMY84jGCqVfB0Ul1VUSJ_HmpDV36945jtQ38BRX72LRIGt7keZLmKHnT4IEN0cYGj7hVfsv8IA0_ZOsUw9ub5HJkxO8b1kjrRb7cHaHvzDIqm39DhIoHO962TSN-kjNzMXlvyOxAaIe0j1ui1mVZO97U9ag)

&#x20;

Особенно много места можно выиграть, если заоверлапить крупные куски.

![](https://lh7-us.googleusercontent.com/O_HLme4W9ccy8Zaoi2Y8XCOIlZhTNly47P6Vn4RjV02yiUbjrron_W1_0hUucE9FU88yDWopyBqZmqUbT5k1UMt3RdXDL-td6r-68ppGqLxibugX7PlJUi9f_nAVNao4MlpFeyjjXS9L-hVd8rvUYbk5qD-GQAHrzjDI_PZmtseRqc_zFKoq5Sr-PxwZsA)

## **Padding** <a href="#null" id="null"></a>

Важно соблюдать паддинг. Нельзя делать шеллы без соблюдения пространства между ними. Паддинг нужно соблюдать.

2048 — 10

4096 — 20

При экспорте текстур также важно чтобы стояло сохранение границ:

&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/1hM-E_sMbR8isV2QM3UH2SwJtZi1BlvwY8bpFNCLjgcSQzALFoKXwr41rriVEHB8ZFkTJniFBmeHw5HkZ2njNcCPA2F-ZE-5dQVkkgL_lyfSAy2D4V7vjdmdGB94o3tYOpACVlf8ZD5yjIPcssLg2QEm82BEb3sJXO5ztfzZmrTt54FOsw8zt1vLaeC7bA" alt=""><figcaption></figcaption></figure>

Если этого не сделать, на модели могут возникнуть проблемы в области швов.

![](https://lh7-us.googleusercontent.com/8YuoYyxG-nsK9CK_2hp2OMJWaOfSnUH4SCaPtaeKhEUecc4D1xJZ76dV_iRE2hEto3qy2wjc6SMR_yGc6Ycx5xMtVQHTA5QSKMCee-Bi2aPqiOSdOzVFMU2CDHtMa8VTdhfjGWJO_nrkPsqHPTd--JHxP-tw_hmz_4c_FgvrYvISxhYKIYKv63l1yyI_Xw)
