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

## <a name="ng-diff"></a> В чем различия ng-content, ng-container и ng-template?

`ng-template` - это не DOM элемент в отличии от `ng-container`. Инициализировать внутренность `ng-template` можно только руками (с помощью нужного кода), а сам `ng-template` живет в памяти до того момента, пока его не проинициализируют. Чаще всего используется с `*ngIf`.
<br/>
<br/>
`ng-container` - это DOM элемент, не имеющий селектора. Позволяет удобно группировать элементы. При рендере элементы внутри `ng-container` будут видны, а сам тег `ng-container` будет заменен на комментарий.
<br/>
<br/>
`ng-content` - используется для проекции контента. Проекция контента — это способ импортировать HTML контент извне компонента и вставить его в шаблон компонента в определенное место.

```typescript
// button.component.ts
import { Component } from "@angular/core";

@Component({
	selector: "app-button",
	template: `<button>
		<ng-content></ng-content>
	</button>`,
})
export class ButtonComponent {}

// app.component.ts
import { Component } from "@angular/core";

@Component({
	selector: "app-root",
	template: `<app-button>
		<app-icon></app-icon>
		Button
	</app-button>`,
})
export class AppComponent {}
```

<br/>

## <a name="data-bind"></a> Когда мы байндим данные в шаблоне, мы работаем с атрибутами или с свойствами (property)?

В мире Angular единственная роль атрибутов - инициализировать состояние элемента и директивы. Когда вы пишете привязку данных, вы имеете дело исключительно со свойствами и событиями целевого объекта. Атрибуты HTML фактически исчезают.

<br/>

## <a name="brackets-omit"></a> Когда можно не использовать скобки при байндинге в шаблоне?

Скобки можно не использовать, если выполняются все следующие условия:

1. Целевое свойство принимает строковое значение.
2. Строка - это фиксированное значение, которое вы можете встроить в шаблон.
3. Это значение никогда не меняется.

<br/>
<br/>
<br/>
<br/>

<hr/>

Источники: <br/>

1. [https://angular.io/guide/template-reference-variables](https://angular.io/guide/template-reference-variables)
2. [https://habr.com/ru/post/491136/](https://habr.com/ru/post/491136/)
3. [https://codeburst.io/angular-interview-question-what-are-ng-container-ng-content-and-ng-template-9fafbbc255d5](https://codeburst.io/angular-interview-question-what-are-ng-container-ng-content-and-ng-template-9fafbbc255d5)
4. [https://www.freecodecamp.org/news/data-binding-in-angular-explained/#:~:text=Angular%20will%20hardly%20ever%20bind,data%20to%20properties%2C%20not%20attributes!](https://www.freecodecamp.org/news/data-binding-in-angular-explained/#:~:text=Angular%20will%20hardly%20ever%20bind,data%20to%20properties%2C%20not%20attributes!)
