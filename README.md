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
	3. <a href="answers/RxJs.md#angular-apis">Назовите несколько angular api, которые используют observables?</a> <br/>
	4. <a href="answers/RxJs.md#how-to-cash">Как кэшировать данные из observable?</a> <br/>
	5. <a href="answers/RxJs.md#order-api-calls">Как с помощью rxjs реализовать несколько запросов к api, которые должны идти друг за другом?</a> <br/>
	6. <a href="answers/RxJs.md#switchMap-concatMap-mergeMap">В чем разница между switchMap, concatMap и mergeMap?</a> <br/>
	7. <a href="answers/RxJs.md#scan-reduce">В чем разница между scan() и reduce()?</a>
</details>

- Вопросы по производительности
- Вопросы по пайпам
- Вопросы по роутеру
- Вопросы по сервисам
- Вопросы по структурным директивам
- Вопросы по стилям
- Вопросы по написанию кода (style guide)
- Вопросы по тестам
- Вопросы по TypeScript
- Вопросы по JavaScript
