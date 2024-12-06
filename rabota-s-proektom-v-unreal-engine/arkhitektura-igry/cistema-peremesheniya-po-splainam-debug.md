# Cистема перемещения по сплайнам (Debug)

Основной код находится в `ProtocolTerminate/Logic/WorldObjects/BP_Teleport.`

## Основные параметры:

Teleporting?: задаёт, нужно ли перенести игрока из точки A в точку B за 1 кадр.

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfVXYUhHJjPVKy8_EuR3rADQ_p7AY-Du-wSKb9eoKBp7d2cNTK2EgbmEr-Mk02ZGtHVy7wOi8jsNC31zgXXu5v-Y7tUJQyWPbKM7rw6FlmcGG3gMyC7t9HQAO7T94tZvzzzZ1iHvA?key=pkkzpLCm04sFEhuyYCHrGf9w" alt=""><figcaption></figcaption></figure>

Time: определяет, за какое время нужно перенести игрока из точки A в точку B, если `Teleporting? = false.`

Speed: задаёт скорость перемещения игрока из точки A в точку B, если `Teleporting? = false.`

## Как использовать BP\_Teleport:

1. Разместите Actor на сцене и установите его в нужной точке.
2. Выберите конец сплайна и переместите его (Mesh и SplineMesh переместятся автоматически).

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfHvehHsXA1SMXKKUn7bJGu-bEUDz7A37nWILpC7TFqScQwtgV0wHpRKJMjudQIFqCq60U9HrKkXB7f7c35cVVK50VWebYzsTKiX3kVhFsN1pygh6CUgY7lvgdHmdSb9Y7s30mSKg?key=pkkzpLCm04sFEhuyYCHrGf9w" alt=""><figcaption></figcaption></figure>

3. Настроить параметры можно, выделив BP\_Teleport на сцене и используя вкладку Details справа.\
   Если параметры не отображаются, выделите BP\_Teleport (Self).

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXe7jjm5_z-YXXlRDaulEgXaw-gG-9_NQDYQSZksqKqkNBSU_EgkrKPWuBO-ltXJMTgbCM-uHW67zNl21FNT54JH9PtGNVkJ0YZ_tcJrs3hZ7dL8Y4MDo1rmVrvKxb7TxALRvLPk?key=pkkzpLCm04sFEhuyYCHrGf9w" alt=""><figcaption></figcaption></figure>

\
