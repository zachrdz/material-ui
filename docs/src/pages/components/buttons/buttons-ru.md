---
title: React-компонент Кнопка
components: Button, ButtonGroup, Fab, IconButton, ButtonBase, Zoom
---

# Кнопки

<p class="description">Кнопки позволяют пользователям выполнять действия и делать выбор одним нажатием.</p>

[Кнопки](https://material.io/design/components/buttons.html) обозначают действия, которые могут выполнять пользователи. Они используются в таких местах пользовательского интерфейса, как:

- Диалоги
- Всплывающие окно
- Формы
- Карточки
- Панели инструментов

## Блочные кнопки

[Блочные кнопки](https://material.io/design/components/buttons.html#contained-button) имеют высокий акцент, отличаются использованием возвышения и заполнения. Они содержат действия, которые являются основными для вашего приложения.

Этот пример показывает, как использовать кнопку загрузки.

{{"demo": "pages/components/buttons/ContainedButtons.js"}}

## Текстовые кнопки

[Текстовые кнопки](https://material.io/design/components/buttons.html#text-button) обычно используются для менее выраженных действий, в том числе расположенных:

- В диалогах
- В карточках - Cards

В Карточках (Cards) текстовые кнопки помогают сохранить акцент на содержании карточки.

{{"demo": "pages/components/buttons/TextButtons.js"}}

## Контурные кнопки

[Контурные кнопки](https://material.io/design/components/buttons.html#outlined-button) - это кнопки со средним акцентом. Они содержат действия, которые важны, но не являются основными в приложении.

### Альтернатива

Выделенные кнопки также являются альтернативой выделенным кнопкам или могут использоваться как альтернатива текстовым кнопкам.

{{"demo": "pages/components/buttons/OutlinedButtons.js"}}

## Сгруппированные кнопки

Компонент ButtonGroup можно использовать для группировки контурных (по умолчанию) или блочных кнопок.

{{"demo": "pages/components/buttons/GroupedButtons.js"}}

## Split Button

ButtonGroup can also be used to create a split button. The dropdown can change the button action (as in this example), or be used to immediately trigger a related action.

{{"demo": "pages/components/buttons/SplitButton.js"}}

## Плавающие кнопки действий

[Плавающая кнопка действия](https://material.io/design/components/buttons-floating-action-button.html) выполняет основное или наиболее распространенное действие на экране. Они отображаются над всем содержимым экрана, обычно в виде закрашенного круга со значком в центре. FABs бывают двух типов: обычные и расширенные.

Используйте плавающую кнопку действий (FAB) только в том случае, если это наиболее подходящий способ представить основное действие экрана.

Для отображения наиболее распространенных действий рекомендуется использовать только одну кнопку с плавающим действием.

{{"demo": "pages/components/buttons/FloatingActionButtons.js"}}

По умолчанию анимация кнопки с плавающим действием на экране является расширяющейся.

Кнопка с плавающим действием, которая охватывает несколько боковых экранов (например, экраны с вкладками), должна анимироваться при переходах.

Переход масштабирование (Zoom) может быть использован для достижения этой цели. Обратите внимание, что так как выход и вход анимации запускаются одновременно, мы используем ` enterDelay `, чтобы разрешить исходящим кнопкам плавающего действия анимироваться постепенно.

{{"demo": "pages/components/buttons/FloatingActionButtonZoom.js", "bg": true}}

## Upload button

{{"demo": "pages/components/buttons/UploadButtons.js"}}

## Размеры

Fancy larger or smaller buttons? Use the `size` property.

{{"demo": "pages/components/buttons/ButtonSizes.js"}}

## Buttons with icons and label

Sometimes you might want to have icons for certain button to enhance the UX of the application as we recognize logos more easily than plain text. For example, if you have a delete button you can label it with a dustbin icon.

{{"demo": "pages/components/buttons/IconLabelButtons.js"}}

## Icon Buttons

Icon buttons are commonly found in app bars and toolbars.

Icons are also appropriate for toggle buttons that allow a single choice to be selected or deselected, such as adding or removing a star to an item.

{{"demo": "pages/components/buttons/IconButtons.js"}}

## Customized buttons

Ниже находятся примеры кастомизации компонента. You can learn more about this in the [overrides documentation page](/customization/components/).

{{"demo": "pages/components/buttons/CustomizedButtons.js", "defaultCodeOpen": false}}

👑 If you are looking for inspiration, you can check [MUI Treasury's customization examples](https://mui-treasury.com/components/button).

## Complex Buttons

The Text Buttons, Contained Buttons, Floating Action Buttons and Icon Buttons are built on top of the same component: the `ButtonBase`. You can take advantage of this lower level component to build custom interactions.

{{"demo": "pages/components/buttons/ButtonBases.js"}}

## Сторонняя библиотека маршрутизации

One common use case is to use the button to trigger navigation to a new page. The `ButtonBase` component provides a property to handle this use case: `component`. However for certain focus polyfills `ButtonBase` requires the DOM node of the provided component. This is achieved by attaching a ref to the component and expecting that the component forwards this ref to the underlying DOM node. Given that many of the interactive components rely on `ButtonBase`, you should be able to take advantage of it everywhere.

Here is an [integration example with react-router](/guides/composition/#button).

## Ограничения

### Cursor not-allowed

The ButtonBase component sets `pointer-events: none;` on disabled buttons, which prevents the appearance of a disabled cursor.

If you wish to use `not-allowed`, you have two options:

1. **CSS only**. You can remove the pointer events style on the disabled state of the `<button>` element:

  ```css
  .MuiButtonBase-root:disabled {
    cursor: not-allowed;
    pointer-events: auto;
  }
  ```

However:

- You should add `pointer-events: none;` back when you need to display [tooltips on disabled elements](/components/tooltips/#disabled-elements)
- The cursor won't change if you render something other than a button element, for instance, a link `<a>` element.

2. **DOM change**. You can wrap the button:

  ```jsx
  <span style={{ cursor: 'not-allowed' }}>
    <Button component={Link} disabled>
      disabled
    </Button>
  </span>
  ```

This has the advantage of supporting any element, for instance, a link `<a>` element.