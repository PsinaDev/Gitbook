# Inventory Anim Notify

`InvalidateInventoryItemAnimNotify`

<figure><img src="../../../.gitbook/assets/image (99).png" alt=""><figcaption></figcaption></figure>

Для корректного удаления объекта (инвалидации) во время проигрывания анимаций, во все Unequip анимации и прочие моменты, где предполагается исчезновение предмета без удаления его из инвентаря, необходимо добавить `InvalidateInventoryItemAnimNotify.`
