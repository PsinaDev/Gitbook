# Разница между ECollisionChannel и ETraceTypeQuery

#### **Разница между `ECollisionChannel` и `ETraceTypeQuery`**

`ECollisionChannel` и `ETraceTypeQuery` — это механизмы в Unreal Engine для управления коллизиями и трассировками. Оба используются для проверки взаимодействия объектов, но различаются в целях и реализации.

***

#### **`ECollisionChannel`**

**Описание:**\
`ECollisionChannel` — это перечисление (Enum), которое определяет тип канала коллизии для объекта. Оно используется для настройки взаимодействия объектов с другими через системы коллизий.

**Этот тип определяет заранее заложенные реакции на взаимодействие с другими коллизиями**

**Основные характеристики:**

1. **Используется для настройки физического взаимодействия:**
   * Определяет, как объект будет блокировать, перекрывать или игнорировать другие объекты.
   * Пример: `ECC_WorldStatic`, `ECC_Pawn`.
2. **Настраивается через редактор или код:**
   * Можно создать пользовательские каналы в **Project Settings → Collision → Object Channels**.
3. **Применяется к компонентам, взаимодействующим с физическим миром:**
   * Например, статические и скелетные меши, коллайдеры, капсулы.
4.  **Реакции коллизий:**

    Например, по умолчанию ObjectTypePawn имеет следующую реакцию на различные Object и Trace Response:

    <figure><img src="../../../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>

***

#### **`ETraceTypeQuery`**

**Описание:**\
`ETraceTypeQuery` — это перечисление, которое определяет тип запросов для трассировок. Оно используется для выполнения запросов, таких как **Line Trace**, **Sweep Trace**, и **Overlap**.

**Основные характеристики:**

1. **Используется для выполнения трассировок:**
   * Определяет, какие объекты должны быть проверены на линии или внутри объёма.
2. **Облегчает управление трассировкой:**
   * Представляет собой маппинг (`Mapping`) к конкретному `ECollisionChannel`.
   * Автоматически преобразует каналы коллизии в тип запроса.
3. **Ограничен предустановленными типами:**
   * Пример: `TraceTypeQuery1`, `TraceTypeQuery2`.
4. **Менее гибок, чем `ECollisionChannel`:**
   * Не может напрямую взаимодействовать с объектами, не имеющими настроенного `Collision Channel`.

***

#### **Как `ECollisionChannel` и `ETraceTypeQuery` взаимодействуют**

1. **`ETraceTypeQuery` преобразуется в `ECollisionChannel`:**
   * Когда вы выполняете трассировку с помощью `ETraceTypeQuery`, движок автоматически преобразует её в соответствующий канал `ECollisionChannel`, настроенный в проекте.
2. **Пример преобразования в коде:**
   *   Используя функцию:

       ```cpp
       UEngineTypes::ConvertToCollisionChannel(TraceTypeQuery1);
       ```

       `TraceTypeQuery1` будет преобразован в свой маппинг, например, `ECC_Visibility`.
3. **Настройка в Project Settings:**
   * В разделе **Project Settings → Collision → Trace Channels** вы можете настроить соответствие между `ETraceTypeQuery` и `ECollisionChannel`.

***

#### **Когда использовать `ECollisionChannel` или `ETraceTypeQuery`?**

| **Критерий**                             | **ECollisionChannel**        | **ETraceTypeQuery**                         |
| ---------------------------------------- | ---------------------------- | ------------------------------------------- |
| **Настройка физического взаимодействия** | Да (основной инструмент).    | Нет.                                        |
| **Трассировка (Raycasts)**               | Да, но через каналы.         | Да, основной инструмент для трассировки.    |
| **Создание пользовательских типов**      | Гибко через Object Channels. | Ограничено Trace Channels.                  |
| **Гибкость и контроль**                  | Высокая.                     | Ограничена маппингом к `ECollisionChannel`. |
| **Совместимость с физикой**              | Полная.                      | Только через преобразование в канал.        |

***

Эти два инструмента идеально дополняют друг друга, обеспечивая гибкость при проектировании систем взаимодействия.
