---
description: Краткая справка об основных системах игры.
---

# Архитектура игры

Игра делится на следующие ключевые модули:

1. **Игровой фреймворк (Game Framework)**: Базовые классы Unreal Engine, расширенные для проекта.
2. **Системы (Subsystems)**: Модули, отвечающие за конкретные игровые механики.
3. **Игровая логика (Gameplay Logic)**: Основные правила и взаимодействия в игре.
4. **Контент (Content)**: Визуальные и звуковые ресурсы.
5. **Интерфейс (UI)**: Система отображения информации игроку.
6. **Отладка (Debug Tools)**: Инструменты для диагностики и тестирования.

***

## Основные модули

### **Игровой фреймворк (Game Framework)**

Использует базовые классы Unreal Engine, такие как `GameMode`, `GameState`, `PlayerController`, и `Pawn`.

* **GameMode**:
  * Управляет правилами игры (например, условия победы).
  * Расширенный класс: `GM_ProtocolTerminate`.
* **PlayerController**:
  * Обрабатывает ввод игрока, переключение камер.
  * Расширенный класс: GamePlayerController.
* **Pawn/Character**:
  * Основные подклассы:
    * `BP_CharacterBase`: Базовый класс всех игроков, имеющий общий функционал.
    * `BP_HumanCharacter`: Игрок-человек.
    * `BP_RobotCharacter`: Игрок-робот.



***

### **Системы (Subsystems)**

Системы реализованы через подсистемы (`Subsystems`) Unreal Engine или независимые модули. Каждая система отвечает за конкретную функциональность.

* **Система инвентаря (Inventory System)**:

Управляет хранением, добавлением и удалением предметов.

Основной класс: `InventoryComponent`.

{% content-ref url="sistema-inventarya/" %}
[sistema-inventarya](sistema-inventarya/)
{% endcontent-ref %}

* **Система взаимодействия (Interaction System)**:
  * Управляет взаимодействием игрока с объектами (например, двери, NPC).
  * Основные классы: \
    `AC_Interactor` - Отвечает за посыл взаимодействия в объекты\
    `AC_Interactable` - Отвечает за прием и обработку Interact сигнала в объектах
  * Дочерние классы: \
    `RoleDependentInteractable` - Фильтрует взаимодействие между ролями

{% content-ref url="sistema-vzaimodeistvii/" %}
[sistema-vzaimodeistvii](sistema-vzaimodeistvii/)
{% endcontent-ref %}

* **Система возможностей (Ability)**
  * Отвечает за статистики персонажа, эффекты, применение скиллов и их обработку.

{% content-ref url="sistema-vozmozhnostei-ability/" %}
[sistema-vozmozhnostei-ability](sistema-vozmozhnostei-ability/)
{% endcontent-ref %}

* **Система оружия (Weapon System)**:
  * Реализует стрельбу, перезарядку и выбор оружия.
  * Основной класс: `BP_Weapon`.

{% content-ref url="sistema-oruzhiya/" %}
[sistema-oruzhiya](sistema-oruzhiya/)
{% endcontent-ref %}

*   **Система анимации (Animation System)**:

    У человека основной класс: `HumanAnimationComponent`



***

### **Игровая логика (Gameplay Logic)**

* **Механика персонажей (Character Mechanics)**:
  * Включает передвижение, способности, использование предметов.
  *   Управляется через компоненты:

      * `AbilityComponent`
      * `InventoryComponent`
      * `Interactor`


* **Предметы (Items)**:
  * Разделены на типы: оружие, расходуемые предметы, ключевые объекты.
  * Логика предметов:
    * `BP_ItemBase`: Базовый класс.
    * `BP_Weapon`: Оружие.
* **Поведение врагов (Enemy AI)**:
  * Построено на Behavior Trees и Blackboards.
  * Основной контроллер: `AI_EnemyController`.

***

**2. Контент (Content)**

* **Анимации (Animations)**:
  * Разделены по типам: персонажи, оружие, окружение.
  * Используются `BlendSpaces`, `Animation Blueprints, etc`.
* **Материалы и текстуры (Materials & Textures)**:
  * Хранятся в папке `Art`.
  * Используются `Material Instances` для оптимизации.
* **Звуки (Audio)**
  * Хранятся в папке `Audio.`

***

***

**Отладка (Debug Tools)**

Реализована через ряд интерфейсов и UMG Debug окон. Подробнее:

{% content-ref url="sistema-otladki-debug/" %}
[sistema-otladki-debug](sistema-otladki-debug/)
{% endcontent-ref %}

***

#### **3. Взаимодействие модулей**

Модули взаимодействуют через событийную систему или напрямую:

* **Игровой процесс**:
  * Игрок → Взаимодействие → Предмет → Система инвентаря.
* **Анимация**:
  * Состояние персонажа → События Blueprint → Animation Blueprint.
* **Оружие**:
  * Игрок → Оружие → Система оружия → Враги.

Диаграмма взаимодействий может быть добавлена в последующих обновлениях документации.

***

#### **4. Расширяемость и поддержка**

* **Добавление новых модулей**:
  * Все новые системы наследуются от базовых классов или интегрируются через Subsystem или как отдельный плагин.
* **Документация**:
  * Каждая система имеет собственный раздел в документации для описания API и сценариев использования.
