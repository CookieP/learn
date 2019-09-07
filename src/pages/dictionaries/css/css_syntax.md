---
title: Способы добавления стилей на страницу, базовый синтаксис. Валидация
templateKey: 'article-page'
order: 1
---

# Способы добавления стилей на страницу, базовый синтаксис. Валидация
---
## Базовый синтаксис

Основной структурной единицей в CSS является правило, которое определяет, как будет выглядеть тот или иной элемент в документе, например:

```css
H1 {
    color: blue;
    font-size: 14px;
}
```

Сначала записывается так называемый селектор, определяющий к какому html тегу (тегам) применяется то или иное свойство. Далее, непосредственно за селектором, пишется блок объявления стилей, который обязательно заключается в фигурные скобки.

Каждое объявление в свою очередь состоит из свойства и его значения. После свойства ставится двоеточие. Правило может содержать в себе несколько объявлений. В таком случае они должны быть отделены друг от друга точкой с запятой причем после последнего объявления точку с запятой можно не ставить.

Показанное выше правило указывает на то, что все заголовки первого уровня в документе будут голубого цвета с размером шрифта 14 пикселей.

## Способы добавления стилей на страницу

Для добавления стилей на веб-страницу существует несколько способов, которые различаются своими возможностями и назначением.

### Связанные стили

При использовании связанных стилей описание селекторов и их значений располагается в отдельном файле, как правило, с расширением css, а для связывания документа с этим файлом применяется тег `<link>`. Данный тег помещается в контейнер `<head>`, как показано в примере:

```html
<head>
    <link href="style.css" rel="stylesheet" type="text/css">
</head>
```

Значение href задаёт путь к CSS-файлу, он может быть задан как относительно, так и абсолютно.

### Глобальные стили

При использовании глобальных стилей свойства CSS описываются в самом документе и располагаются в заголовке веб-страницы. По своей гибкости и возможностям этот способ добавления стиля уступает предыдущему, но также позволяет хранить стили в одном месте, в данном случае прямо на той же странице с помощью контейнера `<style>`, как показано в примере:

```html
<head>
    <style type="text/css">
        h1 {
        color: blue;
    }
    </style>
</head>
```

### Внутренние стили

Внутренний или встроенный стиль является по существу расширением для одиночного тега используемого на текущей веб-странице. Для определения стиля используется атрибут `style`, а его значением выступает набор стилевых правил.

```html
<body>
    <p style="font-size: 14px; color: black">Пример текста</p>
</body>
```

Все описанные методы использования CSS могут применяться как самостоятельно, так и в сочетании друг с другом. В этом случае необходимо помнить об их иерархии. Первым имеет приоритет внутренний стиль, затем глобальный стиль и в последнюю очередь связанный стиль.

### Импорт CSS

В текущую стилевую таблицу можно импортировать содержимое CSS-файла с помощью команды `@import`. Этот метод допускается использовать совместно со связанными или глобальными стилями, но никак не с внутренними стилями. Общий синтаксис следующий:

```css
@import url("имя файла") типы носителей;
@import "имя файла" типы носителей;
```

После ключевого слова `@import` указывается путь к стилевому файлу одним из двух приведенных способов — с помощью url или без него.  Тип носителя указывается тогда, когда необходимо применить стили только для определённого устройства.

Пример:

```html
<head>
    <style type="text/css">
        @import url("style/header.css");
            h1 {
            color: blue;
        }
    </style>
</head>
```

## Валидация CSS

Валидацией называется проверка CSS-кода на соответствие спецификации CSS2.1 или CSS3. Соответственно, корректный код, не содержащий ошибок, называется валидный, а не удовлетворяющий спецификации — невалидный. Наиболее удобно делать проверку кода через сайт http://jigsaw.w3.org/css-validator, с помощью этого сервиса можно указать адрес документа, загрузить файл или проверить набранный текст.