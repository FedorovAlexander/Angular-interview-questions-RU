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

## <a name="activate-route-router-state"></a>В чем разница между ActivatedRoute и RouterState?

`ActivatedRoute` — сервис, предоставляемый каждому компоненту маршрута, который содержит информацию о маршруте, такую ​​как параметры маршрута, статические данные, глобальные параметры запроса и глобальный фрагмент.

`RouterState` — текущее состояние маршрутизатора, включая дерево активных маршрутов вместе с удобными методами обхода дерева маршрутов.

<br/>

## <a name="route-guards"></a>Зачем нужны гарды роутов?

Гарды позволяют ограничить навигацию по определенным маршрутам. Например если для доступа к определенному ресурсу требуется, наличие аутентификации или наличие каких-то других условий, в зависимости от которых мы можем предоставить пользователю доступ, а можем и не предоставить.

<br/>

## <a name="router-outlet"></a>Что такое RouterOutlet?

Router-outlet в Angular работает как плейсхолдер для динамической загрузки компонентов в соответствии с текущим роутом. При навигации контент компонента будет вставлен внутри `<router-outlet></router-outlet>`.

<br/>

## <a name="canActivateEtc"></a>Что такое CanActivate, CanActivateChild, CanDeactivate и CanLoad?

**CanActivate** - разрешает/запрещает доступ к маршруту;

**CanActivateChild** - разрешает/запрещает доступ к дочернему маршруту;

**CanDeactivate** - разрешает/запрещает уход с текущего маршрута;

**CanLoad** - разрешает/запрещает загрузку модуля, загружаемого асинхронно.

<br/>
<br/>
<br/>
<br/>

<hr/>

Источники:<br/>

1. [https://blog.bitsrc.io/boost-angulars-performance-by-lazy-loading-your-modules-ca7abd1e2304](https://blog.bitsrc.io/boost-angulars-performance-by-lazy-loading-your-modules-ca7abd1e2304)
2. [https://angular.io/tutorial/toh-pt5](https://angular.io/tutorial/toh-pt5)
3. [https://metanit.com/web/angular2/7.7.php](https://metanit.com/web/angular2/7.7.php)
4. [Маршрутизация в Angular](https://medium.com/fafnur/angular-docs-%D0%BD%D0%B0%D0%B2%D0%B8%D0%B3%D0%B0%D1%86%D0%B8%D1%8F-%D0%B2-%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D0%B8-%D0%BC%D0%B0%D1%80%D1%88%D1%80%D1%83%D1%82%D0%B8%D0%B7%D0%B0%D1%86%D0%B8%D1%8F-%D0%B2-%D0%BF%D1%80%D0%B5%D0%B4%D1%81%D1%82%D0%B0%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D1%8F%D1%85-c7402c16ce26)
5. [https://www.c-sharpcorner.com/blogs/routeroutlet-in-angular#:~:text=Router%2Doutlet%20in%20Angular%20works,outlet%20to%20load%20its%20content.](https://www.c-sharpcorner.com/blogs/routeroutlet-in-angular#:~:text=Router%2Doutlet%20in%20Angular%20works,outlet%20to%20load%20its%20content.)
6. [https://angdev.ru/doc/angular-routing-guards/](https://angdev.ru/doc/angular-routing-guards/)
