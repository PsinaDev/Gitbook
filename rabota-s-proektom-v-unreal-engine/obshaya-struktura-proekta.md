---
description: >-
  На этой странице будет расписана структура папок проекта и как ими
  пользоваться
---

# Общая структура проекта

### Всегда работайте и помещайте контент в правильную папку! Не нарушайте структуру проекта и соблюдайте нейминги для поддержания комфорта других разработчиков!

```
ProjectRoot/
├── Content/                    # Основной контент проекта
│   ├── Art/                    # Визуальные ресурсы
│   │   ├── Animations/         # Анимации
│   │   ├── Assets/             # 3D-модели и текстуры
│   │   ├── Characters/         # Персонажи
│   │   │   ├── Materials/      # Материалы персонажей
│   │   │   ├── Textures/       # Текстуры персонажей
│   │   ├── Materials/          # Общие материалы
│   │   ├── Meshes/             # Общие 3D-модели
│   ├── Audio/                  # Звуковые файлы
│   ├── Core/                   # Основные игровые системы
│   │   ├── Framework/          # Фреймворк игры (GameModes, PlayerStates)
│   │   ├── Player/             # Игрок и его компоненты
│   │   ├── Systems/            # Игровые подсистемы (инвентарь, взаимодействие, оружие)
│   ├── Data/                   # Данные (например, общие таблицы и Data Asset)
│   ├── Logic/                  # Логика игрового процесса
│   │   ├── Items/              # Предметы (кейсы, оружие, инструменты)
│   ├── Maps/                   # Игровые уровни
│   │   ├── DevOnly/            # Карты для разработки и тестирования
│   ├── UI/                     # Интерфейс пользователя
│   │   ├── DebugUI/            # Интерфейсы для отладки
│   │   ├── UIMaterials/        # Материалы UI
│   ├── Utilities/              # Утилиты для редактора и работы с проектом
│       ├── EditorUtilities/    # Сценарии для редактора

```

#### Описание ключевых разделов

1. **`Art/`**\
   Хранит все визуальные элементы игры: анимации, модели, материалы, текстуры. Организовано по типам ресурсов и их использованию.
2. **`Audio/`**\
   Содержит звуковые ресурсы и все что связано со звуком, такие как эффекты, музыка и озвучка.
3. **`Core/`**\
   Раздел для базовых игровых систем: логики игрока, фреймворков, подсистем (инвентарь, взаимодействие, HUD).
4. **`Data/`**\
   Таблицы данных и конфигурации, описывающие параметры игры, например, характеристики предметов или персонажей.
5. **`Logic/`**\
   Содержит сценарии и логику, управляющую поведением предметов, врагов или других игровых объектов.
6. **`Maps/`**\
   Хранит уровни проекта, включая рабочие и тестовые версии.
7. **`UI/`**\
   Раздел, посвящённый интерфейсу пользователя. Материалы и элементы UI разбиты на основные и отладочные.
8. **`Utilities/`**\
   Скрипты и инструменты, которые помогают автоматизировать или оптимизировать разработку.
