### Position
1. `static`
2. `relative`
3. `absolute`
4. `fixed`
5. `sticky`
*z-index работает только для элементов, у которых position задано как relative, absolute или fixed*

### Как сдвигаются элементы
```
element {
  position: relative;
  top: 5px; /* от верха вниз на 5px */
  top: -5px; /* вверх на 5px */

  left: 5px; /* от левой стороны 5px */
  left: -5px; /* влево 5px */

  right: 5px; /* от правой стороны 5px */
  right: -5px; /* вправо 5px */

  bottom: 5px; /* от низа 5px */
  bottom: -5px; /* вниз 5px */
}
```

#### Relative position
```
/* при наведении на картинку она поднимается и увеличивается */
img {
    border: 1px solid #ce242b; /* Параметры рамки */
    position: relative; /* Относительное позиционирование */
    transition: 1s; /* Время анимации */
}

img:hover {
    z-index: 10; /* Поверх всех картинок */
    transform: scale(1.2); /* Масштабирование на 20% */
}
```

#### Анимации с `position: relative;`
```
/* при наведении кнопка закрывает свою тень */
button {
    background: #CE242B; /* Красный фон */
    color: #fff; /* Белый цвет текста */
    border: none; /* Убираем рамку */
    padding: .7rem 2rem; /* Поля вокруг текста */
    box-shadow: 5px 5px 0 #000; /* Параметры тени */
    position: relative; /* Относительное позиционирование */
    left: 0; /* Положение слева */
    top: 0; /* Положение сверху */
    transition: 1s; /* Время анимации */
}

button:hover {
    left: 5px; /* Положение слева */
    top: 5px; /* Положение сверху */
    box-shadow: 0 0 0 #000; /* Параметры тени */
}
```
### Position Fixed
- Если занулить параллельные стороны (left + right / top + bottom), то элемент будет занимать весь inlise-size / block-size
- Если занулить все стороны -> всю площадь

### Position Sticky 
Обязательно указать 1 сторону для привязки

### Box-model
#### background-clip 
свойство определяющее в каких областях элемента будут отображаться фоновая картинка и фоновый цвет.
`background-clip: border-box | padding-box | content-box | text;`
> [!IMPORTANT]
> Делать цвет `transparent` чтобы background-clip сработал

### Margin Border Padding
* Выравнивание блока по центру через значение `margin: auto;` работает только в сочетании с `width`.
* Отрицательный `margin` возможен, отрицательный `padding` и `border` - нет
