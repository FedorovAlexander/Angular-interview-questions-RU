## <a name="add-class"></a> Как при клике добавить класс "active" выбранному элементу списка?

В шаблоне:

```typescript
<ul id="list" class="list">
	<li class="list-item"
		[ngClass]="{item.selectedItem ? 'active' : null}"
		(click)="listClick(item)"
		*ngFor="let item of groups">
		{{ item.name }}
	</li>
</ul>
```

В component.ts:

```typescript
listClick(item) {
  item.selectedItem = !item.selectedItem; // если при повторном клике мы хотим убрать класс 'active'
}
```

<br/>
