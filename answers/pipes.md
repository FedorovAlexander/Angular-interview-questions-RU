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

<br/>

## <a name="async-pipe"></a>Что такое пайп async?

Пайп async подписывается на Observable или Promise и возвращает их последнее значение. Когда появляется новое значение, пайп async помечает компонент как нуждающийся в проверке. Когда компонент уничтожается, async пайп автоматически отписывается от Observable или Promise для избежания утечек памяти.

<br/>
<br/>
<br/>
<br/>

<hr/>

Источники:<br/>

1. [https://metanit.com/web/angular2/8.1.php](https://metanit.com/web/angular2/8.1.php)
