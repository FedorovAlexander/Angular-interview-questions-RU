## <a name="pipe"></a>Что такое пайп в Angular?

Пайп - это декоратор, который позволяет форматировать отображаемое значение. Например, нам надо вывести определенную дату:

```typescript
import { Component } from "@angular/core";

@Component({
	selector: "my-app",
	template: `
		<div>Без форматирования: {{ myDate }}</div>
		<div>С форматированием: {{ myDate | date }}</div>
	`,
})
export class AppComponent {
	myDate = new Date(1961, 3, 12);
}
```

Мы получим результат:

Без форматирования: Wed Apr 12 1961 00:00:00 GMT +0400 (GMT +04 00)

С форматированием: Apr 12, 1961
