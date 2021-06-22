## <a name="tools-to-improve"></a>Что можно сделать, чтобы улучшить производительность приложения?

1. Изменить `ChangeDetectionStrategy` на `OnPush`.
2. Отключение Change Detection.
3. Обнаружение локальных изменений.
4. Запуск вне Angular.
5. Использование чистых пайпов.
6. Использование опции `trackBy` для директивы `*ngFor`.
7. Использование Web Worker.
8. Lazy Load.
9. Предварительная загрузка.

<br/>

## <a name="on-push"></a>Что такое ChangeDetectionStrategy.onPush?

Когда компонент получает данные из своего родителя, Angular анализирует дерево компонентов и проверяет входные данные на наличие любых отличий от его предыдущего значения этих данных.

`ChangeDetectionStrategy.onPush` отключает такую проверку change detection (CD) на компоненте и его дочерних элементах. При первом запуске приложения Angular запускает CD на компоненте с onPush и отключает слежение. В последующих запусках CD этот компонент и все его дочерние компоненты будут пропущены. Далее CD на этом компоненте будет запущено только в случае, если входные данные были изменены.

<br/>

## <a name="detach"></a>Что такое отключение Change Detection?

У каждого компонента в Angular есть детектор изменений. Мы можем инжектировать этот детектор изменений (`ChangeDetectorRef`) чтобы отключить или включить change detection на этом компоненте (и его дочерних компонентах).

У класса `ChangeDetectorRef` есть методы:

- `markForCheck()`: помечает родительские компоненты как нуждающиеся в проверке (и ререндеринге).
- `detach()`: отключает change detection на этом компоненте и его дочерних компонентах.
- `detectChanges()`: немедленно запустит change detection на этом компоненте и его дочерних компонентах
- `checkNoChanges()`: проверяет change detection и его дочерние элементы и выдает их при обнаружении любых изменений. Используется в режиме разработки, чтобы убедиться, что запущенное обнаружение изменений не вносит других изменений.
- `reattach()`: снова подключает к change detection ранее отключенные компоненты.

<br/>

## <a name="local"></a>Что такое обнаружение локальных изменений (Local Change Detection)?

Отключив компонент от change detection (CD) мы можем запускать CD локально, по поддереву этого компонента.
Например, мы можем создать метод `clickHandler()`, который будет изменять данные (data) и запускать локальное CD.

```typescript
clickHandler() {
	data++;
	changeDetectorRef.detectChanges();
}
```

При этом DOM будет обновлен, а глобального запуска CD от root компонента не произойдет. Это даст огромную производительность, особенно если данные обновляются каждую секунду.

<br/>

## <a name="ngzone"></a>Что такое запуск вне Angular?

Angular использует NgZone/Zone чтобы следить за асинхронными событиями, чтобы знать когда запускать change detection. Весь код приложения на Angular выполняется в зоне Angular, которая создается Zone.js. Zone.js слушает асинхронные события и сообщает их Angular.

У Angular есть особенность, которая позволяет выполнять часть кода вне зоны Angular. В этом случае change detection не будет запущено и UI не будет обновлен.

Это может быть полезно если у нас есть код, который меняет UI каждую секунду. Мы можем вывести обновление UI из зоны Angular, подождать пока нам снова нужно будет обновить UI и ввести обновление UI в зону.

```typescript
@Component({
	...
	template: `
		<div>
			{{data}}
			{{done}}
		</div>
	`
})
class TestComponent {
	data = 0
	done

	constructor(private ngZone: NgZone) {}

	processInsideZone() {
		if(data >= 100) {
			done = "Done"
		}
		else {
			data += 1
		}
	}

	processOutsideZone() {
		this.ngZone.runOutsideAngular(()=> {
			if(data >= 100) {
				this.ngZone.run(()=> {data = "Done"})
			}
			else {
				data += 1
			}
		})
	}
}
```

processInsideZone выполняется в зоне Angular и UI обновляется по ходу выполнения.

processOutsideZone выполняется вне ngZone и UI не будет обновляться. Когда data станет больше 100 и мы хотим показать "Done", мы возвращаемся в ngZone и показываем "Done".

<br/>

## <a name="track-by"></a>Как работает trackBy для директивы \*ngFor?

Мы можем сократить количество запросов к серверу, отслеживая изменения на каждом элементе списка. Используя свойство `trackBy` для `*ngFor` Angular, вместо перерисовки всего списка, будет изменять и перерисовывать только те элементы, которые были изменены.

В компоненте:

```typescript
trackByItems(index: number, item: Item): number {
	return item.id;
}
```

В шаблоне:

```html
<div *ngFor="let item of items; trackBy: trackByItems">
	({{item.id}}) {{item.name}}
</div>
```

<br/>

## <a name="web-worker"></a>Что такое Web Worker-ы?

Web Worker позволяет выполнять скрипта отдельным процессом в фоновом режиме. Web Worker-ы могут создавать другие Web Worker-ы и так далее. Общение между главным процессом и Web Worker-ами осуществляется с помощью сообщений.

<br/>

## <a name="lazy-load"></a>Что такое Lazy Loading в Angular?

По умолчанию все NgModule в тот момент, когда загружается приложение вне зависимости от того, нужны сейчас этим модули или нет. Для больших приложений необходимо использовать lazy loading чтобы модули загружались по мере необходимости. Lazy loading помогает уменьшить размер бандла, что уменьшит время загрузки приложения.

```typescript
const routes: Routes = [
	{
		path: "items",
		loadChildren: () =>
			import("./items/items.module").then((m) => m.ItemsModule),
	},
];
```

<br/>

## <a name="lazy-load"></a>Что такое Lazy Loading в Angular?

<br/>
<br/>
<br/>
<br/>

<hr/>

Источники:<br/>

1. [https://dev-gang.ru/article/10-hitrostei-dlja-optimizacii-vashego-angular-prilozhenija-8fk5qyino3/](https://dev-gang.ru/article/10-hitrostei-dlja-optimizacii-vashego-angular-prilozhenija-8fk5qyino3/)
2. [https://angdev.ru/doc/web-workers/](https://angdev.ru/doc/web-workers/)
