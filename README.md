# Вопросы с ответами на собеседовании по Angular

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
	8. <a href="answers/performance.md#lazy-load">Lazy Load.</a> <br/>
	9. <a href="answers/performance.md#preload">Предварительная загрузка.</a>
</details>

<details>
	<summary>Вопросы по пайпам</summary>
	1. <a href="answers/pipes.md#pure-pipe">Что такое пайп в Angular?</a> <br/>
	2. <a href="answers/pipes.md#async-pipe">Что такое async пайп?</a> <br/>
	3. <a href="answers/pipes.md#kind-of-data-async">Какие данные могут быть использованы с async pipe?</a> <br/>
	4. <a href="answers/pipes.md#how-to-create">Как сделать кастомный пайп?</a> <br/>
	5. <a href="answers/pipes.md#how-pipe-prevent-leeks">Как async pipe предотвращает утечку памяти?</a> <br/>
	6. <a href="answers/pipes.md#pure-impure">В чем разница между чистыми и нечистыми пайпами?</a>
</details>

<details>
	<summary>Вопросы по роутеру</summary>
	1. <a href="answers/router.md#for-root-for-child">What is the difference between RouterModule.forRoot() vs RouterModule.forChild()? Why is it important?</a> <br/>
	2. <a href="answers/router.md#loadChildren">How does loadChildren property work?</a> <br/>
	3. <a href="answers/router.md#when-to-use-routing-module">Do you need a Routing Module? Why/not?</a> <br/>
	4. <a href="answers/router.md#when-lazy-loaded-is-loaded">When does a lazy loaded module is loaded?</a> <br/>
	5. <a href="answers/router.md#activate-route-router-state">Can you explain the difference between ActivatedRoute and RouterState?</a> <br/>
	6. <a href="answers/router.md#debug">How do you debug router?</a> <br/>
	7. <a href="answers/router.md#route-guards">Why do we need route guards?</a> <br/>
	8. <a href="answers/router.md#router-outlet">What is a RouterOutlet?</a>
</details>

<details>
	<summary>Вопросы по сервисам</summary>
	1. <a href="answers/service.md#use-case">What is the use case of services?</a> <br/>
	2. <a href="answers/service.md#injected">How are the services injected to your application?</a> <br/>
	3. <a href="answers/service.md#unit-test">How do you unit test a service with a dependency?</a>
</details>

<details>
	<summary>Вопросы по структурным директивам</summary>
	1. <a href="answers/directives.md#what-is">What is a structural directive?</a> <br/>
	2. <a href="answers/directives.md#html">How do you identify a structural directive in html?</a> <br/>
	3. <a href="answers/directives.md#hide-remove">When creating your own structural directives, how would you decide on hiding or removing an element? What would be the advantages or disadvantages of choosing one method rather than the other?</a>
</details>

<details>
	<summary>Вопросы по стилям</summary>
	1. <a href="answers/styles.md#select-custom-element">How would you select a custom component to style it.</a> <br/>
	2. <a href="answers/styles.md#targets-host">What pseudo-class selector targets styles in the element that hosts the component?</a> <br/>
	3. <a href="answers/styles.md#all-child">How would you select all the child components' elements?</a> <br/>
	4. <a href="answers/styles.md#select-class-any-ancestor">How would you select a css class in any ancestor of the component host element, all the way up to the document root?</a> <br/>
	5. <a href="answers/styles.md#all-mighty-class">What selector force a style down through the child component tree into all the child component views?</a> <br/>
	6. <a href="answers/styles.md#host-context">What does :host-context() pseudo-class selector targets?</a>
</details>

<details>
	<summary>Вопросы по написанию кода (style guide)</summary>
	1. <a href="answers/style-guide.md#suggestions">What are some of the Angular Style Guide suggestions you follow on your code? Why?</a> <br/>
	2. <a href="answers/style-guide.md#importance">Is it important to have a style guide? Why/not?</a> <br/>
</details>

<details>
	<summary>Вопросы по тестам</summary>
	1. <a href="answers/tests.md#tests">What are some of the different tests types you can write?</a> <br/>
	2. <a href="answers/tests.md#mock-a-service">How do you mock a service to inject in an integration test?</a> <br/>
	3. <a href="answers/tests.md#mock-a-module">How do you mock a module in an integration test?</a> <br/>
	4. <a href="answers/tests.md#test-a-component">How do you test a component that has a dependency to an async service?</a> <br/>
	5. <a href="answers/tests.md#async-fake-async">What is the difference between 'async()' and 'fakeAsync()'?</a>
</details>

<details>
	<summary>Вопросы по TypeScript</summary>
	1. <a href="answers/typescript.md#why-type">Why do you need type definitions?</a> <br/>
	2. <a href="answers/typescript.md#custom-type">How would you define a custom type?</a> <br/>
	3. <a href="answers/typescript.md#interface-class">What is the difference between an Interface and a Class?</a> <br/>
	4. <a href="answers/typescript.md#discriminated">What are Discriminated union types?</a> <br/>
	5. <a href="answers/typescript.md#object-type">How do you define Object of Objects type in typescript?</a> <br/>
	6. <a href="answers/typescript.md#capture">How can you capture the 'type' the user provides (e.g. number), so that we can use that information later.</a>
</details>

<details>
	<summary>Вопросы по JavaScript</summary>
	1. <a href="answers/javascript.md#var-let-const">Explain the difference between var, let and const key words.</a> <br/>
	2. <a href="answers/javascript.md#garbage">Could you make sure a const value is garbage collected?</a> <br/>
	3. <a href="answers/javascript.md#object-assign">Explain Object.assign and possible use cases.</a> <br/>
	4. <a href="answers/javascript.md#object-freeze">Explain Object.freeze and possible use cases.</a> <br/>
	5. <a href="answers/javascript.md#destruct-assignment">What is destructuring assignment?</a>
</details>
