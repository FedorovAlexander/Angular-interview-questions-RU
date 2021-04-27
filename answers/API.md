## <a name="renderer"></a> Почему для доступа к элементам и манипуляции с ними лучше использовать renderer методы (а не доступ через нативный JS)?

Использование renderer дает нам возможность быть уверенными,что все манипуляции с элементами будут работать в окружениях, где нет DOM (мобильные и десктопные приложения, веб воркеры).

<br/>

## <a name="size"></a>Как изменить размер элемента при изменении ширины окна?

```typescript
export class someComponent implements OnInit {
	innerWidth: number;
	isMobile: boolean;
	mobileWindowWidth: number = 768;

	ngOnInit() {
		this.innerWidth = window.innerWidth;
		this.isMobile = this.innerWidth > this.mobileWindowWidth ? false : true;
	}

	@HostListener("window:resize", ["$event"])
	onResize($event) {
		this.innerWidth = window.innerWidth;
		this.isMobile = this.innerWidth > this.mobileWindowWidth ? false : true;
	}
}
```

При изменении переменной `isMobile` можно изменять класс элемента в шаблоне или менять/добавлять css-свойство.
Также можно использовать npm-пакеты (пример: [https://www.npmjs.com/package/angular-resize-event](https://www.npmjs.com/package/angular-resize-event)).

<br/>

## <a name="ngzone-service"></a>Можете привести хороший пример использования NgZone сервиса?

Наиболее распространенное использование такого сервиса - оптимизация производительности при запуске работы, состоящей из одной или нескольких асинхронных задач, которые не требуют обновления пользовательского интерфейса или обработки ошибок для обработки с помощью Angular. Такие задачи можно запускать через `runOutsideAngular`, и при необходимости эти задачи могут повторно входить в зону Angular через `run`.

При реализации drag and drop мы должны следить за событиями `onmousedown`, `onmousemove` и `onmouseup`. При вызове `onmousedown` мы можем вывести `onmousemove` из зоны angular, чтобы это событие не вызывало change detection. А при `onmouseup` мы триггерим change detection и обновляем позицию перетаскиваемого элемента с помощью `run`.

<br/>

## <a name="component-protection"></a>Как защитить компонент от активации через роутер?

Защитить компонент от активации можно с помощью гардов CanActivate,CanActivateChild, CanDeactivate, CanLoad. Гарды можно написать по разному, но в итоге они возвращают или Observable или Promise или true/false. Гарды регистрируются в providers.

<br/>

## <a name="difference"></a>В чем разница между `@ViewChild()` и `@ContentChild()`?

`@ContentChild` и `@ViewChild` используются для доступа к первому элементу или директиве, соответствующим селектору.

`@ContentChild`:

- Запросы контента делаются перед `ngAfterContentInit` (после `ngOnInit` и `ngDoCheck`)
- Невозможно получить элементы или директивы, которые находятся в шаблонах других компонентов.
  <br/>

`@ViewChild`:

- Запросы представления делаются перед `ngAfterViewInit` (после `ngAfterContentInit` и `ngAfterContentChecked`)
- Поддерживает запросы к DOM
  - К любому классу в декораторами `@Component` или `@Directive`
  - К переменной шаблона (т.е. к `<my-component #cmp></my-component>` через `@ViewChild('cmp')`)
  - К любому провайдеру из дочернего компонента текущего компонента (т.е. `@ViewChild(SomeService) someService: SomeService`)
  - К `TemplateRef` (т.е. `@ViewChild(TemplateRef) template`)

<br/>
<br/>
<br/>
<br/>

<hr/>

Источники: <br/>
[https://blog.thoughtram.io/angular/2017/02/21/using-zones-in-angular-for-better-performance.html](https://blog.thoughtram.io/angular/2017/02/21/using-zones-in-angular-for-better-performance.html)
<br/>
[Пример гарда](https://github.com/johnpapa/angular-first-look-examples/blob/master/_examples/storyline-tracker/app/core/auth-guard.service.ts)
<br/>
[https://angular.io/api/core/ContentChild](https://angular.io/api/core/ContentChild)
<br/>
[https://angular.io/api/core/ViewChild](https://angular.io/api/core/ViewChild)
