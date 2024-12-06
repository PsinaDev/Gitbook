# Работа с коммитами

**Важно:** **перед отправкой всегда проверяйте работоспособность коммита, чтобы не испортить команде рабочий опыт.**\


После того как вы закончили работу над какой-то задачей/рядом задач, вам нужно отправить изменения на сервер. Порядок следующий:

### 1. Закоммитьте свои изменения. Сделать это можно во вкладке “Состояние файлов” (File Status)

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXc15L6TWxGAMXGpOMgi2AVmJDlKBFq-EKgEhajVp3LKKRxQ1HUTGAu5KyTnWumzW5gDjhWDKcBI4pPKa-bW0sh2JCSnRFu0yplh4F3HugZD7AEHEy6iigChj58F_ezXQz1w7RCtNK3i6K6jNR5kylg3Yb1c?key=MFvsAmq73t2EaIJsyKb_tA" alt=""><figcaption></figcaption></figure>

### 2. Нажимаете кнопку “закоммитить все” (Stage All)

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXcG_WxGZzNtxFjrNqqo8Rt1oZz6Wl4_m3y9Ye_hdQhPkzeWrCe49hrEto0ftAxWxwBCeBJKn3cMe5U-dJH2C0xoFgQ1k2nm2p125uLGk06JjPNzFSoggvyIHlVTQrEnMDIvtvGdg0IC2N8LBrt7PXNPTit1?key=MFvsAmq73t2EaIJsyKb_tA" alt=""><figcaption></figcaption></figure>

### 3. В нижнем поле пишите описание коммита. Оно должно быть коротким, но содержательным. Можно использовать русские символы.

### 4. Нажимаете кнопку “Закоммитить”(Commit)

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfDdkwOOluElWIrBnw8UPyeb73pe5Q-2kd_3ibxisd9fjhPKpL1IjP2hi_xsf-hbeHkPfOEs2zov622eVajbAo7bb_tsXqxsbSkq5OnRvw-vO1nIX_wRQ_TM6qOKSAeD4-gp0VRCJS6IaVk3hAKgIVwSQzV?key=MFvsAmq73t2EaIJsyKb_tA" alt=""><figcaption></figcaption></figure>

### 5. Перед отправкой нажимаете Fetch (Извлечь) или Pull (Получить). Разницу между этими двумя командами можете прочитать в [Руководстве по командам Git](../rukovodstvo-po-komandam-git-i-chastnym-problemam-s-repozitoriem/raznica-mezhdu-pull-i-fetch.md)

<figure><img src="../../../.gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>

### 6. Если вы нажали "Получить" (Pull),  предварительно выполнив предыдущие шаги и получили ошибку, с большей степенью вероятности это значит у вас конфликт. См.Пункт "Решение конфиктов" ниже.

Обратите внимание на дерево, если основная ветка main (origin/main; origin/HEAD) находится ниже вашего коммита, это значит, что ваша ветка отсоединена от главной. Чтобы это исправить, нужно сделать Merge.

<figure><img src="../../../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>

После этого появится окно, где вам нужно будет выбрать коммит, с которым хотите провести слияние. В большинстве случаев это Origin/Main.\


<figure><img src="../../../.gitbook/assets/image (73).png" alt=""><figcaption><p>Галочки ставить не нужно</p></figcaption></figure>

Затем нажмите Ок и дождитесь окончания слияния.\
Если при слиянии были обнаружены конфликты, SourceTree уведомит вас об этом следующим диалоговым окном:

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXe1hhxrt3jnccczMNNsZjGsUkuPpZBv8NUr_RDVOG2CfLzGZJJfRlvJVFQ7brYpV7KEDjLzzADlFX2gQOil89v-7VH-_mOXzXRFwyS0RQjl3WE8-9yAnG5fsvQj5_-HlA8YClLVrk-4PYai6GoVMTfbvqnp?key=MFvsAmq73t2EaIJsyKb_tA" alt=""><figcaption></figcaption></figure>

### Решение конфликтов

Если это произошло, открывайте “Состояние Файлов” (File Status)

В окне появится автоматически сгенерированный коммит “Merge remote-tracking branch 'origin/main'”. Название лучше не трогать. В окне незакоммиченных изменений будет несколько файлов, конфликты для которых нужно разрешить. Для этого нужно нажать пкм по файлу, и выбрать один из трех способов разрешения. Если вы файл потрогали случайно, то можете отменить изменения (Discard file changes). Или выбрать ту версию файла, которая останется на сервере.\


<figure><img src="../../../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

После разрешения конфликтов и подготовки коммита, нажмите кнопку "Отправить" (Push)
