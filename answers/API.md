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

## <a name="di"></a>Что такое Dependency Injection?

Внедрение зависимостей или Dependency Injection - это шаблон проектирования, в котором класс запрашивает зависимости из внешних источников, а не создает их.

<br/>

## <a name="constr-ngOnInit"></a>В чем разница между constructor и ngOnInit?

`Constructor` - это дефолтный метод класса, который выполняется при создании экземпляра класса и обеспечивает правильную инициализацию полей в классе и его подклассах. В Angular используется для Dependency Injection. `Constructor` - это не фича Angular. Это концепция объектно-ориентированного программирования.

`ngOnInit` - это метод жизненного цикла компонента. Вызывается один раз после установки свойств компонента, которые участвуют в привязке. Выполняет инициализацию компонента.

Основная роль `ngOnInit` - подать сигнал о том, что Angular завершил инициализацию компонента и что пользователи могут продолжить работу. `Constructor` в основном используется для инициализации членов класса, но он не может выполнить всю работу. Он полезен только в случае внедрения зависимостей и инициализации поля класса. Нужно избегать написания логики в конструкторе. `ngOnInit` - лучшее место для написания кода, который требуется во время создания экземпляра класса.

<br/>

## <a name="service-worker"></a>Что такое сервис-воркер и его роль в Angular?

Service worker - это скрипт, который запускается в браузере и управляет кэшированием приложения.

Сервис-воркеры позволяют приложениям обеспечивать удобство работы пользователей с надежностью и производительностью, сопоставимой с нативными приложениями. Добавление сервис-воркера в приложение Angular - это один из шагов по превращению приложения в прогрессивное веб-приложение (PWA).

## <a name="zonejs"></a>Что такое зона в zone.js?

Зоны предоставляют механизм перехвата планирования и вызова асинхронных операций. Логика перехватчика может выполнять дополнительный код до или после задачи и уведомлять заинтересованные стороны о событии.
<br/>
<br/>
<br/>
<br/>

## <a name="signals-intro"></a>Что такое Angular Signals и какие основные типы сигналов существуют?

Signals — это новая реактивная модель в Angular, основанная на «ячейках состояния», которые знают, кто на них подписан, и могут точечно уведомлять только тех потребителей, которые реально зависят от значения.

Основные типы:

- `signal()` — создаёт изменяемый (writable) сигнал, внутри которого хранится значение. Чтение — вызовом как функции (`counter()`), изменение — через `set`, `update` или мутацию объекта в колбэке `update`.
- `computed()` — вычисляемый сигнал, который зависит от других сигналов. Он автоматически пересчитывается, когда изменяются исходные сигналы.
- `input()` / `output()` сигналы — API для входных и выходных параметров компонента на базе сигналов, используемые вместо `@Input` / `@Output`.
- `ReadonlySignal` / `WritableSignal` — типы, обозначающие, можно ли изменять сигнал (Writable) или только читать его значение (Readonly).

<br/>

## <a name="signals-input-output"></a>Как использовать signals в компоненте вместо `@Input` / `@Output`?

Вместо декораторов `@Input` и `@Output` в новых версиях Angular используются `input()` и `output()` API, которые создают сигналы:

```typescript
import { Component, input, output } from '@angular/core';

@Component({
  selector: 'app-counter',
  standalone: true,
  template: `
    <button (click)="decrease()">-</button>
    <span>{{ value() }}</span>
    <button (click)="increase()">+</button>
  `,
})
export class CounterComponent {
  value = input.required<number>();
  valueChange = output<number>();

  increase() {
    this.valueChange.emit(this.value() + 1);
  }

  decrease() {
    this.valueChange.emit(this.value() - 1);
  }
}
```

Родительский компонент использует такой компонент так же, как и раньше, но реализация основана на signals:

```html
<app-counter [(value)]="count"></app-counter>
```

Такой подход упрощает интеграцию с сигналами внутри компонента и убирает необходимость в декораторах `@Input` / `@Output`.

<br/>

## <a name="signals-template"></a>Как сигналы используются в шаблоне и чем их чтение отличается от Observable?

Сигналы ведут себя как функции: чтобы прочитать значение, их нужно «вызвать»:

```html
<p>Текущее значение: {{ counter() }}</p>
```

Ключевые отличия от Observable:

- Для сигналов не нужен `async` пайп и не нужны подписки; Angular сам отслеживает зависимости шаблона от сигналов.
- Сигналы имеют текущее значение синхронно (как обычная переменная), а Observable — поток значений во времени.
- Change detection для сигналов может быть более точечным: пересчитываются только те вычисления и шаблоны, которые реально зависят от изменившегося сигнала.

<br/>

## <a name="signals-vs-observables"></a>В чем разница между сигналами и Observable с точки зрения change detection и производительности?

- **Сигналы**:
  - Хранят текущее значение и знают, какие вычисления и шаблоны зависят от них.
  - Обновляют только тех подписчиков, которые реально зависят от изменившегося сигнала (fine-grained reactivity).
  - Не требуют ручного управления подписками/отписками.
  - Хорошо подходят для локального и UI-состояния.

- **Observable**:
  - Моделируют поток значений во времени, часто используются для работы с асинхронностью (HTTP, события, стримы).
  - Для отображения в шаблоне обычно нужен `async` пайп или ручная подписка.
  - Не имеют встроенного знания о том, какой именно шаблон или вычисление зависит от конкретного Observable.

На практике часто используют комбинацию: RxJS/Observable — для внешних потоков и сложной асинхронной логики, Signals — для хранения уже полученных данных и обновления UI без лишних запусков change detection.

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
