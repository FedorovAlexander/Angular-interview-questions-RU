## <a name="observable-promise"></a>В чем разница между observable и promise?

**Promise** обрабатывает одно значение по завершению асинхронной операции, вне зависимости от ее исхода, и не поддерживают отмену операции.
<br>
<br>
**Observable** же является потоком, и позволяет передавать как ноль, так и несколько событий, когда callback вызывается для каждого события.

<br/>

## <a name="observable-subject"></a>В чем разница между observable и subject?

В случае Observable каждая новая подписка (subscribe) получает новую копию данных.

```typescript
import { Observable } from "rxjs";

let obs = Observable.create((observer) => {
	observer.next(Math.random());
});

obs.subscribe((res) => {
	console.log("subscription a :", res); //subscription a :0.2859800202682865
});

obs.subscribe((res) => {
	console.log("subscription b :", res); //subscription b :0.694302021731573
});
```

<br/>

Когда мы используем Subject все подписчики получают одни и те же данные.

```typescript
import { Subject } from "rxjs";

let obs = new Subject();

obs.subscribe((res) => {
	console.log("subscription a :", res); // subscription a : 0.91767565496093
});

obs.subscribe((res) => {
	console.log("subscription b :", res); // subscription b : 0.91767565496093
});

obs.next(Math.random());
```

<br/>

## <a name="how-to-cache"></a>Как кэшировать данные из observable?

Для кэширования потока с состоянием можно использовать операторы `publishReplay()` и `refCount()`.

`publishReplay()` создает внутри себя буфер сообщений и первым параметром принимает размер буфера. Каждый новый подписчик сразу же получит накопленные сообщения.

`refCount()` реализует простой паттерн Ref Count, который используется для определения актуальности текущего потока. Если слушателей больше не останется, то он отпишется от потока, тем самым уничтожив его вместе с данными.

Также можно использовать `BehaviorSubject`. Этот оператор хранит текущее значение и передаст его новому подписчику.

<br/>

## <a name="order-api-calls"></a>Как с помощью rxjs реализовать несколько запросов к api, которые должны идти друг за другом?

Для реализации следующий друг за другом запросов к API нужно использовать Observable высшего порядка `concatMap`. Данный оператор ждет, пока предыдущий запрос будет выполнен, а затем делает следующий.

<br/>
<br/>
<br/>
<br/>

<hr/>

Источники:<br/>

1. [https://medium.com/ngx/practical-use-rxjs-81aaab57045c](https://medium.com/ngx/practical-use-rxjs-81aaab57045c)
2. [https://blog.angular-university.io/rxjs-higher-order-mapping/](https://blog.angular-university.io/rxjs-higher-order-mapping/)
