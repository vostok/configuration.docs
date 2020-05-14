# Value nodes

[Value nodes](https://github.com/vostok/configuration.abstractions/blob/master/Vostok.Configuration.Abstractions/SettingsTree/ValueNode.cs) are key-value pairs with optional keys. They cannot have child nodes and thus are always the leaves of settings node trees. Standalone values are rare: most of the time value nodes can be found inside [objects](object-nodes.md) or [arrays](array-nodes.md). 

Value nodes are typically mapped to primitive types during [binding](../binding-nodes-to-models.md).

### Properties

| Property | Description |
| :--- | :--- |
| `Name` | Required if nested in an [object node](object-nodes.md), optional otherwise. |
| `Value` | Useful payload. The value of a object field or array element. Can be null. |
| `Children` | Always returns an empty sequence. |
| `this[name]` | Always returns `null`. |

### Equality

Two value nodes are considered equal if their values match exactly and their names match up to differences in case.

### Representation

```text
Value("name", "value") --> "value"
Value("name", null) --> <null>
```

### Related pages

{% page-ref page="./" %}

{% page-ref page="../settings-nodes-merging.md" %}



