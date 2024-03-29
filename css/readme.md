## [Файловая структура](template)
1. Base — Стили основных всех и элементов сайта — body, input, button, ul, ol и т.п.
    * аналог или подключить Normalize.css
    * атомарные стили
2. Common - стили и файлы на "скорую руку".
3. Layout — стили макета. Также здесь находятся стили глобальных элементов шапки, футера, сайдбара и т.п.
    * (п2) «!important» использование не допустимо
4. libs - стили библиотек (опционально)
5. Mixins - миксины и функции
6. Modules — стили модулей, то есть блоков, которые могут использоваться многократно на разных проектах или одной странице.
    * В модулях активно применяем согласованный БЭМ (об этом ниже).
    * Формы и элементы формы
    * Модальные окна и хлебные крошки.
7. config.scss - Глобальный конфиг для стилей, включить/выключить лишние стили.
8. fonts.scss - шрифты, в том числе "внешние".
9. variables.scss

* (п2) В файлах компонента добавлять шаблоны
* (п2) Придерживаться последовательности правил: (display, position, margin, padding, block-color, content-color, other, animation, transform)

### БЭМ
* (п1) Соглашение по именованию [**Классический**](https://ru.bem.info/methodology/naming-convention):
    1. (п1) Имена записываются латиницей в нижнем регистре.
    2. (п1) Слова в именах блока и элементов разделяем дефис "-". 
    3. (п1) блок__элемент используем __
    4. (п1) блок/элемент_модификатор используем _
    5. (п1) модификатор_значение используем _
* (п3) Для блока и элемента желательно придумывать название в одно слово
* (п1) Для модификатора давать четко "говорящее" название.
* (п3) Для значения модификатора использовать сокращение. Допустимо опустить.
* (п3) Классы, которые не имеют правил, можно опустить. [Исключаем правило БЭМ](https://ru.bem.info/methodology/css/#%D1%81%D0%B5%D0%BB%D0%B5%D0%BA%D1%82%D0%BE%D1%80%D1%8B-%D0%BA%D0%BB%D0%B0%D1%81%D1%81%D0%BE%D0%B2)
* (п1) Применяем правило: [не существует элементов элементов](https://ru.bem.info/methodology/faq/#%D0%9F%D0%BE%D1%87%D0%B5%D0%BC%D1%83-%D0%BD%D0%B5-%D1%81%D1%82%D0%BE%D0%B8%D1%82-%D1%81%D0%BE%D0%B7%D0%B4%D0%B0%D0%B2%D0%B0%D1%82%D1%8C-%D1%8D%D0%BB%D0%B5%D0%BC%D0%B5%D0%BD%D1%82%D1%8B-%D1%8D%D0%BB%D0%B5%D0%BC%D0%B5%D0%BD%D1%82%D0%BE%D0%B2-block__elem1__elem2)
```scss
.block {
  &__element {
    &__sub-element {
      /* не верно */
    }
  }
}
```
* (п1) Применяем: "БЭМ не рекомендует совмещать теги и классы в селекторе"

### Сокращения:
b - border
bg - background
c - color
d - display
f - font
t - text
