# Система спавна предметов и лута

Основные классы системы спавна предметов и лута: **GS\_ProtocolTerminate**, **BP\_Spawner** и **BP\_ItemSocket**.

* **GS\_ProtocolTerminate** — отвечает за получение сида, чтобы предметы генерировались одинаково на всех клиентах.
* **BP\_Spawner** — отвечает за создание предметов на сокетах.

#### Настройка предметов и лута

Предметы и лут необходимо настроить в таблицах по следующим путям:

* `ProtocolTerminate/Data/SpawnItemData`
* `ProtocolTerminate/Data/SpawnLootData`

#### Настройка сокетов на карте

Чтобы добавить сокеты на карту:

1. Перетащите **BP\_Spawner** на карту, выберите его и откройте вкладку **Details**.
2.  Найдите нужный массив:

    * **LootSockets** — массив сокетов для спавна лута.
    * **ItemSockets** — массив сокетов для спавна предметов.

    Для выбора сокета используйте пипетку справа от индекса массива и кликните на нужный сокет.

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

3 В **BP\_Spawner** укажите таблицы и ряды, отвечающие за спавн предметов и лута на уровне или в зонах.

<figure><img src="../../.gitbook/assets/image (109).png" alt=""><figcaption></figcaption></figure>

В сокете доступны две переменные:

#### Переменные сокета

* **`bool CanSpawnBox`** — определяет, можно ли заспавнить ящик на данном сокете.
* **`bool LootSocket`** — косметическая переменная, которая изменяет название сокета. Это помогает быстрее находить ошибки или понимать назначение сокета.

#### Настройка таблиц данных (DataTable)

1. **Для лута**
   * Перейдите в папку `ProtocolTerminate/Data/SpawnLootData` и откройте файл `DT_LootSpawnData`.
   * Создайте новый ряд, задайте общую стоимость лута, количество редких предметов, затем укажите этот ряд в **BP\_Spawner**.

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

2. **Для предметов**

* Перейдите в папку `ProtocolTerminate/Data/SpawnItemsData` и откройте файл `DT_ItemSpawnerData`.
* Создайте новый ряд, задайте предметы, их количество, а также количество коробок для спавна, затем укажите этот ряд в **BP\_Spawner**.

<figure><img src="../../.gitbook/assets/image (110).png" alt=""><figcaption></figcaption></figure>
