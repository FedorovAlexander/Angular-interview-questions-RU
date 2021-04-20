## <a name="transition"></a> Как определить переход между двумя состояниями в Angular?

Во время перехода между состояниями можно создавать простые анимации. Анимации определяются в @Component() и состоят из множества сменяющих друг друга состояний конкретного элемента. Переходы определяются в функции state().

```typescript
@Component({
  selector: 'example-panel',
  templateUrl: './example-panel.component.html',
  animations: [
    trigger('expandedPanel', [
      state('initial', style({ height: 0 })),
      state('expanded', style({ height: '*' })),
      transition('initial <=> expanded', animate('0.3s')),
    ]),
  ],
})
```

<br/>

## <a name="wildcard"></a>Что такое состояние wildcard?

Звездочка `*` или wildcard соответствует любому состоянию. Используется для того, чтобы определить анимацию, которая применяется независимо от начального или конечного состояния HTML-элемента. <br/>
Пример:<br/>
Анимирование всех состояний:<br/>

```typescript
transition("* => *", animate("0.3s"));
```

Если анимация должна срабатывать при переходе с initial на любое другое состояние, то это указывается так:

```typescript
transition("initial => *", animate("0.3s"));
```

## <a name="trigger"></a>Что такое триггер анимации?

Описания состояний объединяются в триггер, который и является полноценной Angular анимацией.
<br/>
<br/>
<br/>
<br/>

<hr/>

Источник: [https://angdev.ru/doc/angular-animation-part-1/](https://angdev.ru/doc/angular-animation-part-1/)
