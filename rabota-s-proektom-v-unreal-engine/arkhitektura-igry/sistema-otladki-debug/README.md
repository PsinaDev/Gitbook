---
description: Общие сведения
---

# Система отладки (Debug)

Для общего понимания профилирования игровых процессов в UE, ознакомьтесь с ресурсами по ссылками ниже:\
\
[Unreal Debugging Tools (YouTube)](https://www.youtube.com/watch?v=XC_ntVpHg80)\
[Advanced Debugging in Unreal Engine (Documentation)](https://dev.epicgames.com/community/learning/tutorials/dXl5/advanced-debugging-in-unreal-engine)\
[Gameplay Debugging in Unreal Engine (Documentation)](https://dev.epicgames.com/documentation/en-us/unreal-engine/using-the-gameplay-debugger-in-unreal-engine)\


## Основное  дебаг меню в игре

По умолчанию и на момент написания данной статьи вызывается по кнопке Period (точка). В зависимости от Ru/En раскладки, это может быть  кнопка \[/] или \[Ю].



### Пользовательская справка

Главное окно дебага состоит из 5 элементов:

1. Быстрый доступ к консольным командам (список расширяем) Слева - выпадающее меню команд. Справа - кнопка выполнения команды.
2. Кнопка Show PRAS debug - включает/выключает окно отладки Procedurak Recoil Animation System - Системы процедурных анимаций. Используется в основном аниматорами.
3. Окно - список доступных компонентов для отладки. Генерируется автоматически.
4. Текущая роль игрока.
5. Область для отображения дочерних виджетов. Туда автоматически помещаются полученные из компонентов виджеты по интерфейсу `DebugActorComponentInterface.`

<figure><img src="../../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

### Список всех отладочных окон в проекте

{% content-ref url="../sistema-vzaimodeistvii/okno-otladki-sistemy-vzaimodeistvii.md" %}
[okno-otladki-sistemy-vzaimodeistvii.md](../sistema-vzaimodeistvii/okno-otladki-sistemy-vzaimodeistvii.md)
{% endcontent-ref %}

{% content-ref url="../sistema-inventarya/okno-otladki-inventarya.md" %}
[okno-otladki-inventarya.md](../sistema-inventarya/okno-otladki-inventarya.md)
{% endcontent-ref %}

{% content-ref url="../sistema-oruzhiya/okno-otladki-oruzhiya.md" %}
[okno-otladki-oruzhiya.md](../sistema-oruzhiya/okno-otladki-oruzhiya.md)
{% endcontent-ref %}

{% content-ref url="../sistema-vozmozhnostei-ability/okno-otladki-ability-system.md" %}
[okno-otladki-ability-system.md](../sistema-vozmozhnostei-ability/okno-otladki-ability-system.md)
{% endcontent-ref %}

{% content-ref url="../sistema-hud/okno-otladki-hud.md" %}
[okno-otladki-hud.md](../sistema-hud/okno-otladki-hud.md)
{% endcontent-ref %}

### Техническая справка

Основной код системы находится в `Core/Debug.` Главный виджет работает автоматически, собирая все доступные компоненты у игрока, которые реализуют `DebugActorComponentInterface`. На каждый компонент создается DebugOption widget, который позволяет включать/выключать debug у того или иного компонента; Так же посылает EventOverlayEnabled через `DebugUIInterface` во все Child виджеты, при включении/выключении дебаг меню. \
\
Это позволяет легко его расширить. Просто добавьте реализацию`DebugActorComponentInterface` в нужный компонент, создайте внутри него bDebug, и собственный дебаг виджет, события из которого будут влиять на работу компонента. В основной функции передайте созданный виджет в Output, и он появится в основном меню.\
Если вам нужен дополнительный функционал (в основном показывание/скрывание кнопок при выключении оверлея, реализуйте в этом виджете `DebugUIInterface).`

### Пример использования

В новом Actor Component в Class Settings реализуйте вышеупомянутый интерфейс.&#x20;

<figure><img src="../../../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

В появившейся функции переключите текущее значение bDebug на противоположное.

<figure><img src="../../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

Добавьте обработку виджета

<figure><img src="../../../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

Добавьте компонент в нужный класс (Pawn, PlayerController или PlayerState).\
Готово!\


<figure><img src="../../../.gitbook/assets/image (93).png" alt=""><figcaption></figcaption></figure>
