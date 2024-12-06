# Наглядные примеры реализации Gameplay Message Router

## Blueprint

1. Для отправки сообщения мы должны сперва обратиться к GameplayMessageSubsystem

<figure><img src="../../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

2. Вызываем метод Broadcast Message

<figure><img src="../../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

3. Выбираем канал, по которому будет отправлено сообщение (Gameplay Tag)

<figure><img src="../../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

4. В качестве Message указываем Make (StructName)

<figure><img src="../../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

Теперь нам надо получить сообщение. Для этого

1.  Вызываем функцию Listen For Gameplay Messages. Она создает асинхронную задачу, которая ожидает сообщения по конкретному каналу.

    <figure><img src="../../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

    <figure><img src="../../../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>


2. Указываем канал и Payload Type - тип данных, который мы ожидаем получить по данному каналу.
3. При запуске игры мы увидим сообщение.

<figure><img src="../../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

##

