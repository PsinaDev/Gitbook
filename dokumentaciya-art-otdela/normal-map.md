# Normal Map

При подготовке lowpoly-модели очень важно, чтобы карта normal выполняла задачу добавления геометрии, а не функцию компенсации шейда. Это не только правило хорошего тона, но и необходимое условие для правильной генерации мипмап. Поэтому шейды на лоуполи и на хайполи должны максимально совпадать. Если шейд на лоуполи сильно отличается от того что мы имеем на хайполи, это место компенсируется на карте, как видно на примере ниже.

<figure><img src="https://lh7-us.googleusercontent.com/N-1KL5m0KZjFTDwviC4fPqum3mx3R-InYH_w47-EUtK4sJYLCOYXXBEPCzmdWpbUYPwGm_oHkhfdUCVDccXmiRFWOj2sYqdpqga04WKqElh2CZnyLlXHcUUcqlKHenE-Nm1W02s4hQXZp0fFmr1xqbKa_ZNPBMeTW8mJbcv6JrvLUt--GNLAZ22gIDZVrA" alt=""><figcaption></figcaption></figure>

То есть, на выходе у нас в обоих случаях получается идентичный результат, но карта нормала сильно отличается в области мест, где произошла компенсация разницы геометрии. И эти места в итоге при ресайзе (когда будут генерироваться мипмапы) могут привести к сильной потере в качестве. Для избежания проблем связанных с компенсацией, необходимо добиться максимально чистой карты normal, то есть, выровнять геометрию на лоуполи так, чтобы подобные места отсутствовали:

<figure><img src="https://lh7-us.googleusercontent.com/tOrz0UAr6hAmY1SH1WiBh9FTKnat2LMcB9xeVyWfssQAfNePe64fIvd01NhfWiQOlO4GRqtBTJv8QFYmAkOoxMuYAVRF1w0Pu05FE2An_4zdjjsHWeF48x9-ZH--Wk5joQMY57VBfKlide1_asuki-d-LSo8wnLr3pSfvyrbV7-k5eDzK_79yISWN8JrXw" alt=""><figcaption></figcaption></figure>

Хороший шейд для данного места выглядит так:

&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/MYjFl1oexoEtuE8tuTtGtKWzGrxnoFlEnoUm9hjJUF8rzqSZXvoM0Mzcmo32P6Nc3fw_WlLGuHYt5fqhBwVdVOAoCiO2YJC-je5nHRCDN-ESOp4Sqp0wE-0EK30fHsQFRzpQ-G7n-oTKVpia-OmPKc1QkKPNWbhD_OhIfQUr31rMJY27BjdbfHIrNVzZ7w" alt=""><figcaption></figcaption></figure>

То есть, в карте normal нам нужна информация только в тех местах, которые мы реально хотим детализировать за счет хайполи. Если место на хайполи и на лоуполи ровное, то мы избегаем жестких градиентов в нормале и вообще любой лишней информации, которая не выполняет функцию детализации нашего объекта.

Смотрим еще один пример: сверху у нас лоуполи с запеченным нормалом. Слева ровный шейд в области отверстий, а справа наоборот — кривой шейд, который в итоге компенсирует карта normal. Нам нужен такой результат, как слева, где нормал просто добавляет нам фаски на отверстия, а область которая у нас ровная, таковой и остается в карте normal.

&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/3gHXY_C7u_Zf-Vq3CrUQFu85MseatLvHxZ2fq5KinMGUXvNA_0-jpIryRnPr31c89Sf4SeyYipSl5U9e57014j1LL3y8Tk8cr3OlR_fy0RaoYbL9NjiqLOi6JpE6SBhSdgHcQ70tw7iJrCrk-GsU_p2lWQQJJ-S_uHccdyatiY-Ccny-0k9k1qn5Qifeng" alt=""><figcaption></figcaption></figure>

Итак, что же делать, если у нас уже вышел плохой шейд? Для начала убедиться что мы все сделали верно: сделали нашей модели soften edge, потом проставили harden edge в местах разрывов на uv.

Для выравнивания шейда у нас несколько действий:

Average. Мы можем выделить проблемную область и применить к ней функцию average, если проблема возникла на плоской поверхности. То есть, после того, как мы сделали нашей модели soft edge и проставили в местах разрывов uv hard edge, мы выделяем нужную нам область и выравниваем на ней нормали так, чтобы они были перпендикулярны к фейсам. Тут стоит учитывать, что кроме стандартных средств также существует и много дополнительных тулов и скриптов под разный софт (как пример, для Мауа есть Flatten Faces на Python).

Если шейд проблемный во многих местах одновременно, либо не выравнивается простыми действиями, то можно просто отрезать проблемную зону на uv, либо даже отделить геометрию (в месте разрыва uv получается не 1 вертекс, а 4, то есть, для видеокарты разрыв на uv = разрыв меша. Поэтому мы спокойно можем детачить геометрию для удобства работы с шеллами)

&#x20;

<figure><img src="https://lh7-us.googleusercontent.com/cueeerzcdyW6rl94bQrlEwSJHo1lONILyM2T_ZK8bc0f0doyOqN6x3ZuLHp12hxV4otI2nwi6enf-BB4ibpZNN7xEkOhQDDoZEtJYit3e2b03hBNbK7pfAnsIbbCNCnh6uq6ApubTihjZ-A8grgtIGmAM8NsOuqWFnU1J_hE9fDKp0wxtDIlpQiJelFeUQ" alt=""><figcaption></figcaption></figure>

Отрезаем нужный нам кусок и выравниваем его. Если у нас есть примыкающие полигоны, как на примере ниже, мы их тоже отрезаем.

<figure><img src="https://lh7-us.googleusercontent.com/J9CGTXtwCSoZtPcyB06tnghHas2PCzfmJej7ivjLUDuejMpjoaZMlygnZFpIMupjCtFdcdal9lyp-ok8EcUDrJxb2fQXGopC9vfjMWAoPjyfI7aXsOrNoyOzrkuIJMetIho2w9Jc9KWjpC0e0U1W99r8EkfLiuEjAwAEFtjwM9MBpvbfW_fRISj69YLnUw" alt=""><figcaption></figcaption></figure>

После манипуляций, меш можно склеить, сохранив все смус группы (также в некоторых случаях перед склейкой вертексов можно залочить нормали, чтобы не слетели группы сглаживания).
