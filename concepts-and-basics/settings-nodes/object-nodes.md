# Object nodes

[Object nodes](https://github.com/vostok/configuration.abstractions/blob/master/Vostok.Configuration.Abstractions/SettingsTree/ObjectNode.cs) are containers used to represent objects with named fields/properties. Each object node contains a map of child nodes with their names as keys. There is no limit to nesting: objects can contain other objects and arrays. Elements of an object are required to have non-null names.

Object nodes are typically mapped to arbitrary classes and structs during [binding](../binding-nodes-to-models.md).

### Properties

| roperty | Description |
| :--- | :--- |
| `Name` | Required if nested in an [object node](object-nodes.md), optional otherwise. |
| `Value` | Always returns `null`. Only [value nodes](value-nodes.md) can have values. |
| `Children` | Returns an unordered sequence of child nodes. |
| `ChildrenCount` | Returns the number of elements in the `Children` sequence. |
| `this[name]` | Returns a child node with given name or `null` if such a node does not exist. |

### Equality

Two object nodes are considered equal if their `Children` sequences are equivalent \(contain equal elements but may present different order\) and their names match up to differences in case.

### Representation

```text
Object(Value("A", "1"), Value("B", "2")) --> { "A": "1", "B": "2" }
```

### Related pages

{% page-ref page="./" %}

{% page-ref page="../settings-nodes-scoping.md" %}

{% page-ref page="../settings-nodes-merging.md" %}

