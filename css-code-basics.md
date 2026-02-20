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

Property `text-decoration`
1. `underline` — Подчёркивание текста
2. `line-through` — Перечёркивание текста
3. `overline` — Надчёркивание текста

<hr>

Property `font-family`

```
.new-font {
    font-family: Arial, Futura, sans-serif;
  }
```

#### Семейства шрифтов
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

#### Box model
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

#### Свойство ` border `

```
.border {
  border: 1px solid #000; /* ширина стиль цвет рамки */
  border-radius: 10px; /* скругление рамки */
}
```
##### Стили границ рамки ` border-style `
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

## Flex
> Это некая ось, на которую «насаживаются» элементы.
> Поворачивать главную ось можно посредством свойства `flex-direction`.

#### Значения свойства `flex-direction`
1. `row (по умолчанию);`
2. `row-reverse;`
3. `column;`
4. `column-reverse;`

<img width="400" alt="Flex-direction" src="https://github.com/user-attachments/assets/7e7a2684-f9c1-4af6-a6fa-d946753428b7" />

#### Перенос flex элементов главной оси при переполнении
1. `wrap` - перенос элементов;
2. `wrap-reverse` - перенос элементов в обратном порядке;
3. `nowrap` - перенос отключен;

### Выравнивание элементов внутри контейнера
1. `justify-content` - относительно главной оси
2. `align-items` - относительно побочной оси

Значения **`justify-content`**
1. **`flex-start`** - начало оси;
2. **`flex-end`** - конец оси;
3. **`center`** - центер оси;
4. **`space-between`** - первый и последний элементы прижимаются к началу и концу оси, Оставшееся пространство равномерно распределяется между элементами. Промежутки между элементами равны.
5. **`space-around`** - элементы равномерно распределяются с одинаковым пространством вокруг каждого. Пространство до первого и после последнего элемента равно половине расстояния между соседними элементами.
6. **`space-evenly`** - расстояния между элементами и от краёв контейнера до элементов одинаковы.
