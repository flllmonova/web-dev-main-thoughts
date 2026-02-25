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
