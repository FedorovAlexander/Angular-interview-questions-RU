## <a name="use-case"></a>Зачем нужны сервисы?

Сервисы нужны для сокращения дублированного кода.
Сервисы также могут обеспечивать связь между компонентами, а также доступ к любой другой бизнес-логике.

<br/>

## <a name="injected"></a>Как сервисы внедряются в приложение?

Два способа внедрения сервиса:

- на уровне приложения
- на уровне компонента (и всех его дочерних компонентов)

Внедрение сервиса на уровне приложения создает один единственный экземпляр этого сервиса. Это удобно когда нам нужно шарить данные между различными компонентами или модулями.

Внедрение сервиса на уровне компонента, создает новый экземпляр сервиса для каждого компонента в отдельности.

Чтобы начать использовать сервис, его нужно добавить в массив `providers` модуля, а затем инжектировать его в директиву, использую `constructor`. Чтобы инжектировать сервис в другой сервис нужно использовать декоратор `@Injectable`.

```typescript
@Injectable()
export class MessageService {
	//injected service
	constructor(private errorService: ErrorService) {}
}
```

<br/>

## <a name="singleton"></a>Что такое Singleton Service?

Singleton service - это сервис у которого только одни экземпляр на всё приложение.
