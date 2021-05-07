## <a name="definition"></a> Какие минимальные требования к компоненту?

```typescript
import { Component } from "@angular/core";

@Component({
	templateUrl: "./minimum.component.html", // or template: ''
})
export class MinimumComponent {}
```

Нужно учесть:

- constructor не обязателен, он генерируется автоматически
- селектор не обязателен, доступ к компоненту можно получить через роутер по названию класса
- шаблон обязателен (сам шаблон or templateUrl)
