## <a name="what-is"></a>Что такое структурная директива?

Структурные директивы в Angular отвечают за манипулирование элементами, их изменение и удаление внутри шаблона компонента. Структурная директива применяется к основному элементу, который изменяется и обновляется вместе со своими дочерними элементами сообразно с поведением структурной директивы. В Angular имеется несколько встроенных структурных директив, таких как `ngFor`, `ngSwitch` и `ngIf`.

<br/>

## <a name="html"></a>Как идентифицировать структурную директиву в шаблоне?

Структурные директивы начинаются с `*`, например `*ngFor`, `*ngSwitch` и `*ngIf`.

<br/>

## <a name="directives-on-same-element"></a>Можно ли использовать ngFor и ngIf на одном и том же элементе?

Не рекомендуется использовать директивы `ngFor` и `ngIf` на одном и том же элементе.

Директива `ngFor` используется для итерации по коллекции элементов и создания HTML-кода для каждого из них, в то время как директива `ngIf` используется для условного отображения элемента на основе логического выражения.

При использовании этих двух директив вместе на одном элементе, это может вызвать непредсказуемое поведение и ошибки. Например, если `ngIf` удаляет элемент из DOM, `ngFor` не сможет итерироваться по нему.

Вместо этого рекомендуется использовать элемент-обертку `ng-container` и применять директивы `ngFor` и `ngIf` к отдельным дочерним элементам внутри `ng-container`. Например:

```typescript
<ng-container *ngFor="let item of items">

  <div *ngIf="item.isVisible">
    <!-- Контент для видимых элементов здесь -->
  </div>
</ng-container>
```

В этом примере `ngFor` применяется к элементу ng-container, а `ngIf` - к элементу `div` внутри него. Таким образом, директива ngIf не будет влиять на итерацию `ngFor`.
