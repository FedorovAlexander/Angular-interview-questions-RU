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
