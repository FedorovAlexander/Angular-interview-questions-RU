## <a name="parent-child"></a> Как передать данные из родительского компонента в дочерний?

1. Передача данных через декоратор `@Input()`

**parent.component.ts**

```typescript
import { Component } from "@angular/core";

@Component({
	selector: "app-parent",
	template: ` <app-child [childMessage]="parentMessage"></app-child> `,
	styleUrls: ["./parent.component.css"],
})
export class ParentComponent {
	parentMessage = "message from parent";
	constructor() {}
}
```

**child.component.ts**

```typescript
import { Component, Input } from "@angular/core";

@Component({
	selector: "app-child",
	template: ` Say {{ childMessage }} `,
	styleUrls: ["./child.component.css"],
})
export class ChildComponent {
	@Input() childMessage: string;

	constructor() {}
}
```

2. Передавать данные между компонентами можно через сервис. При этом компоненты могут быть никак не связаны между собой.

<br/>

## <a name="child-parent"></a> Как передать данные из дочернего компонента в родительский?

1. Передача данных с помощью `@ViewChild`
   <br/>
   `@ViewChild` дает родительскому компоненту доступ к атрибутам и функциям дочернего компонента. Есть один недостаток: дочерний компонент не будет доступен пока view не будет инициализирован. Это значит, что для получения данных из дочернего компонента нужно реализовать `AfterViewInit`.

**parent.component.ts**

```typescript
import { Component, ViewChild, AfterViewInit } from "@angular/core";
import { ChildComponent } from "../child/child.component";

@Component({
	selector: "app-parent",
	template: `
		Message: {{ message }}
		<app-child></app-child>
	`,
	styleUrls: ["./parent.component.css"],
})
export class ParentComponent implements AfterViewInit {
	@ViewChild(ChildComponent) child;

	constructor() {}

	message: string;

	ngAfterViewInit() {
		this.message = this.child.message;
	}
}
```

**child.component.ts**

```typescript
import { Component } from "@angular/core";

@Component({
	selector: "app-child",
	template: ``,
	styleUrls: ["./child.component.css"],
})
export class ChildComponent {
	message = "Hola Mundo!";

	constructor() {}
}
```

2.  Передача данных с помощью `Output()` and `EventEmitter`
    <br/>
    В этом случае мы эмитим данные из дочернего компонента.
    Способ идеально подходит для обработки кликов, ввода в поля форм и других событий пользователя.
    <br/>
    В родительском компоненте мы создаем функцию, которая будет обрабатывать полученные из дочернего компонента данные. В шаблоне присваиваем эту функцию тому сообщению, которое эмитится из дочернего компонента (`<app-child (messageEvent)="receiveMessage($event)"></app-child>`). <br/>
    В дочернем компоненте с помощью декоратора `@Output` мы объявляем событие, которое будет эмитится. Далее создаем функцию, которая будет вызывать эмит этого события. В шаблоне создаем кнопку, при клике на которую будет вызываться функция.

**parent.component.ts**

```typescript
import { Component } from "@angular/core";

@Component({
	selector: "app-parent",
	template: `
		Message: {{ message }}
		<app-child (messageEvent)="receiveMessage($event)"></app-child>
	`,
	styleUrls: ["./parent.component.css"],
})
export class ParentComponent {
	constructor() {}

	message: string;

	receiveMessage($event) {
		this.message = $event;
	}
}
```

**child.component.ts**

```typescript
import { Component, Output, EventEmitter } from "@angular/core";

@Component({
	selector: "app-child",
	template: ` <button (click)="sendMessage()">Send Message</button> `,
	styleUrls: ["./child.component.css"],
})
export class ChildComponent {
	message: string = "Hola Mundo!";

	@Output() messageEvent = new EventEmitter<string>();

	constructor() {}

	sendMessage() {
		this.messageEvent.emit(this.message);
	}
}
```

3. Передавать данные между компонентами можно через сервис. При этом компоненты могут быть никак не связаны между собой.

<br/>

## <a name="event-emit"></a> Какие компоненты будут оповещены о том, что был emit события?

В отличие от DOM событий кастомные события в Angular не всплывают. Поэтому оповещен будет только родительский компонент. Эту проблему можно решить с помощью передачи события "дальше" в родительский компонент родительского компонента, но лучше использовать сервис.

<br/>

## <a name="cached-data"></a> Как кэшировать данные в Angular?

Способы кэширования данных в Angular:

- Сохранять данные в localStorage/sessionStorage
- Сохранять данные в переменной в сервисе
- Симулировать стейт с помощью BehaviorSubject и получать из него последнее значение
- Использовать кэширование в помощью RxJs
- Использовать хранилище NgRx

<br/>
<br/>
<br/>
<br/>

<hr/>

Источники:<br/>

1. [https://fireship.io/lessons/sharing-data-between-angular-components-four-methods/](https://fireship.io/lessons/sharing-data-between-angular-components-four-methods/)
2. [https://stackoverflow.com/questions/59972242/angular-show-cached-data-and-update-the-new-data-if-needed-data-in-background](https://stackoverflow.com/questions/59972242/angular-show-cached-data-and-update-the-new-data-if-needed-data-in-background)
