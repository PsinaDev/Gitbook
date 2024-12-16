# Система маркеров

Чтобы настроить клавишу, на которую будет ставиться маркер, нужно пройти по пути:\
`ProtocolTerminate/Core/Player/Inputs` и найти `IMC_GeneralInputs`. В этом файле необходимо найти элемент `IA_SpawnMarker`.\
В нем можно настроить не только клавишу, но и условия спавна маркера (например, нажать, зажать или отпустить клавишу).

<figure><img src="../../.gitbook/assets/image (114).png" alt=""><figcaption></figcaption></figure>

Чтобы изменить время жизни маркера на игроке, нужно открыть `BP_HumanCharacter`, зайти в **Class Defaults**, найти параметр `MarkDuration` и установить нужное значение.\


<figure><img src="../../.gitbook/assets/image (115).png" alt=""><figcaption></figcaption></figure>

Настройка времени жизни маркера робота описана в разделе: **Система возможностей (Ability) > Эффект маркера робота**.
