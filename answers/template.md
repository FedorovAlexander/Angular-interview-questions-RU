## <a name="add-class"></a> Как при клике добавить класс "active" выбранному элементу списка?

В шаблоне:

```html
<ul id="list" class="list">
	<li
		class="list-item"
		[ngClass]="{item.selectedItem ? 'active' : null}"
		(click)="listClick(item)"
		*ngFor="let item of groups"
	>
		{{ item.name }}
	</li>
</ul>
```

В component.ts:

```typescript
listClick(item) {
  item.selectedItem = !item.selectedItem; // если при повторном клике мы хотим убрать класс 'active'
}
```

<br/>

## <a name="template-var"></a> Что такое template variable? Как ее использовать?

Template variables помогают использовать данные из одной части шаблона в другой части шаблона.

```html
<input #phone placeholder="номер телефона" />

<!-- другие элементы -->

<button (click)="callPhone(phone.value)">Позвонить</button>
```

Angular присваивает значение template variable в зависимости от того, где мы ее объявляем:

- Если мы объявляем переменную на компоненте, то переменная ссылается на экземпляр компонента.
- Если мы объявляем переменную на стандартном HTML тэге, то переменная ссылается на этот элемент.
- Если мы объявляем переменную на `<ng-template>`, то переменная ссылается на экземпляр TemplateRef этого элемента.
- Если мы определяем переменную через выражение (`#var="ngModel"`), то переменная ссылается на директиву или компонент с соответствующим именем `exportAs`.

<br/>

## <a name="mult-async"></a> Что случится если подписаться на поток данных несколько раз через async pipe?

Каждое использование пайпа `async` создает новую подписку на observable$. Избежать этого можно с помощью RxJs оператора `share()` или

```typescript
*ngIf=”{key: observable$ | async} as data”
```

на родительском элементе в шаблоне.

<br/>
<br/>
<br/>
<br/>

<hr/>

Источники: <br/>
[https://angular.io/guide/template-reference-variables](https://angular.io/guide/template-reference-variables)
