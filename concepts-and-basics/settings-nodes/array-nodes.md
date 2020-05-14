# Array nodes

[Array nodes](https://github.com/vostok/configuration.abstractions/blob/master/Vostok.Configuration.Abstractions/SettingsTree/ArrayNode.cs) are containers used to represent sequences, such as JSON arrays. Each array node contains an ordered list of child nodes. There is no limit to nesting: arrays can contain other arrays and objects. Elements of an array are not required to have names.

Array nodes are typically mapped to ordered collections during [binding](../binding-nodes-to-models.md).

### Properties

| roperty | Description |
| :--- | :--- |
| `Name` | Required if nested in an [object node](object-nodes.md), optional otherwise. |
| `Value` | Always returns `null`. Only [value nodes](value-nodes.md) can have values. |
| `Children` | Returns an ordered sequence of child nodes. |
| `ChildrenCount` | Returns the number of elements in the `Children` sequence. |
| `this[name]` | Always returns `null`. Arrays cannot be navigated with [scoping](../settings-nodes-scoping.md). |

### Equality

Two array nodes are considered equal if their `Children` sequences are equal elementwise and their names match up to differences in case.

### Representation

```text
Array(Value("1"), Value("2)) --> ["1", "2"]
Array(Object(), Object()) --> [{}, {}]
Array(Array(Value("1")), Array(Value("2"))) --> [["1"], ["2"]]
```

### Related pages

{% page-ref page="./" %}

{% page-ref page="../settings-nodes-merging.md" %}



