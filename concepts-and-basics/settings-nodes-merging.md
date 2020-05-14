# Settings nodes merging

Merge is the operation of reducing two [settings nodes](settings-nodes/) to one: `left + right --> result`.

Its primary use is to [combine configuration sources](../basic-scenarios/combine-sources.md).

### API

Each node type implements a `Merge` method that accept another node \(`right` in our terms\) and an instance of settings merge options with following properties:

| Property | Values | Description |
| :--- | :--- | :--- |
| `ObjectMergeStyle` | `Deep`, `Shallow` | Type of the merge procedure performed on two [object nodes](settings-nodes/object-nodes.md). `Deep` is the default style. |
| `ArrayMergeStyle` | `Replace`, `Concat`, `Union`, `PerElement` | Type of the merge procedure performed on two [array nodes](settings-nodes/array-nodes.md). `Replace` is the default style. |

[SettingsNodeMerger](https://github.com/vostok/configuration.abstractions/blob/master/Vostok.Configuration.Abstractions/SettingsTree/SettingsNodeMerger.cs) is a handy public helper used to merge arbitrary nodes:

```text
var result = SettingsNodeMerger.Merge(left, right, SettingsMergeOptions.Default);
```

### General merging rules

* If both nodes are `null`, the result is also `null`.
* If one of the nodes is `null`, the non-null node wins:
  * `left + null --> left`
  * `null + right --> right`
* If nodes are of different types, the right node always wins:
  * `value + array --> array`
  * `array + object --> object`
  * `object + value --> value`
* If nodes are of same type, special rules apply. They are described in the next sections.

### Merging two [value nodes](settings-nodes/value-nodes.md)

Right node always wins: `left value + right value --> right value`.

### Merging two [array nodes](settings-nodes/array-nodes.md)

**Replace** style \(default\) ****always preserves the right array:

`left array + right array --> right array`.

**Concat** style ****produces an array containing elements from both arrays. All elements from the left array, then all elements from the second one, preserving order inside arrays.

`[1, 2] + [3, 4] --> [1, 2, 3, 4]`

**Union** style ****produces an array containing unique items from both arrays. The order is the same to **Concat** style.

`[1, 2, 3] + [2, 3, 4] --> [1, 2, 3, 4]`

**Per element** style ****produces an array containing items obtained by merging corresponding items \(by index\) from both arrays. If merged arrays have different children count, the "tail" of the longer array is preserved as-is.

`[1, 2, 6] + [4, 5] --> [4, 5, 6]`

### Merging two [object nodes](settings-nodes/object-nodes.md)

**Deep** style \(default\) produces an object with union of the children from both nodes, then merges children with same names recursively.

`{A:1} + {B:2} --> {A:1, B:2}`

`{A: {C:1}, B: {D:2}} + {A: {E:3}, B: {F:4}} --> {A: {C:1, E:3}, B: {D:2, F:4}}`

**Shallow** style compares children of both nodes by names. If the sets of names match, regardless of order, merges the pairs of matching children recursively. Elsewise, just prefers to return the right node.

`{A:1} + {B:2} --> {B:2}`

`{A:1} + {A:2} --> {A:2}`

### Related pages

{% page-ref page="settings-nodes/" %}

{% page-ref page="../basic-scenarios/combine-sources.md" %}

