## <a name="when-to-use"></a>Когда нужно использовать стандартные (template driven), а когда реактивные (reactive) формы?

Template driven формы можно использовать в тех случаях, когда нужно сделать небольшую форму или если приложение переходит с AngularJS на Angular (`ngModel` работает так же как `ng-model` в AngularJS). Во всех остальных случаях лучше использовать реактивные формы.<br/>
Преимущества реактивных форм: <br/>

- Лучше масштабируются
- Разделение бизнес и презентационной логики
- Повышается читабельность кода
- Проще поддерживать
- Проще применять кастомную валидацию

<br/>

## <a name="submit"></a>Как отправить форму?

Нужно использовать `ngSubmit` чтобы слушать событие отправки формы. При сабмите формы будет вызываться соответствующий метод.

```typescript
<form [formGroup]="checkoutForm" (ngSubmit)="onSubmit()"></form>
```

<br/>

## <a name="difference"></a>В чем разница между NgForm, FormGroup, и FormControl?

Директива `NgForm` создает новую сущность `FormGroup` и байндит ее к элементу `<form>` шаблона, собирает все значения полей формы и следит за их изменениями и валидацией. При импорте `Forms Module` директива применяется по умолчанию ко всем тегам `<form>`. Применяется на уровне шаблона.
<br/>
<br/>
`FormGroup` собирает значения каждой дочерней `FormControl` в один объект, где ключами будут имена контроллеров полей формы.
<br/>
<br/>
`FormControl` следит за значением и валидацией одного конкретного контроллера формы.

<br/>

## <a name="form-builder"></a>В чем преимущество использования FormBuilder?

`FormBuilder` упрощает создание новых сущностей `FormControl`, `FormGroup` или `FormArray`. Сокращает количество кода, необходимого для создания сложных форм.

<br/>
<br/>
<br/>
<br/>

<hr/>

Источники:<br/>

1. [https://blog.angular-university.io/introduction-to-angular-2-forms-template-driven-vs-model-driven/](https://blog.angular-university.io/introduction-to-angular-2-forms-template-driven-vs-model-driven/)
2. [https://angular.io/start/start-forms](https://angular.io/start/start-forms)
3. [https://angular.io/api/forms/FormControl](https://angular.io/api/forms/FormControl)
4. [https://angular.io/api/forms/FormBuilder](https://angular.io/api/forms/FormBuilder)
