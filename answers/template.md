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
<br/>
<br/>
<br/>

<hr/>

Источники: <br/>
[https://angular.io/guide/template-reference-variables](https://angular.io/guide/template-reference-variables)
<br/>
[https://habr.com/ru/post/491136/](https://habr.com/ru/post/491136/)
<br/>
[https://codeburst.io/angular-interview-question-what-are-ng-container-ng-content-and-ng-template-9fafbbc255d5](https://codeburst.io/angular-interview-question-what-are-ng-container-ng-content-and-ng-template-9fafbbc255d5)
