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

## <a name="kind-of-data-async"></a>Какие данные могут быть использованы с async pipe?

Данные, которые приходят асинхронно из Observable или Promise.

<br/>

## <a name="how-to-create"></a>Как сделать кастомный пайп?

Допустим, нам надо выводить число, в котором разделителем между целой и дробной частью является запятая, а не точка. Для этого мы можем написать небольшой пайп.

Создать пайп можно с помощью Angular CLI команды `ng generate pipe format` (format - имя пайпа).

Будет создан файл format.pipe.ts

**format.pipe.ts**

```typescript
import { Pipe, PipeTransform } from "@angular/core";

@Pipe({
	name: "format",
})
export class FormatPipe implements PipeTransform {
	transform(value: number, args?: any): string {
		return value.toString().replace(".", ",");
	}
}
```

К кастомному пайпу должен применяться декоратор Pipe. Этот декоратор определяет метаданные, в частности, название pipe, по которому он будет использоваться:

```typescript
@Pipe({
	name: 'format'
})
```

Применим FormatPipe в коде компонента:

```typescript
import { Component } from "@angular/core";

@Component({
	selector: "my-app",
	template: `<div>
		Число до форматирования: {{ x }}<br />Число после форматирования:
		{{ x | format }}
	</div>`,
})
export class AppComponent {
	x: number = 15.45;
}
```

Но чтобы задействовать FormatPipe, его надо добавить в главном модуле приложения AppModule:

```typescript
import { NgModule } from "@angular/core";
import { BrowserModule } from "@angular/platform-browser";
import { AppComponent } from "./app.component";
import { FormatPipe } from "./format.pipe";

@NgModule({
	imports: [BrowserModule],
	declarations: [AppComponent, FormatPipe],
	bootstrap: [AppComponent],
})
export class AppModule {}
```

Полученный результат:

Число до форматирования: 15.45 <br/>
Число после форматирования: 15,45

<br/>

## <a name="how-pipe-prevent-leeks"></a>Как async pipe предотвращает утечку памяти?

В момент уничтожения компонента (NgOnDestroy) async пайп автоматически отписывается от Observable или Promise на которые подписан.

<br/>

## <a name="pure-impure"></a>В чем разница между чистыми и нечистыми пайпами?

**Чистые (pure) пайпы:**

- Входные параметры определяют выходные. Если входные параметры не поменялись, то выходные тоже не поменяются.
- Легко переиспользовать, так как результат предсказуем.
- Чистые пайпы это чистые функции и их легко тестировать.

**Нечистые (impure) пайпы:**

- Входные параметры не определяют выходные.
- Не могут быть переиспользованы.

<br/>
<br/>
<br/>
<br/>

<hr/>

Источники:<br/>

1. [https://metanit.com/web/angular2/8.1.php](https://metanit.com/web/angular2/8.1.php)
2. [https://angular.io/api/common/AsyncPipe](https://angular.io/api/common/AsyncPipe)
3. [https://metanit.com/web/angular2/8.2.php](https://metanit.com/web/angular2/8.2.php)
