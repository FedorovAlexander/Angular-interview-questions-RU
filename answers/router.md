## <a name="for-root-for-child"></a>В чем разница между RouterModule.forRoot() и RouterModule.forChild()?

Когда мы импортируем сервис в lazy loaded модуль, то Angular создает новый экземпляр этого сервиса.
<br/>
RouterModule объявляет и экспортирует директивы (`router-outlet`, `routerLink`, `routerLinkActive` и т.д.) и сервисы (`Router`, `ActivatedRoute` и т.д.). Для того, чтобы избежать дублирования экземпляров сервиса у `RouterModule` есть два метода: `forRoot` and `forChild`.
<br/>
Из названий методов ясно, что метод `forRoot` должен быть вызван только в корневом модуле (app.module), а `forChild` должен вызываться в других (feature) модулях. Таким образом все директивы, компоненты и пайпы всё также будут экспортироваться из модуля, но новый экземпляр сервиса не будет создан.

<br/>

## <a name="loadChildren"></a>Как работает loadChildren?

Для ленивой загрузки модуля нужно использовать свойство `loadChildren` объекта Route. `loadChildren` определяет, какой модуль должен быть лениво загружен.

В примере ниже показано, что роутер лениво загрузит модуль, используя нативную браузерную систему импорта.

```typescript
[
	{
		path: "lazy",
		loadChildren: () =>
			import("./lazy-route/lazy.module").then((mod) => mod.LazyModule),
	},
];
```

<br/>

## <a name="when-to-use-routing-module"></a>Нужен ли отдельный Routing Module?

В Angular конфигурация роутов в отдельном файле считается лучшей практикой. При этом роуты можно прописать в и в App модуле.

<br/>

## <a name="when-lazy-loaded-is-loaded"></a>В какой момент загружается lazy loaded module?

При ленивой загрузке модуле загружаются по требованию в тот момент, когда пользователь перешел по ссылке на этот модуль в роутере.

<br/>
<br/>
<br/>
<br/>

<hr/>

Источники:<br/>

1. [https://blog.bitsrc.io/boost-angulars-performance-by-lazy-loading-your-modules-ca7abd1e2304](https://blog.bitsrc.io/boost-angulars-performance-by-lazy-loading-your-modules-ca7abd1e2304)
2. [https://angular.io/tutorial/toh-pt5](https://angular.io/tutorial/toh-pt5)
