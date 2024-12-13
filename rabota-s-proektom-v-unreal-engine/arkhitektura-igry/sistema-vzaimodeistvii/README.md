---
description: >-
  В этом документе будет описано взаимодействие и работа с системой
  взаимодействий (InteractionSystem) и её основными классами.
---

# Система взаимодействий

Основной код системы находится в Plugins/InteractionPluginByPsina

Плагин рассчитан на использование Enhanced Input.&#x20;

## `AC_Interactor`

### Метод имплементации:

*   Компонент должен быть помещен в PlayerController или игровой Pawn. \


    <figure><img src="../../../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>
*   На Listen-event InputAction Started и Completed, который вы хотите использовать для взаимодействий, вызовите функцию Interaction Input. Передайте во входные параметры Input Action и Boolean Action Value\
    \


    <figure><img src="../../../.gitbook/assets/image (106).png" alt=""><figcaption></figcaption></figure>



<figure><img src="../../../.gitbook/assets/image (78).png" alt=""><figcaption></figcaption></figure>

Управляемые параметры

* **Detection mode** Режим обнаружения объектов, доступных для взаимодействия; Enum\
  `EBP_InteractionMode::CharacterProximity` - Будет выбран ближайший объект по мировым координатам относительно персонажа.\
  `EBP_InteractionMode::CameraProximity` -  Будет выбран ближайший к центру Viewport объект.
* **DetectionFrequency -** Частота обновления списка доступных объектов; сек
* **bAddLayout** - Добавлять ли курсор по центру экрана; Boolean
* **LayoutWidgetClass -** Класс LayoutWidget; UserWidgetClassReference
* **Detection Radius** - Радиус обнаружения интерактивных объектов вокруг персонажа; UE Units
* **Detection Channel -** Канал коллизии для обнаружения объектов.&#x20;
* bIsActiveOnStart - определяет, активировать ли компонент при начале игры; Boolean

Для Runtime управления параметрами, вынесены следующие функции:

<figure><img src="../../../.gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>

## `AC_Interactable`

### Метод имплементации:

* Добавьте этот компонент к Actor, который должен быть интерактивным.

<figure><img src="../../../.gitbook/assets/image (81).png" alt=""><figcaption></figcaption></figure>

* Укажите DataTableInfo\
  \
  в Uproperty стоит фильтр на таблицы с правильной структурой. Если таблицы в выпадающем меню нет, её надо создать. Подробнее

{% content-ref url="../../instrukcii-po-razrabotke/rabota-s-tablicami-i-assetami-dannykh.md" %}
[rabota-s-tablicami-i-assetami-dannykh.md](../../instrukcii-po-razrabotke/rabota-s-tablicami-i-assetami-dannykh.md)
{% endcontent-ref %}

<figure><img src="../../../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>

### Взаимодействие с таблицей для Interactable компонента

Все данные для интерактивных объектов унифицированы и хранятся в Data Table. \
По умолчанию таблица хранится в `ProtocolTerminate/Data`

<figure><img src="../../../.gitbook/assets/image (85).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>

#### Расшифровка параметров таблицы для интерактивных объектов

В приведенном интерфейсе перечислены параметры, которые задают поведение и свойства интерактивных объектов в Unreal Engine. Вот их детальное описание:

***

**1. DisplayText**

**Описание:** Текст, отображаемый пользователю для описания объекта.\
**Пример:** "Interact with me!" – подсказка, которая объясняет, что можно сделать.

***

**2. TooltipText**

**Описание:** Подсказка, отображающая дополнительную информацию при наведении на объект.\
**Пример:** "Press that button!" – сообщение с инструкцией.

***

**3. InteractionType**

**Описание:** Тип взаимодействия с объектом.\
**Значения:**

* **Press** – одноразовое действие при нажатии кнопки.
* **Hold** – действие, требующее удержания кнопки. Заполняет прогресс-бар в виджете.
* Pulse - действие, требующее многократного нажатия кнопки. Заполняет прогресс-бар на 1/n значение, в то время как он убывает с заданной скоростью. Имеет 2 исхода - Success и Fail, отображаемых через bSuccess в Event Dispatcher OnInteract.

***

**4. InteractionDuration**

**Описание:** Время, необходимое для выполнения взаимодействия (актуально для типа "Hold").\
**Пример:** Если значение равно `3.0`, игроку нужно удерживать кнопку в течение 3 секунд.

***

**5. DelayBetweenInteraction**

**Описание:** Задержка между повторными взаимодействиями.\
**Пример:** Значение `1.0` указывает, что повторное взаимодействие возможно только через секунду.

***

**6. Num Of Target Clicks.**

**Описание:** Количество кликов, требуемых в идеальных условиях для заполнения шкалы. См. DecreaseTimeFactor\
**Пример:** Значение `3.0` означает, что один клик будет заполнять треть шкалы.

***

**7. DecreaseTimeFactor**

**Описание:** Скорость убывания, сек.\
**Пример:** Значение `1.0` означает, что с полностью заполненной шкалы до 0 значение изменится за 1 секунду. Чем меньше это значение и больше количество кликов, тем сложнее будет пройти QTE.

***

**6. bStartWithInteractionActive**

**Описание:** Флаг, определяющий, активен ли объект для взаимодействия сразу при старте.\
**Значения:**

* **True** – объект доступен для взаимодействия.
* **False** – объект изначально неактивен.

***

**7. bDetectWhenObstructed**

**Описание:** Проверяет, должен ли объект быть доступным для обнаружения игроком, если путь к нему заблокирован.\
**Значения:**

* **True** – взаимодействие возможно через препятствия.
* **False** – препятствия блокируют взаимодействие.

***

**8. bAllowInteractionWhenObstructed**

**Описание:** Позволяет взаимодействие с объектом, даже если путь к нему перекрыт.\
**Значения:**

* **True** – объект можно использовать через препятствия.
* **False** – препятствия делают объект недоступным.

***

**9. ObstructionTraceChannel**

**Описание:** Канал трассировки, используемый для проверки препятствий (коллизий).\
**Пример:** `Visibility` – стандартный канал, проверяющий видимость объекта.\
**Подробнее:**

{% content-ref url="../../instrukcii-po-razrabotke/obshaya-spravka-po-kolliziyam/" %}
[obshaya-spravka-po-kolliziyam](../../instrukcii-po-razrabotke/obshaya-spravka-po-kolliziyam/)
{% endcontent-ref %}

***

10. **ObstructionIgnoreOptions**

**Описание:**  Опция позволяет выбрать, кого игнорировать при выполнении проверки на препятствие. \
**Пример:** `Owner` - весь Actor, к которому добавлен компонент; `AttachParent` - только компонент, к которому прикреплен AC\_Interactable; `None` - Actor будет учитываться в проверке.



**11. ResponseInputAction**

**Описание:** Связанное действие ввода для взаимодействия с объектом.\
**Пример:** `IA_Interact` – действие, соответствующее кнопке взаимодействия.

***

**12. ResponseMappingContexts**

**Описание:** Контекст ввода, используемый для определения доступных действий при взаимодействии. Необходимо для получения кнопки, привязанной к InputAction и выведением её в виджет\
**Пример:**

* **Index \[0]: IMC\_GeneralInputs** – общий контекст ввода для всех интеракций.

***

**13. MaxHoverDistance**

**Описание:** Максимальная дистанция, на которой объект становится интерактивным (можно навести).\
**Пример:** Значение `300.0` ограничивает взаимодействие в радиусе 300 единиц.

***

**14. MaxOverlapDistance**

**Описание:** Максимальная дистанция для пересечения (Overlap), при которой взаимодействие возможно (по умолчанию появляется треугольничек).\
**Пример:** Значение `600.0` задаёт предел на 600 единиц для перекрытия области взаимодействия.Заполните в соответсвии с расшифровкой выше.

### Доступные методы

<figure><img src="../../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

## **Доступные делегаты**

<figure><img src="../../../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (101).png" alt=""><figcaption></figcaption></figure>

1. **OnInteract (InteractorComponent, bSuccess)**\
   Вызывается при выполнении или не выполнении (актуально для pulse) условиях взаимодействия.&#x20;
2. **OnHoverUpdated (bIsBeingHovered, Interactor, Interactable)**\
   Вызывается при обновлении состояния Hover у компонента. Используется для косметических целей; По умолчанию включает/выключает выдимость кнопки у виджета
3. **OnOverlapUpdated (bIsOverlapping, Interactor, Interactable)**\
   Вызывается при обновлении состояния Overlap у компонента. Используется для косметических целей; По умолчанию включает/выключает отображение треугольника у виджета.
4. **OnPercentUpdated (Float: Percent)**\
   Вызывается при обновлении прогресса взаимодействия (актуально для Hold и Pulse). Выдает значение от 0 до 1 и используется для косметических целей; По умолчанию для заполнения прогресс-бара у виджета.
5. **OnUpdateWidgetInfo (Interactable)**\
   Вызывается для обновления InteractionData из таблицы в виджете (ToolTipText, DisplayText, etc.)



#### **FAQ (Часто задаваемые вопросы по интерактивным объектам)**

***

**1. Почему объект не реагирует на взаимодействие?**

**Причины и решения:**

* Убедитесь, что параметр **bStartWithInteractionActive** включён (True).
* Проверьте канал коллизии, используемый в **ObstructionTraceChannel**, и убедитесь, что объект правильно взаимодействует с трассировкой. И предметы в руках персонажа/возле персонажа не блокируют обнаружение.
* Проверьте настройки коллизии объекта. Он должен быть настроен на реагирование на используемый канал (например, **ECC\_Visibility**).

***

**2. Что делать, если взаимодействие не срабатывает через препятствие?**

**Решение:**

* Включите флаг **bDetectWhenObstructed** для проверки трассировки через препятствия.
* Если требуется разрешить взаимодействие даже через препятствия, включите **bAllowInteractionWhenObstructed**.

***

**3. Как увеличить радиус взаимодействия?**

**Решение:**

* Измените параметр **MaxHoverDistance** для увеличения дистанции наведения.
* Также проверьте параметр **MaxOverlapDistance**, чтобы он соответствовал новым требованиям.

***

**4. Как назначить новую клавишу для взаимодействия?**

**Решение:**

* Поменяйте клавишу соответсвующему InputAction в MappingContext.
* Свяжите необходимое действие с параметром **ResponseInputAction**, указав соответствующее действие (например, `IA_Interact`).
* Убедитесь, что в **ResponseMappingContexts** указан правильный контекст ввода (например, `IMC_GeneralInputs`).

***

**5. Почему не отображается текст взаимодействия?**

**Причины и решения:**

* Проверьте, задан ли текст в **DisplayText** и **TooltipText**.
* Убедитесь, что логика отображения интерфейса подключена к вашему интерактивному объекту.

***

**6. Можно ли использовать несколько каналов для обнаружения препятствий?**

**Ответ:**\
Нет, параметр **ObstructionTraceChannel** поддерживает только один канал. Однако вы можете настроить поведение объекта для взаимодействия через другие подходы, такие как кастомный ObstructionTraceChannel с настроенными кастомно реакциями.

***

**7. Как задать анимацию или эффект при взаимодействии?**

**Решение:**

* Подвяжите необходимые действия на нужные делегаты (Event Dispatcher)

***

**8. Как запретить взаимодействие временно?**

**Решение:**

* Вы можете динамически включать или отключать взаимодействие через скрипт:

<figure><img src="../../../.gitbook/assets/image (88).png" alt="" width="351"><figcaption></figcaption></figure>

***

**9. Как проверить, что препятствие корректно блокирует трассировку?**

**Решение:**

* Используйте отладочные инструменты. Подробнее:

{% content-ref url="../sistema-otladki-debug/" %}
[sistema-otladki-debug](../sistema-otladki-debug/)
{% endcontent-ref %}

***

**10. Как интегрировать кастомный тип взаимодействия?**

**Решение:**

* Добавьте новую логику в **InteractionType**, используя кастомное перечисление (enum), если требуется.
* Определите, как это взаимодействие должно работать (например, переключение, двойное нажатие).
* Внесите соответствующие корректировки в код AC\_Interactor.

