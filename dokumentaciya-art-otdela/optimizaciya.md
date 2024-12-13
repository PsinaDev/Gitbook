# Оптимизация

В некоторых статичных моделях допускается снижать количество полигонов путем удаления невидимых граней ( например ящик лежащий на полу статично) Важно! Убедитесь, что модель не будет переиспользоваться, или если и будет, то данная грань будет всегда на земле. Если в силуэтных габаритах модели присутствуют ребра, после удаления которых форма модели не изменяется, их можно смело удалять. Что касается средней и мелкой детализации, то стоит придерживаться правила, чем меньше размер детали, относительно модели, тем меньшее количество треугольников требуется, для его создания.

### **Использование LOD-ов** <a href="#null" id="null"></a>

Все модели в игре используют Nanite систему, динамически уменьшающую количество полигонов в зависимости от расстояния до модели. Тем не менее, это не исключает того факта, что LOD-ы иногда необходимо создавать вручную.&#x20;

Существуют различные группы уровней детализации созданные для каждой модели. Каждая из них имеет разный счетчик polygon и относится к группе, где группа LOD0 - это полностью детализированные модели, а LOD1, LOD2 一 имеют более низкий уровень детализации, и так далее.&#x20;

![](https://lh7-us.googleusercontent.com/eOfQgnctxCD_y-YVaE_xFHWTQJwQcfZgMvehzdvwBceebFyE8Iiw3of8C6RijX5JB9lKttDM-HBkFnn0gALaY6PkQKcPCjFVpg9trX3cZkxiRa_xfRTM2w5e7hLKz3fhZ6ITWYwJQ6bxJGwfFnsCTDbAzwE1ObsQzbxsbBwiX24isRphd7YySr9GWVV2wg)

### **Коллизии** <a href="#null" id="null"></a>

Упрощенная геометрия столкновений важна для оптимизации обнаружения столкновений в игре.Unreal Engine  предоставляет базовые инструменты для создания геометрии коллизий в редакторе Static Mesh Editor . Однако в некоторых случаях лучше всего создать сетку в 3d пакете и экспортировать в  UE. Как правило, это верно для любой сетки с открытой или вогнутой областью, с которой объекты не должны сталкиваться.

Например:

* Сетка дверного проема
* Стены с оконными проемами
* Сетки необычной формы

Сетки столкновений идентифицируются движком на основе их имени. Синтаксис именования коллизий должен быть следующим:

UBX\_\[RenderMeshName]\_## - бокс должен быть создан с использованием обычного прямоугольного 3D-объекта . Должна иметь форму призмы. деформация недопустима, иначе коллизия не будет считываться.

UCP\_\[RenderMeshName]\_## - Капсула должна быть цилиндрическим объектом , увенчанным полусферами. Ему вообще не нужно иметь много сегментов (8 — хорошее число), потому что он превращается в настоящую капсулу для столкновения. Как и боксом, деформировать капсулу недопустимо.

USP\_\[RenderMeshName]\_## - Сфере вовсе не обязательно иметь много сегментов (8 — хорошее число), потому что она преобразуется в настоящую сферу для столкновения . Как и с предыдущими коллизиями деформировать сферу недопустимо.

UCX\_\[RenderMeshName]\_## - Выпуклый объект может быть любой полностью замкнутой выпуклой 3D-формой . На приведенной ниже диаграмме показано, что является выпуклым, а что нет:

![](https://lh7-us.googleusercontent.com/Sllt_rFwFlJZu1Wzt_6JHxoOO-Oi7ZlilPW7yTdQf1B1mwQla9c089fcNc6DdIVe_8Ckh8pYNBgyRfdiPwW8Dd_miVBqh6VBordIksIuoLGQuK0I8GQQVmgjhe2EupQFdjGQkj4sAu7y8FjxGZIE1v07VpxSTS6-3SkrIzwH05lSh_TfU91JSebE1-q9Ow)

**Пример использования**

![](https://lh7-us.googleusercontent.com/0xQlLYtdUUR-wKleh6ouTTc_sYV60UN7uKXr-EPoihMEF9vBq2m9-c2UOhq5EXiUVGtjmaW7JbRE8xePbBBYUFwoknFaGR5garZLoW-Tc-TksLyNpMm_L4Opur3GyjZdYru_6zXPa3xcPVyG3GzneETiQeCgF4MkBs19HISkNRFJkmIP1a0vK1zBR5fSlQ)

### **Оптимизация текстур** <a href="#null" id="null"></a>

Для оптимизации сложности шейдера в UE мы упаковываем AO, Roughness, Metallic карты в карту ORM (Occlusion Roughness Metallic). С помощью объединения трех текстур в одну (но раскинутые по каналам RGB) мы можем уменьшить нагрузку на материал, который используется для модели. Объединить текстуры можно как в фотошопе, так и в Substance painter, выбрав пресет Unreal engine при экспорте текстур.
