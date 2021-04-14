## <a name="transition"></a> Что такое переход между двумя состояниями в Angular?

Это процесс изменения состояния (state). Во время этого перехода мы можем создавать простые анимации между двумя состояниями. Анимации определяются прямо в @Component() и состоят из множества сменяющих друг друга состояний конкретного элемента. Переходы определяются в функции state().

```
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

## <a name="wildcard"></a>Что такое состояние wildcard?

Звезочка `*` или wildcard соответствует любому сосотоянию. Ипользуется для того, чтобы определить анимацию, которая применятеся независимо от начального или конечного состония HTML-элемента. <br/>
Пример:<br/>
Анимирование всех состояний:<br/>

```
transition('* => *', animate('0.3s'))
```

Если анимация должна срабатывать при переходе с initial на любое другое состояние, то это указывается так:

```
transition('initial => *', animate('0.3s'))
```

## <a name="trigger"></a>Что такое триггер анимации?

Описания состояний объединяются в триггер, который и является полноценной Angular animation.
<br/>
<br/>
<br/>
<br/>

<hr/>

Источник: [https://angdev.ru/doc/angular-animation-part-1/](https://angdev.ru/doc/angular-animation-part-1/)
