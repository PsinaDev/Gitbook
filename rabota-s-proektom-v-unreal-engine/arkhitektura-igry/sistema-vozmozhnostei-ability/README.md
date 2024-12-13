# Система возможностей (Ability)

**Attribute (Атрибут)**

Атрибут — это параметр, описывающий свойства игрового объекта или персонажа. Он хранит числовые значения, которые могут изменяться в процессе игры. Например: здоровье, мана, энергия, урон, скорость.

***

**Gameplay Tag для атрибутов**

**Gameplay Tag** — это метка, которая применяется к атрибуту для его идентификации или классификации. Она используется для определения логики геймплея, связывания атрибутов с эффектами и другими системами.

**Пример:**

* Атрибут `Health` может быть связан с меткой `Attribute.Player.Health`, указывая, что это параметр, связанный со здоровьем.
* Метка `Attribute.Player.Mana` указывает на ресурс маны.

**Зачем это нужно:**

* Для удобной категоризации атрибутов.
* Для определения, какие механики или эффекты могут влиять на атрибут.
* Для быстрого поиска и фильтрации данных в системе.

***

**Base, Current, Min и Max Value**

1. **Base Value (Базовое значение):**
   * Исходное значение атрибута.
   * Оно не изменяется напрямую, а используется как основа для расчёта текущего значения.
   * Пример: Максимальное здоровье в игре — 100. Базовое - 80 (например 1 уровень). Таким образом в начале игры по умолчанию текущее будет 80. Игрок получает урон в процентах от базового, допустим 10%. Тогда текущее будет 72, базовое останется 80, а максимальное - 100. На игрока наложен эффект, который должен в соответствии с его уровнем восстановить атрибут. Восстанавливаться он будет до базового (для этого есть параметр bRestorable - сбрасывает атрибут при отсутсвии эффектов), а не для максимального.
2. **Current Value (Текущее значение):**
   * Значение, которое используется в данный момент времени.
   * Может изменяться в ходе игры, например, при получении урона или восстановлении здоровья.
   * Пример: У игрока 75/100 здоровья (текущее здоровье — 75).
3. **Min Value (Минимальное значение):**
   * Нижняя граница атрибута.
   * Значение атрибута не может быть меньше этого значения.
   * Пример: Здоровье не может упасть ниже 0.
4. **Max Value (Максимальное значение):**
   * Верхняя граница атрибута.
   * Значение атрибута не может превышать эту границу.
   * Пример: Максимальное здоровье игрока — 100.

При всех математических рассчетах с атрибутами значение всегда будет ограничено Min/Max Value.

***

**Attribute Set (Набор атрибутов)**

**Что это:**\
Группа атрибутов, связанных с определённым игровым объектом, классом или системой. Это удобный способ организовать параметры.

**Пример:**

* **Набор атрибутов для игрока:**
  * `Health` (здоровье).
  * `Mana` (мана).
  * `Stamina` (выносливость).
* **Набор атрибутов для оружия: (оружие  тоже может иметь абилити систему, в случае если для этого есть смысл, например игрок накладывает на оружие свой классовый эффект, повышающий точность оружия)**
  * `Damage` (урон).
  * `Range` (дальность).
  * `Accuracy` (точность).

**Почему это важно:**

* Позволяет группировать и структурировать параметры.
* Упрощает их настройку и управление.
* Помогает разграничить области использования (например, боевые атрибуты отдельно от экономических).
