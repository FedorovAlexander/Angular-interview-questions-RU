## <a name="custom-type"></a>Как объявить кастомный тип?

```typescript
type Programmer = {
	name: string;
	knownFor: string[];
};
```

<br/>

## <a name="interface-class"></a>В чем разница между интерфейсом и классом?

**Интерфейс** - это группа связанных свойств и методов, которые описывают объект, но не обеспечивают их реализацию или инициализацию.

**Класс** - это шаблон для создания объектов и инкапсулирует функциональность, которую должен иметь объект. Класс определяет состояние и поведение, которыми обладает объект.

<br/>

## <a name="discriminated"></a>Что такое Discriminated union?

Discriminated union - это шаблон, который указывает компилятору все возможные типы, которые может представлять вновь созданный тип.

```typescript
type HouseCoffee = {
	kind: "house";
	ouncesDrip: number;
};

type Latte = {
	kind: "latte";
	ouncesEspresso: number;
	milkToEspresso: 4;
};

type Cappuccino = {
	kind: "cappuccino";
	ouncesEspresso: number;
	milkToEspresso: 2;
};

type Coffee = HouseCoffee | Latte | Cappuccino;
```

Тип `Coffee` - пример discriminated union.

<br/>
<br/>
<br/>
<br/>

<hr/>

Источники:<br/>

1. [https://metanit.com/web/typescript/3.1.php](https://metanit.com/web/typescript/3.1.php)
2. [https://www.typescriptlang.org/docs/handbook/2/classes.html](https://www.typescriptlang.org/docs/handbook/2/classes.html)
3. [https://www.fullstory.com/blog/discriminated-unions-and-exhaustiveness-checking-in-typescript](https://www.fullstory.com/blog/discriminated-unions-and-exhaustiveness-checking-in-typescript)
