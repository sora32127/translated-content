---
title: Функция calc()
slug: Web/CSS/calc
---

{{CSSRef}}

`calc()` - это функция CSS, которая даёт возможность рассчитать значения свойств CSS во время их определения. Она может быть использована везде, где применимы {{cssxref("&lt;length&gt;")}}, {{cssxref("&lt;frequency&gt;")}}, {{cssxref("&lt;angle&gt;")}}, {{cssxref("&lt;time&gt;")}}, {{cssxref("&lt;number&gt;")}}, или {{cssxref("&lt;integer&gt;")}}.

{{InteractiveExample("CSS Demo: calc()")}}

```css interactive-example-choice
width: calc(10px + 100px);
```

```css interactive-example-choice
width: calc(100% - 30px);
```

```css interactive-example-choice
width: calc(2em * 5);
```

```css interactive-example-choice
width: calc(var(--variable-width) + 20px);
```

```html interactive-example
<section class="default-example" id="default-example">
  <div class="transition-all" id="example-element">Change my width.</div>
</section>
```

```css interactive-example
:root {
  --variable-width: 100px;
}

#example-element {
  border: 10px solid #000;
  padding: 10px;
}
```

## Синтаксис

Функция `calc()` принимает в качестве параметра математическое выражение, результат вычисления которого можно использовать как значение CSS-свойства. Выражение может включать операторы +, -, \*, / с использованием стандартных правил приоритета операторов:

- **+**
  - : Сложение
- **-**
  - : Вычитание.
- **\***
  - : Умножение. По крайней мере хоть один из сомножителей должен быть {{cssxref("&lt;number&gt;")}}.
- **/**
  - : Деление. Делитель должен быть {{cssxref("&lt;number&gt;")}}.

Операнды в expression могут быть различными выражениями {{cssxref("&lt;length&gt;")}}. Если пожелаете, то можете использовать разные единицы измерения для каждого из операндов. Вы также можете использовать скобки, чтобы указать порядок вычисления.

### Формальный синтаксис

```
calc(expression)
```

## Примеры

### Позиционирование объекта в окне с помощью отступа

`calc()` делает простым позиционирование объекта с помощью отступа. В этом примере создаётся баннер занимающий в ширину все окно с отступами по краям в 40px.

```css
.banner {
  position: absolute;
  left: 5%; /* для браузеров не поддерживающих calc() */
  left: calc(40px);
  width: 90%; /* для браузеров не поддерживающих calc() */
  width: calc(100% - 80px);
  border: solid black 1px;
  box-shadow: 1px 2px;
  background-color: yellow;
  padding: 6px;
  text-align: center;
}
```

```html
<div class="banner">Это баннер!</div>
```

{{ EmbedLiveSample('Позиционирование_объекта_в_окне_с_помощью_отступа', '100%', '60') }}

### Автоматическое изменение размера формы ввода для соответствия размеру контейнера

В следующем случае `calc()` помогает обеспечить не выпадание полей формы за края блока, задав отступ.

Давайте посмотрим некоторый код CSS:

```css
input {
  padding: 2px;
  display: block;
  width: 98%; /* для браузеров, не поддерживающих calc() */
  width: calc(100% - 1em);
}

#formbox {
  width: 130px; /* для браузеров, не поддерживающих calc() */
  width: calc(100% / 6);
  border: 1px solid black;
  padding: 4px;
}
```

Здесь ширина формы становится 1/6 от ширины окна. Затем, чтобы задать размер полей, мы вновь используем функцию `calc()`, которая вычитает 1em из ширины блока. Теперь применим этот CSS к следующему HTML-коду:

```html
<form>
  <div id="formbox">
    <label>Type something:</label>
    <input type="text" />
  </div>
</form>
```

{{ EmbedLiveSample('Автоматическое_изменение_размера_формы_ввода_для_соответствия_размеру_контейнера', '100%', '80') }}

### Вложенный `calc()` с CSS переменными

Вы также можете использовать `calc()` с CSS переменными. Рассмотрим пример кода:

```css
.foo {
  --widthA: 100px;
  --widthB: calc(var(--widthA) / 2);
  --widthC: calc(var(--widthB) / 2);
  width: var(--widthC);
}
```

## Спецификации

{{Specifications}}

## Совместимость с браузерами

{{Compat}}

## Смотрите также

- [Firefox 4: CSS3 calc() ✩ Mozilla Hacks – the Web developer blog](https://hacks.mozilla.org/2010/06/css3-calc/)
