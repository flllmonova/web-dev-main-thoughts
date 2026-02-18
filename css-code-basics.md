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

> Капитель — вид строчных букв, размер которых совпадает (или приближен) к размеру заглавных букв.

```
.small-caps {
  font-variant: small-caps;
}
```

property `text-decoration`
1. `underline` — Подчёркивание текста
2. `line-through` — Перечёркивание текста
3. `overline` — Надчёркивание текста

property `font-family`

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

*font-size/line-height пишутся через слеш*
*Обязательными из них являются font-size и font-family. Остальные можно не указывать.*

#### Правильный порядок слов
font-style
font-variant
font-weight
font-size / line-height (эти два правила записываются через слэш)
font-family
