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
<br/>
<br/>
<br/>

<hr/>

Источники:<br/>

1. [https://fireship.io/lessons/sharing-data-between-angular-components-four-methods/](https://fireship.io/lessons/sharing-data-between-angular-components-four-methods/)
