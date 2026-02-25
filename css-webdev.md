#### Min-content
* Ширина / высота = минимальной ширине / высоте содержимого
```
width: min-content;
height: min-content;
```

> Content overflow - переполнение контента.
> Полосы прокрутки (scrollbars) находятся в отступах (padding box). <br>
> Свойства `outline` и `box-shadow` занимают пространство полей (margin box), не влияют на размер box model.

<hr>

### & - represent parent selector
```
/* without & */
.button {
  color: blue;
}
.button:hover {
  color: darkblue;
}

/* with & */
.button {
  color: blue;
  &:hover {
    color: darkblue;
  }
}

/* without & */
.card {
  background: white;
}
.card--highlighted {
  border: 2px solid gold;
}

/* with & */
.card {
  background: white;
  &--highlighted {
    border: 2px solid gold;
  }
}
```
> & работает только внутри вложенной структуры Sass. Нельзя использовать его вне блока селектора.

#### :is()
```
.card .title, .card .subtitle, .card .description {
  margin-bottom: 10px;
}

/* with :is() */

.card :is(.title, .subtitle, .description) {
  margin-bottom: 10px;
}

h1 a, h2 a, h3 a, h4 a, h5 a, h6 a {
  color: blue;
}

/* with :is() */

:is(h1, h2, h3, h4, h5, h6) a {
  color: blue;
}

article :is(header, footer) :is(h1, h2) {
  color: darkred;
}

/*
Результат: заголовки <h1> и <h2> внутри <header> или <footer> в <article> станут тёмно‑красными.
*/
```
> **Валидность списка** Если в списке есть некорректный селектор, весь список игнорируется.
> **Производительность** В большинстве случаев :is() работает быстрее, чем длинные цепочки селекторов, так как сокращает объём CSS‑кода.

CSS conditional group rules like `@container`, `@media`, `@supports`, and `@layer` can also be nested.
```
.feature {
  @media (min-width: 40em) {
    /* ... */
  }

  @container (inline-size > 900px) {
    /* ... */
  }

  @supports (display: grid) {
    /* ... */
  }

  @layer component {
      h2 {
        /* ... */
      }
    }
  }
```

<hr>

### Cascade Algorithm
1. 
> [!IMPORTANT]
> 1. `!important` на первом месте. `property: value !important`
> 2. `Инлайновые` стили будут всегда сильнее, чем стили из тега `<style>` или `style.css` вне зависимости от их специфичности.
> 3. Специфичность

### Specifity
(1, 0, 0) - id
(0, 1, 0) - class, :pseudo-class, [attribute]
(0, 0, 1) - element, ::pseudo-element

- `*` **universal selector** has no specififty, his value (0, 0, 0)
- `**:not()**`, `**:is()**` не добавляет специфичность
- `**:where()**` обнуляет специфичность (0,0,0)

<hr>

## Inheritance
1. `inherit` - заставляет элемент наследовать значение свойства от своего родителя.
> используйте для явного наследования там, где это не происходит автоматически (например, для border или margin).

2. `initial` - устанавливает начальное (стандартное) значение свойства, определённое спецификацией CSS.
> для полного сброса свойства до стандарта (полезно в компонентах).

4. `unset` - ведёт себя по‑разному в зависимости от типа свойства:
> когда нужно сбросить свойство, но не знать, наследуется ли оно.
- для наследуемых свойств → inherit;
- для ненаследуемых свойств → initial.
```
/* Для наследуемого color → inherit */
.element {
  color: unset; /* возьмёт цвет от родителя */
}

/* Для ненаследуемого margin → initial (0) */
.element {
  margin: unset; /* станет 0 */
}
```
4. `all` - универсальное свойство для управления сразу всеми CSS‑свойствами элемента.
> для массового сброса стилей (например, .reset { all: unset; }).
```
all: inherit | initial | unset | revert;

/* Универсальный сброс */
.universal-reset {
  all: unset;
}
```

5. `revert` откатывает значение свойства до уровня каскада, на котором оно было впервые задано.
>  чтобы вернуть «естественный» вид элемента (особенно для кнопок, форм).
- 1. Проверяет, есть ли это свойство в `стилях пользователя` — если да, применяет его.
- 2. Если нет — применяет `стили браузера` (по умолчанию).
- 3. Если и их нет — применяет `initial`.

6. `revert-layer`  в сложных системах с CSS‑слоями для управления темами.

<hr>

> Создает колонки, по мере доступного пространства увеличивает / уменьшает кол-во колонок
> Фиксированное число колонок `column-count: 2;`
```
.text {
    width: 100%;
    column-width: 260px;
    column-gap: 1em;
}
```

<hr>

### Logical properties
1. `inline-axis` (строчная ось) - направление текста в строке (справа налево / слева направо)
2. `block-axis` (блочная ось) - направление между блоками (сверху вниз / снизу вверх)

#### Ключевые понятия:
1. `inline-start` — начало строчной оси;
2. `inline-end` — конец строчной оси;
3. `block-start` — начало блочной оси;
4. `block-end` — конец блочной оси;

#### Основные логические свойства
1. Отступы и поля:
- `margin-inline-start`, `margin-inline-end`, `margin-block-start`, `margin-block-end`;
- `padding-inline-start`, `padding-inline-end`, `padding-block-start`, `padding-block-end`;
- shorthands: `margin-block`, `margin-inline`, `padding-block`, `padding-inline`

2. Границы:
- `border-inline-start`, `border-inline-end`, `border-block-start`, `border-block-end`
- shorthands: `border-block`, `border-inline`

3. Размеры:
- `inline-size` — ширина в горизонтальном режиме, высота в вертикальном;
- `block-size` - высота в горизонтальном режиме, ширина в вертикальном;

4. Минимум/максимум:
- `min-inline-size`, `max-inline-size`;
- `min-block-size`, `max-block-size`.

5. Радиус скругления (по часовой):
`border-start-start-radius`, `border-start-end-radius`, `border-end-end-radius`, `border-end-start-radius`

6. Viewports units


```
p {
  text-align: end; /* text-align: right; */
}
```

<hr>
