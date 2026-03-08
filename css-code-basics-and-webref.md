# CSS

1. `inline style` - инлайновые стили, стили в атрибуте

```
<p style="font-size: 10px;">
  Text example
</p>  
```

2. в теге `<style>`

```
<style>
  div {
    font-size: 10px;
  }
</style>
```

<hr>

> Капитель — вид строчных букв, размер которых совпадает (или приближен) к размеру заглавных букв.

```
.small-caps {
  font-variant: small-caps;
}
```

<hr>

### Property `text-decoration`
1. `underline` — Подчёркивание текста
2. `line-through` — Перечёркивание текста
3. `overline` — Надчёркивание текста

<hr>

### Property `font-family`

```
.new-font {
    font-family: Arial, Futura, sans-serif;
  }
```

### Семейства шрифтов
1. `serif` — шрифты с засечками (антиквы) (Times New Roman).
2. `sans-serif` — шрифты без засечек (гротеск) (Arial и Verdana).
3. `cursive` — курсивные шрифты
4. `fantasy` — декоративные шрифты
5. `monospace` — моноширинные шрифты. Шрифты у которых все символы имеют одинаковую ширину.


```
.text {
  font: italic bold 24px Arial;
}
```

> [!IMPORTANT]
> Обязательными из них являются **font-size** и **font-family**.
> Остальные можно не указывать.

#### Правильный порядок слов в свойстве `font`
1. `font-style`
2. `font-variant`
3. `font-weight`
4. `font-size / line-height` (эти два правила записываются через слеш)
5. `font-family`

<hr>

<img height="300" alt="Box model" src="https://github.com/user-attachments/assets/3e9406a4-32f9-4f73-ab34-6306b217c09c" />

### Box model
Размер элемента складывается из 4 слоев:
1. width + height = content
2. padding
3. border
4. margin (не влияет на физический размер)

> По умолчанию браузер высчитывает размер элемента, складывая все слои за исключением margin
> content(width x height) + padding + border,
> что определяется свойством **`box-sizing: content-box;`**

> [!IMPORTANT]
> Чтобы размер элемента не выходил за пределы width x height,
> меняем поведение **`box-sizing: border-box;`**

```
.box-sizing {
  box-sizing: content-box; /* размер элемента: content + padding + border */
  box-sizing: border-box; /* размер элемента: content */ 
}
```

<hr>

### Свойство ` border `

```
.border {
  border: 1px solid #000; /* ширина стиль цвет рамки */
  border-radius: 10px; /* скругление рамки */
}
```
#### Стили границ рамки ` border-style `
1. ` dotted ` - - -
2. ` dashed ` ...
3. ` solid `  ___
4. ` double ` ===
5. ` groove `
6. ` ridge `
7. ` inset `
8. ` outset `
9. ` none `

<hr>

### Flex
> Это некая ось, на которую «насаживаются» элементы.
> Поворачивать главную ось можно посредством свойства `flex-direction`.

#### Значения свойства `flex-direction`
1. `row (по умолчанию);` начало справо, start-правая сторона
2. `row-reverse;` начало слева, start-левая сторона
3. `column;` начало сверху, start-верх
4. `column-reverse;` начало снизу, start-снизу

<img width="400" alt="Flex-direction" src="https://github.com/user-attachments/assets/7e7a2684-f9c1-4af6-a6fa-d946753428b7" />

#### Перенос flex элементов главной оси при переполнении
1. `wrap` - перенос элементов;
2. `wrap-reverse` - перенос элементов в обратном порядке;
3. `nowrap` - перенос отключен;

#### Shorthand flex-direction & flex-wrap
```
.container {
  display: flex;
  flex-flow: column wrap;
}
```

#### Выравнивание элементов внутри контейнера
1. `justify-content` - относительно главной оси
2. `align-items` - относительно побочной оси

#### Значения `justify-content`
1. `flex-start` - начало оси;
2. `flex-end` - конец оси;
3. `center` - центер оси;
4. `space-between` - первый и последний элементы прижимаются к началу и концу оси, Оставшееся пространство равномерно распределяется между элементами. Промежутки между элементами равны.
5. `space-around` - элементы равномерно распределяются с одинаковым пространством вокруг каждого. Пространство до первого и после последнего элемента равно половине расстояния между соседними элементами.
6. `space-evenly` - расстояния между элементами и от краёв контейнера до элементов одинаковы.

#### Значения `align-content` (в рамках линий второстепенной оси)
1. `flex-start`
2. `flex-end`
3. `center`
4. `space-between`
5. `space-around`
6. `space-evenly`
7. `stretch`

> [!IMPORTANT]
> Shorthand для justify-content & align-content `place-content`
```
.container {
  place-content: space-between;
  /* sets both to space-between */
}
```

#### Значения `align-items` (в рамках одной второстепенной линии)
1. `stretch` - растягивает по всей оси (по умолчанию)
2. `flex-start` - начало оси;
3. `flex-end` - конец оси;
4. `center` - центр оси;
5. `baseline` - по базовой линии текста;
6. `first-baseline` - по первой строке текста;
7. `last-baseline` - по последней строке текста;

#### Значения `align-self`
1.`stretch`
2. `flex-start`
3. `flex-end`
4. `center`

#### Flex-grow & Flex-shrink
1. По умолчанию `flex-grow: 0` т.е. элемент не растёт
2. По умолчанию `flex-shrink: 1` т.е. элемент сжимается
```
.nav {
  display: flex;
}

.nav-menu {
  flex-grow: 1; /* меню занимает всё доступное пространство */
}

.nav-button {
  flex-shrink: 0; /* кнопка не сжимается */
  width: 100px;
}
```

#### Shorthand flex-grow & flex-short & flex-basis
```
.item1 {
  flex: 1 1 auto;
}
```

<hr>

### Относительные единицы измерения
1. em, размер относительно размера шрифта родительского контейнера
2. rem, размер относительно размера шрифта корневого элемента

<hr>

### Цветовая модель RGB
> HEX делит цвет на три блока по два символа (#rrggbb).
> Каждый блок описывает интенсивность красного, зелёного или синего в диапазоне от 00 до ff.

**Задать цвет**
1. цвет: `rgb(255, 0, 255);`
2. цвет и прозрачность: `rgba(0, 0, 0, 0.5);`

### Названия цветов
CSS предлагает [145 названий цветов](https://webref.ru/html/value/colorname)

### Цвет через HSL
**HSL** расшифровывается как:
- H — Hue (оттенок);
- S — Saturation (насыщенность);
- L — Lightness (яркость).

**Hue** (оттенок)
Это значение цвета на цветовом круге, задаётся в градусах 
* 0 ∘ - соответствует красному цвету;
* 120 ∘ — зелёному;
* 240 ∘ — синему;
> Диапазон значений: от 0 до 359 (поскольку 0 ∘ и 360 ∘ означают один и тот же красный цвет).

**Saturation** (насыщенность) 
> Определяет интенсивность цвета, степень его удалённости от серого той же яркости. Измеряется в процентах:
* 0% — полностью ненасыщенный цвет (оттенки серого);
* 100% — максимально насыщенный, «чистый» цвет.

**Lightness** (яркость)
> Характеризует, насколько цвет светлый или тёмный. Также измеряется в процентах:
* 0% — абсолютно чёрный;
* 50% — «нормальная» яркость базового цвета;
* 100% — чисто белый.

```
.element {
  color: hsl(120, 50%, 40%);
}

body {
  color: hsla(4, 68%, 56%, 0.5);
}
```

<hr>

#### Медиазапросы

```
@media (условие) {
  /* Правила */
}
```

*Думайте об этом, как о новом CSS файле, со своими селекторами, свойствами.*


```
@media (orientation: portrait/landscape) {
  .text {
    color: #ffffff;
  }
}
```

*если ширина viewport меньше или равно 700 пикселей. Тогда указывается правило max-width: 700px*
```
@media (max-width: 700px) {
  .text {
    color: black;
  }
}
```

1. *Mobile first*
при увеличении ширины экрана включаются правила с @media (min-width).
```
.container {
  width: 100%;
}
@media (min-width: 768px) {
  .container {
    width: 80%;
  }
}
```

2. *Desktop first*
при уменьшении ширины экрана включаются правила с @media (max-width)

```
.container {
  width: 80%;
}
@media (max-width: 768px) {
  .container {
    width: 100%;
  }
}
```

<hr>

#### Animations
1. задать анимацию через `@keyframes`
2. применить анимацию к элементу через селектор
> Для этого используется правило animation с тремя основными значениями
- Название анимации
- Длительность анимации. Указывается в секундах (1s, 2s, 3s и так далее)
- Бесконечная анимация или нет (если бесконечная, то указывается параметр infinite)

```
@keyframes color-change {
  0% {
    color: blue;
  }

  50% {
    color: red;
  }

  100% {
    color: blue;
  }
}

.animation-text {
  animation: color-change 3s infinite;
}

<p class="animation-text">
  Text with color-change animation. The color of the text changes from blue to red and back again
</p>
```

<hr>

#### Переменные
Синтаксис 
1. объявить `--имя-переменной: значение;`
2. использовать `свойство: var(--имф-переменной);`

```
:root {
  --main-color: #000000;
}

.news-block {
  background-color: var(--main-color);
}

.left-sidebar {
  background-color: var(--main-color);
}
```

<hr>

#### Позиционирование
> **Позиционирование** — возможность влиять на место отображения элемента на странице.
**Position**
1. **`relative`** - изменить текущего расположение элемента без выдергивая из разметки
2. **`absolutely`** - «Вынимает» блок из HTML вёрстки и изменяет его расположение относительно левого верхнего угла страницы (или родительского элемента, если у него есть свойство position в значении fixed, absolute, relative, или sticky). Место, где располагался absolute блок, будет удалено, и другие блоки смогут занять это место.
3. **`fixed`** - данное правило извлечёт блок из HTML вёрстки и расположит его в левом верхнем углу, блок будет «следовать за страницей» и всегда находится в зоне видимости пользователя.
4. **sticky** - элемент остается на месте, при прокручивании прилипает к экрану.

> Для управления расположением используются 4 правила CSS: top, right, left и bottom;
> значением которых являются координаты, где будет расположен блок.

```
<style>
  .absolute-position {
    position: absolute;
    top: 100px;
    left: 100px;
  }
</style>

<div class="absolute-position">Блок с абсолютным позиционированием, который будет расположен на расстоянии 100 пикселей от верха и 100 пикселей от левого края страницы</div>
```

<hr>

### Селекторы
1. Селектор по типу ` tag ` (type selector)
```
p {
  color: red;
}
```

2. Селектор по id ` #id ` (ID selector)
- комбинирование с селектором типа
```
#cool,
ul#cool {
  color: red;
}
```

3. Селектор всех потомков `A B` (descendant selector)
- любого уровня вложенности
```
p strong,
#fancy span {
  color: red;
}
```

4. Селектор класса ` .class ` (class selector)
- комбинирование с селектором типа
```
.red,
p.red {  
  color: eed;
}
```

5. Несколько селекторов ` A, B ` (grouping selector, comma combinator)
```
h1, p {
  color: red;
}
```

6. Выбрать все * дочерние элементы родительского элемента (universal selector)
```
p * {
  color: red;
}
```

7. Селектор братского элемента после определенного братского `A + B` (adjacent sibling selector)
> Будет выбран каждый элемент B, который сразу следует за братским элементом А (один элемент)
```
div + a {
  color: red;
}
```

8. Селектор всех братcких элементов после определенного братского `A ~ B` (general sibling selector)
> Будут выбраны все братские элементы типа B, которые сразу следуют за братским элементом A (может быть несколько элементов)
```
div ~ p {
  color: red;
}
```
> Будет выбрано 4 <p> по селектору `div ~ p`: `<div>` `<p>` `<p>` `<p>` `<blockquote>` `<p>`

9. Селектор дочернего элемента `A > B`
прямые потомки (1 уровень)
```
plate > apple {
  color: red;
}
```

10. `:first-child` (селектор первого потомка)
Эквивалент `:nth-child(1)`
```
.container p:first-child {
  color: red;
}

<div class="container">
  <p>Первый параграф (будет красным)</p>
  <p>Второй параграф</p>
  <span>Строчный элемент</span>
</div>
```
- Универсальный селектор для первого потомка
```
<section>
  <h1>Заголовок</h1>
  <p>Параграф</p>
  <div>Блок</div>
</section>

section > *:first-child {
  font-weight: bold;
}
```


11. Псевдокласс ` :only-child `
`:only-child` — это псевдокласс, который выбирает элемент, только если он является единственным дочерним элементом своего родителя.

```
<div class="container">
  <p>Единственный параграф</p>
</div>

p:only-child {
  color: green;
  font-size: 20px;
}
```

12. ` :last-child `
Выбирает последнего прямого потомка
*если потомок всего один он считатеся первым / последним / единственным*

13. ` nth-child(A) `
Выбирает прямого потомка исходя из его номера положения, а не типа
```
<section class="outer-section">
  <h2>Heading</h2>
  <p>text 1</p>
  <p>станет красным</p>
  <p>text 3</p>
</section>

p:nth-child(3) {
  color: red;
}
```

14. ` :nth-last-child(A) `
- то же самое как и №13 только отсчёт идет с конца

15. ` :first-of-type `
- учитывается тип и номер элемента
```
<section>
  <h2>Heading</h2>
  <p>станет красным</p> 
  <p>text 2</p>
  <p>text 3</p>
</section>

p:first-of-type {
  color: red;
}
```

16. ` :nth-of-type(A) `, ` :nth-of-type(odd) `, ` :nth-of-type(even) `
17. ` :nth-child(An + B) `
` span:nth-of-type(6n+2) ` выбирает каждый 6й элемент, начиная со 2го элемента (включительно).

18. ` :only-of-type `
Выбирает элементы тип которых единственный в родительском контейнере

19. ` :last-of-type `
Выбирает последний элемент по типу

20. ` :empty `
Выбирает пустой элемент

21. ` :not() `
Выбирате элементы кроме тех, что прописаны в :not()

22. селектор по атрибуту ` [attribute] `
- можно комбинировать ` a[href] `

23. селектор по значению атрибута [attribute='value']
> [!IMPORTANT]
> 2 оператора **`s`** (case-**sensetive**) и **`i`** (case-**insensetive**)
> их можно добавить в селектор таким образом: [attr='value' s] / [attr='value' i]

25. селектор по значению атрибута `начало с` ` [attribute^='value'] `
(Attribute Starts With Selector)
- например ` .toy[category^='swim' i] `

25. селектор по значению атрибута `заканчивается на` ` [attribute$='value'] `
(Attribute Ends With Selector)
- например ` img[src$='.jpg'] `

26. селектор по значению атрибута в котором есть определенная последовательность символов [attribute*="value"]
- например ` img[src*='/thumbnails/'] ` выберет все фотки из папки thumbnails

```
/* A href that contains "example.com" */
[href*='example.com'] {
  color: red;
}

/* A href that starts with https */
[href^='https'] {
  color: green;
}

/* A href that ends with .com */
[href$='.com'] {
  color: blue;
}
```

<hr>

### Нормалайзер CSS
> Нет такого понятия, как элемент HTML без стилей.
> Каждая веб-страница использует по крайней мере один CSS: **стиль клиентского приложения**.
Чтобы у браузеров был исходный одинаковый стиль,
используется сброс CSS, файл [normalize.css](https://piccalil.li/blog/a-more-modern-css-reset/)
```
<head>
  <link rel="stylesheet" href="normalize.css">
  <link rel="stylesheet" href="styles.css">
</head>
```

Для установки всем элементам border box model
```
*,
*::before,
*::after {
  box-sizing: border-box;
}
```
