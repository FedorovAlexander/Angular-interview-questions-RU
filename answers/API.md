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
<br/>
<br/>
<br/>

<hr/>

Источник: [https://blog.thoughtram.io/angular/2017/02/21/using-zones-in-angular-for-better-performance.html](https://blog.thoughtram.io/angular/2017/02/21/using-zones-in-angular-for-better-performance.html)
