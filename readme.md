Регламент v.0.1.1
===

## Общие

Для чего это надо (если не очень очевидно):

1) Как в любой сфере нужны стандарты
2) Что бы по кругу друг за другом не переделывать, т.е. что бы ускорить разработку
3) Что бы ускорить разработку
4) Что бы с каждым днем ускорять разработку
5) Я/Мы должны делать много и быстро
6) **Что бы ускорить разработку**

* не поддерживаем Internet Explorer 
* функционал, который в требованиях не учтен, но очевидно потребуется сразу реализовывать без согласований.
* Для верстки писем используем правила google почты, или (если требований простые) вообще ничего, только html.
* **Дополнять обсуждать данные правила**

### Области ответственности:

Андрей:
* ТЗ - уточнить/обсудить **ЧТО** делать
* Дизайн/Внешний вид
`...`

Дима:
* ТЗ - уточнить/обсудить **КАК** делать
* ТЗ - уточнить/обсудить **КТО БУДЕТ** делать 
* Вся техническая часть, инструменты, библиотеки
* БД/хранение/сервера
`...`

Марина:
* ТЗ - уточнить/обсудить **КАК** делать
* ТЗ - уточнить/обсудить **КТО БУДЕТ** делать
* Верстка. JS-логика.
`...`


## Редактор

* Используйте UTF-8 везде (кроме csv для поддержки excel)
* Для отступов всегда используем два/три/четыре пробела. Не используем табуляцию.
* желательно соблюдать 120 символов в строке
* Отмечайте задачи для списка дел непонятные места или временный код с помощью **TODO**.
* **никогда** не используем транскрипцию
* Для переменных, идентификаторов, классов, функций используем настолько длинные имена, насколько нужно, но настолько короткие, насколько возможно.
* неочевидные алгоритмы сопровождать комментариями
* (для ЯП) Файлы классов и имена классов должны начинаться с заглавной буквы, в то время как любое другое имя файла (конфигурации, виды, скрипты и т.д.) должны быть в нижнем регистре.
* желательно комментировать используя BlockDoc все функции, классы, миксины..
* константы только верхнем регистре

## HTML5
***

* только !DOCTYPE html
* Всегда пишите в нижнем регистре.
* Всегда двойные кавычки "
```html
<div class="class" id="id"></div>
```

* Использовать теги семантически
  * input - элементы кнопок
    * button/checkbox/color/file/hidden/radio/range
    * date/datetime
    * email - для почты, или text
    * tel - для телефона, + pattern, и не надо никакой jq.mask
    * password - для ввода пароля при авторизации
    * text - не использовать для чисел (цен, количество), по возможности прописывать minlength maxlength
    * number - если по умолчанию 0, то при фокусировке очищать значение, по возможности прописывать min max 
  * button - кнопки для формы (по умолчанию писать type="button")
  ```html
   <button type="button"></button>
  ```
  * a - ссылки

* имена классов в camelCase используем в js, через - и _ в css
* пустыми строками разделяем только логические блоки, избегаем пустых строк просто так

#### Атрибуты:
* tabindex - проставлять только в финальной версии, если не следить будет только хуже. 
* src - опускайте название протокола (http:, https:) в ссылках на картинки или другие медиа-ресурсы, файлы стилей или скрипты, конечно, если эти файлы доступны по обоим протоколам.

### Желательно также: 
* комментариями подписывать неочевидные области секции.
* указывайте высоту, ширину и высоту для изображений
* Старайтесь соблюдать последовательность атрибутов:
1. Ключевые (без которых тег не имеет смысла) для тегов (кроме src, этот последний)
2. ID и Class
3. все остальные

* для input использовать pattern, для почты/телефона
* для input использовать required, где требуется

## CSS3/SCSS
***

* Верстку начинать с мобильной версии (особенно если сайт для пользователей, а не менеджеров)
* Библиотеки целиком подключать в исключительных случаях(к 5-6 проекту у нас должна быть своя библиотека с кучей модулей)
* Каждый новый компонент верстать с мыслями о его многократном использовании, т.е.:
   * если такая кнопка ранее не версталась: 1) Откладываем верстание целевой страницы 2) Верстаем кнопку как компонент 3) Возвращаемся к целевой странице и добавляем новый компонент
   `да, первый проект будем делать месяц а то и 2, но второй 2 недели, 5ый за пол дня`

* Методология что-то среднее между SMACSS + БЭМ + ATOMIC CSS
* разделяем стили для всех проектов:
1. Base — базовые стили. Это стили основных элементов сайта — body, input, button, ul, ol и т.п. В этой секции используются в основном селекторы тэгов и атрибутов, классы — в исключительных случаях;
   * в этих правилах заводим переменные цветов шрифтов для быстрой смены для каждого проекта
   * можно добавить Normalize.css
   * «!important» использование не допустимо
2. Layout — стили макета. Здесь глобально Также здесь находятся стили глобальных элементов шапки, футера, сайдбара и т.п.
   * в стилях макета прописываем сетку (например вырезанную из bootstrap), позиционирование, отступы (margin/padding)
3. Modules — стили модулей, то есть блоков, которые могут использоваться многократно на разных проектах или одной странице.
   * В модулях активно применяем упрощенный БЭМ.
   * Модуль главный, потом каскадом его элементы и состояния элементов
   * стили состояния - этот раздел, в котором допустимо использование ключевого слова «!important».
4. Theme/Custom — оформление. Здесь описываются стили оформлений индивидуально для проекта.
* Атомарные стили прописать в base, layout и переносить их за собой от проекта к проекту. Допустимо использование ключевого слова «!important»
* Названия атомарных стилей должно четко давать понять что он делает
```css
.margin-left { margin-left: 10px; } /* НЕПРАВИЛЬНО, такое можно написать индивидуально в проекте */
.m-left10 { margin-left: 10px; } /* такой стиль возможно добавить в базовый (но лучше использовать относительные единицы) */
```
* Названия атомарных стилей предлагаю использовать такие же, как в bootstrap (а точнее даже оттуда их и скопировать), не придется писать документацию 
* Используйте сокращенные формы записи свойств, где возможно.
* Ставим ';' после каждого правила.


## javascript
***

* минимальная версия es2016 (это значит никакого var)
* только строгий режим "use strict"
* не использовать глобальные переменные, в объект window добавлять только свойства в виде объектов, как это делает JQuery
* не переопределять свойства встроенных объектов, кроме объекта Оbject, и в этом случае лучше создавать объект без прототипа (Object.create(null)) 
* использовать только строгое "===/!=="
* собирать собственные компоненты, коллекции, популярные функции, например формат числа. Планируется завести репозиторий.

### Руководство по стилю:
###### (возможно стоит сделать отдельную страницу)

* [базовый уровень](https://learn.javascript.ru/coding-style)
* [продвинутый - airbnb style](https://leonidlebedev.github.io/javascript-airbnb/)
* `следует определиться с паттернами`


### Желательно также:
* переменные объявлять в начале функции
* переменные объекты JQ/HtmlNodeElement должны начинаться "$";
* заботится об утечках памяти. (но это не значит что надо 1 объект/переменную на все случаи жизни)
* имена давать в camelCaseStyle
* думать о переходе на typeScript

## php
***

* минимальная версия php 7
* для битрикс: если для модуля отдельная страница делаем отдельным файлом в папке, если модуль на странице с другими - битрикс компонент.
* для wordpress/opencart все делаем через включаемую область
* использовать только строгое "===/!=="
* максимально допустимое количество использование "ECHO" - 1 раз.
* имена файла класса должно совпадать с именем самого класса.
* имена классов всегда должны начинаться с первой заглавной буквы.


### Руководство по стилю:
###### (возможно стоит сделать отдельную старницу)

* [Основной стандарт](https://world-hello.ru/php/psr/psr-1.html)
* [Руководство по стилю](https://world-hello.ru/php/psr/psr-2.html)
* имена давать в camelCaseStyle 
* файлы *.php не должны содержать закрывающий тег "?>", кроме шаблонов с html-разметкой. (phtml - устарел)
* в рабочем коде не должны использоваться, только исключения и ошибки die()/exit()

## библиотеки/фрэймворки/системы

* cms 1cBitrix/Wordpress/OpenCart/... - и прочие
* Самодельная Vistegra CMS
* Фрэйморки пока не используем - не было столь массового проекта (наверное)
* Normalize.css/Bootstrap - по желанию верстальщика
* jquery - ***НЕ ИСПОЛЬЗОВАТЬ В ФУНКЦИИ КАЛЬКУЛЯТОРА*** использовать только для взаимодействия со страницей, что бы ускорить разработку, например для select/dropdown menu...
* redBeam - работа c БД
* mpdf - формирование pdf для php 7+
* html2pdf - формирование pdf для php на Битрикс
* phpmailer - отправка писем

## Инструменты/СТЭК

* браузер Chrome как основной (желательно проверять Firefox и safari)
* trello - таск-менеджер (отчитываться что делаем, всем кроме Андрея)
* нормальный текстовый редактор/IDE - желательно что-то от jetbrains
* openserver/xampp/php-cli - желательно openserver
* html/pug/... - возможно стоит использовать препроцессор для html
* sass/scss - желательно scss
* webpack/gulp - желательно webpack
* webpack-dev-server - самый удобный liveEditor
* autosave - не лениться и не забывать использовать
* git - ветку мастер, трогаю (пока) только я (Дима)
* babel - по особым требованиям (если клиент требует поддержку старых браузеров, кроме IE)

---
###### всё обсуждаемо
###### _vistegra 2020_
