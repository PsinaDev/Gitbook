---
description: На этой странице будут перечислены обновленные классы системы взаимодействий.
---

# Расширенные классы системы взаимодействий

## `AC_InteractorDebug`

* **Главное отличие: реализует Debug-interface**

{% content-ref url="../sistema-otladki-debug/" %}
[sistema-otladki-debug](../sistema-otladki-debug/)
{% endcontent-ref %}

## **`RoleDependentInteractable`**

В целом название говорит само за себя. Это дочерний класс AC\_Interactable, позволяющий конфигурировать косметические данные и возможность взаимодействовать специфичным ролям проекта Protocol:Terminate.&#x20;

<figure><img src="../../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

* Role Specific Display Data - переопределяет виузальное отображение для конкретной роли
* Roles That Can Interact - роли, которые могут взаимодействовать с объектом.&#x20;

## `ContextDependentInteractable`

Это расширение позволяет менять полностью контекст взаимодействий для конкретного игрока или вообще для всех!

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption><p>У игрока слева стоит контекст "Confused", в то время как у игрока справа стоит "Default". Изменения в методе взаимодействия происходят локально, но результат взаимодействий происходит у всех!</p></figcaption></figure>

Во вкладке Interaction Settings есть параметр "Context Override". Он представляет из себя Map GameplayTag/DataTableRowHandle.  Таким образом это позволяет полностью поменять контекст всех взаимодействий.\


<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

### Как это работает:

Используя плагин [GameplayMessageRouter](https://github.com/imnazake/gameplay-message-router/tree/master) по каналу Channel.Interaction.UpdateContext компонент `ContextDependentInteractable` ожидает Gameplay Tag, который будет являться ключом в Map ContextOverride. Когда сообщение будет получено,  данные будут обновлены.

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Обратите внимание, тег InteractionContext.Default зарезервирован в коде; В начале игры компонент кеширует на этот тег данные по умолчанию.

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

### Репликация

Поскольку по умолчанию InteractionData реплицируется через RepNotify, а подписка на канал обновлений происходит и на сервере, и на клиенте, вы можете очень гибко управлять изменениями контекста взаимодействий, отправляя их через сервер, в случае если вы хотите обновить взаимодействия всем, или только на клиенте, как это происходит в примере в начале.\


<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption><p>Отправка сообщения по каналу Channel.Interaction.UpdateContext</p></figcaption></figure>

#### Добавленные методы и делегаты:

<figure><img src="../../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>





