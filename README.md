# Вопросы с ответами для собеседования по Angular. Основы Angular.

## Содержание

<details>
	<summary>Вопросы по анимации</summary>
	1. <a href="answers/animations.md#transition">Как определяется переход между двумя состояниями в Angular?</a> <br/>
	2. <a href="answers/animations.md#wildcard">Что такое состояние wildcard?</a> <br/>
	3. <a href="answers/animations.md#trigger">Что такое триггер анимации?</a>
</details>
<details>
	<summary>Вопросы по архитектуре</summary>
	1. <a href="answers/architecture.md#ngrx-store">Приведите хороший пример когда нужно использовать ngrx/store?</a> <br/>
	2. <a href="answers/architecture.md#race-condition">Что такое "race condition" и какие баги могут быть связаны с этим? Как с ними справиться?</a> <br/>
	3. <a href="answers/architecture.md#smart-dumb">Разница между умным и презентационным компонентом? Приведите пример использования? Назовите преимущества?</a> <br/>
	4. <a href="answers/architecture.md#shared">Что такое Shared модуль?</a>
</details>

<details>
	<summary>Вопросы по API</summary>
	1. <a href="answers/API.md#renderer">Почему для доступа к элементам и манипуляции с ними лучше использовать renderer методы (а не доступ через нативный JS)?</a> <br/>
	2. <a href="answers/API.md#size">Как изменить размер элемента при изменении ширины окна?</a> <br/>
	3. <a href="answers/API.md#ngzone-service">Можете привести хороший пример использования NgZone сервиса?</a> <br/>
	4. <a href="answers/API.md#component-protection">Как защитить компонент от активации через роутер?</a> <br/>
	5. <a href="answers/API.md#difference">В чем разница между @ViewChild() и @ContentChild()?</a>
	6. <a href="answers/API.md#di">Что такое Dependency Injection?</a>
	7. <a href="answers/API.md#constr-ngOnInit">В чем разница между constructor и ngOnInit?</a>
	8. <a href="answers/API.md#service-worker">Что такое service-worker и его роль в Angular?</a>
</details>

<details>
	<summary>Вопросы по шаблонам (template)</summary>
	1. <a href="answers/template.md#add-class">Как при клике добавить класс "active" выбранному элементу списка?</a> <br/>
	2. <a href="answers/template.md#template-var">Что такое template variable? Как ее использовать?</a> <br/>
	3. <a href="answers/template.md#mult-async">Что случится если подписаться на поток данных несколько раз через async pipe?</a> <br/>
	4. <a href="answers/template.md#ng-diff">В чем различия ng-content, ng-container и ng-template?</a> <br/>
	5. <a href="answers/template.md#data-bind">Когда мы байндим данные в шаблоне, мы работаем с атрибутами или с свойствами (property)?</a> <br/>
	6. <a href="answers/template.md#brackets-omit">Когда можно не использовать скобки при байндинге в шаблоне?</a> <br/>
</details>

<details>
	<summary>Вопросы по компонентам</summary>
	1. <a href="answers/components.md#definition">Какие минимальные требования к компоненту?</a> <br/>
	2. <a href="answers/components.md#difference">В чем разница между компонентом и директивой?</a> <br/>
	3. <a href="answers/components.md#communication">Как происходит взаимодействие компонентов?</a> <br/>
	4. <a href="answers/components.md#two-way">Как сделать двухстороннее связывание данных?</a> <br/>
	5. <a href="answers/components.md#errors">Как бы вы сделали компонент для показа сообщений об ошибках?</a> <br/>
	6. <a href="answers/components.md#hooks">Что такое Lifecycle Hooks?</a> <br/>
</details>

<details>
	<summary>Вопросы по взаимодействию компонентов и state management</summary>
	1. <a href="answers/interactions-and-state.md#parent-child">Как передать данные из родительского компонента в дочерний?</a> <br/>
	2. <a href="answers/interactions-and-state.md#child-parent">Как передать данные из дочернего компонента в родительский?</a> <br/>
	3. <a href="answers/interactions-and-state.md#event-emit">Какие компоненты будут оповещены о том, что был emit события?</a> <br/>
	4. <a href="answers/interactions-and-state.md#cached-data">Как кэшировать данные в Angular?</a>
</details>

<details>
	<summary>Вопросы по формам</summary>
	1. <a href="answers/forms.md#when-to-use">Когда нужно использовать стандартные (template driven), а когда реактивные (reactive) формы?</a> <br/>
	2. <a href="answers/forms.md#submit">Как отправить форму?</a> <br/>
	3. <a href="answers/forms.md#difference">В чем разница между NgForm, FormGroup, и FormControl?</a> <br/>
	4. <a href="answers/forms.md#form-builder">В чем преимущество использования FormBuilder?</a> <br/>
	5. <a href="answers/forms.md#validation">Как добавить валидацию к форме, сделанной с помощью FormBuilder?</a> <br/>
	6. <a href="answers/forms.md#dirty-touched-pristine">В чем разница между состояниями dirty, touched и pristine?</a> <br/>
	7. <a href="answers/forms.md#validation-errors">Как получит доступ к ошибкам валидации, чтобы показать их в шаблоне?</a> <br/>
</details>

<details>
	<summary>Вопросы по ngModule</summary>
	1. <a href="answers/ngModule.md#what-is">Зачем нужен NgModule?</a> <br/>
	2. <a href="answers/ngModule.md#when-to-create">Когда нужно создавать новый NgModule?</a> <br/>
	3. <a href="answers/ngModule.md#for-root-for-child">В чем разница между методами forRoot() and forChild() и зачем они нужны?</a> <br/>
	4. <a href="answers/ngModule.md#provideIn">Как используется свойство providedIn?</a> <br/>
	5. <a href="answers/ngModule.md#shared-module">Что бы вы поместили в shared модуль?</a> <br/>
	6. <a href="answers/ngModule.md#not-shared-module">Что бы вы не поместили в shared модуль?</a> <br/>
	7. <a href="answers/ngModule.md#where-to-put">В какой модуль вы бы поместили сервис которые используется по всему приложению?</a> <br/>
	8. <a href="answers/ngModule.md#exports">Зачем нужны exports в NgModule?</a> <br/>
	9. <a href="answers/ngModule.md#why-is-it-bad">Почему не стоит импортировать сервис из SharedModule в lazy loaded модуль?</a>
</details>

<details>
	<summary>Вопросы по RxJs</summary>
	1. <a href="answers/RxJs.md#observable-promise">В чем разница между observable и promise?</a> <br/>
	2. <a href="answers/RxJs.md#observable-subject">В чем разница между observable и subject?</a> <br/>
	3. <a href="answers/RxJs.md#how-to-cache">Как кэшировать данные из observable?</a> <br/>
	4. <a href="answers/RxJs.md#order-api-calls">Как с помощью rxjs реализовать несколько запросов к api, которые должны идти друг за другом?</a> <br/>
	5. <a href="answers/RxJs.md#switchMap-concatMap-mergeMap">В чем разница между switchMap, concatMap и mergeMap?</a> <br/>
	6. <a href="answers/RxJs.md#scan-reduce">В чем разница между scan() и reduce()?</a> <br/>
	7. <a href="answers/RxJs.md#subject">Что такое Subject?</a> <br/>
	8. <a href="answers/RxJs.md#behavior-reply-async">В чем разница между BehaviorSubject, ReplySubject и AsyncSubject?</a> <br/>
	9. <a href="answers/RxJs.md#higher-order">Что такое Observable высшего порядка (Higher-Order)?</a> <br/>
	10. <a href="answers/RxJs.md#of-from">В чем разница между of и from?</a>
	11. <a href="answers/RxJs.md#multicasting">Что такое multicasting?</a>
</details>

<details>
	<summary>Вопросы по производительности</summary>
	1. <a href="answers/performance.md#tools-to-improve">Что можно сделать, чтобы улучшить производительность приложения?</a> <br/>
	2. <a href="answers/performance.md#on-push">Что такое ChangeDetectionStrategy.onPush?</a> <br/>
	3. <a href="answers/performance.md#detach">Что такое отключение Change Detection?</a> <br/>
	4. <a href="answers/performance.md#local">Что такое обнаружение локальных изменений (Local Change Detection)?</a> <br/>
	5. <a href="answers/performance.md#ngzone">Что такое запуск вне Angular?</a> <br/>
	6. <a href="answers/performance.md#track-by">Как работает trackBy для директивы *ngFor?</a> <br/>
	7. <a href="answers/performance.md#web-worker">Что такое Web Worker-ы?</a> <br/>
	8. <a href="answers/performance.md#lazy-load">Что такое Lazy Loading в Angular?</a> <br/>
	9. <a href="answers/performance.md#preload">Какие бывают стратегии предварительной загрузки?</a>
</details>

<details>
	<summary>Вопросы по пайпам</summary>
	1. <a href="answers/pipes.md#pipe">Что такое пайп в Angular?</a> <br/>
	2. <a href="answers/pipes.md#async-pipe">Что такое пайп async?</a> <br/>
	3. <a href="answers/pipes.md#kind-of-data-async">Какие данные могут быть использованы с async pipe?</a> <br/>
	4. <a href="answers/pipes.md#how-to-create">Как сделать кастомный пайп?</a> <br/>
	5. <a href="answers/pipes.md#how-pipe-prevent-leeks">Как async pipe предотвращает утечку памяти?</a> <br/>
	6. <a href="answers/pipes.md#pure-impure">В чем разница между чистыми и нечистыми пайпами?</a>
</details>

<details>
	<summary>Вопросы по роутеру</summary>
	1. <a href="answers/router.md#for-root-for-child">В чем разница между RouterModule.forRoot() и RouterModule.forChild()?</a> <br/>
	2. <a href="answers/router.md#loadChildren">Как работает loadChildren?</a> <br/>
	3. <a href="answers/router.md#when-to-use-routing-module">Нужен ли отдельный Routing Module?</a> <br/>
	4. <a href="answers/router.md#when-lazy-loaded-is-loaded">В какой момент загружается lazy loaded module?</a> <br/>
	5. <a href="answers/router.md#activate-route-router-state">В чем разница между ActivatedRoute и RouterState?</a> <br/>
	6. <a href="answers/router.md#route-guards">Зачем нужны гарды роутов?</a> <br/>
	7. <a href="answers/router.md#router-outlet">Что такое RouterOutlet?</a>
	8. <a href="answers/router.md#canActivateEtc">Что такое CanActivate, CanActivateChild, CanDeactivate и CanLoad?</a>
</details>

<details>
	<summary>Вопросы по сервисам</summary>
	1. <a href="answers/service.md#use-case">Зачем нужны сервисы?</a> <br/>
	2. <a href="answers/service.md#injected">Как сервисы внедряются в приложение?</a> <br/>
	3. <a href="answers/service.md#singleton">Что такое Singleton Service?</a>
</details>

<details>
	<summary>Вопросы по структурным директивам</summary>
	1. <a href="answers/directives.md#what-is">Что такое структурная директива?</a> <br/>
	2. <a href="answers/directives.md#html">Как идентифицировать структурную директиву в шаблоне?</a>
</details>

<details>
	<summary>Вопросы по стилям</summary>
	1. <a href="answers/styles.md#select-custom-element">Как стилизовать кастомный компонент?</a> <br/>
	2. <a href="answers/styles.md#targets-host">Какой псевдокласс нужно использовать, чтобы стилизовать элемент, в котором находится компонент?</a> <br/>
	3. <a href="answers/styles.md#all-child">Как выбрать все дочерние компоненты элемента?</a> <br/>
	4. <a href="answers/styles.md#select-class-any-ancestor">Как выбрать класс в любом родителе компонента (вплоть до корневого элемента)?</a> <br/>
</details>

<details>
	<summary>Вопросы по написанию кода (style guide)</summary>
	1. <a href="answers/style-guide.md#suggestions">Какие вы знаете Angular Style Guide рекомендации?</a> <br/>
	2. <a href="answers/style-guide.md#importance">Почему важно следовать style guide?</a>
</details>

<details>
	<summary>Вопросы по тестам</summary>
	1. <a href="answers/tests.md#tests">Какие бывают виды тестирования?</a> <br/>
</details>

<details>
	<summary>Вопросы по TypeScript</summary>
	1. <a href="answers/typescript.md#custom-type">Как объявить кастомный тип?</a> <br/>
	2. <a href="answers/typescript.md#interface-class">В чем разница между Interface и Class?</a> <br/>
	3. <a href="answers/typescript.md#discriminated">Что такое Discriminated union?</a> <br/> 
</details>
