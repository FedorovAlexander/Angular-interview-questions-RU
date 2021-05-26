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
<br/>
<br/>
<br/>

<hr/>

Источники:<br/>

1. [https://blog.angular-university.io/introduction-to-angular-2-forms-template-driven-vs-model-driven/](https://blog.angular-university.io/introduction-to-angular-2-forms-template-driven-vs-model-driven/)
2. [https://angular.io/start/start-forms](https://angular.io/start/start-forms)
