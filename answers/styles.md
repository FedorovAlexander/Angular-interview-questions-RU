## <a name="select-custom-element"></a>Как стилизовать кастомный компонент?

Для этого нужно использовать селектор `:host`.

```css
:host {
	display: block;
	background-color: yellow;
}
```

<br/>

## <a name="targets-host"></a>Какой псевдокласс нужно использовать, чтобы стилизовать элемент, в котором находится компонент?

`:host`

<br/>

## <a name="select-class-any-ancestor"></a>Как выбрать класс в любом родителе компонента (вплоть до корневого элемента)?

Селектор `:host-context()` ищет css класс в любом родителе компонента. `:host-context()` удобно комбинировать с другими селекторами.

```css
:host-context(.theme-light) h2 {
	background-color: #eef;
}
```

<br/>
<br/>
<br/>
<br/>

<hr/>

Источники:<br/>

1. [https://angular.io/guide/component-styles](https://angular.io/guide/component-styles)
