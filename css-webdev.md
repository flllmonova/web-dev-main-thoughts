#### Min-content
* Ширина / высота = минимальной ширине / высоте содержимого
```
width: min-content;
height: min-content;
```

> Content overflow - переполнение контента.
> Полосы прокрутки (scrollbars) находятся в отступах (padding box). <br>
> Свойства `outline` и `box-shadow` занимают пространство полей (margin box), не влияют на размер box model.

#### & - represent parent selector
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

.card :is(.title, .subtitle, .description) {
  margin-bottom: 10px;
}

h1 a, h2 a, h3 a, h4 a, h5 a, h6 a {
  color: blue;
}

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
