# Settings nodes scoping

Scoping is the operation of navigating a [settings node](settings-nodes/) tree by accessing child nodes of [objects](settings-nodes/object-nodes.md) via names in a case-insensitive manner. A sequence of names resembling a path in the object structure, such as `["property1", "property2"]` is called a _scope_.

Scoping does not work on [value](settings-nodes/value-nodes.md) and [array](settings-nodes/array-nodes.md) nodes \(always results in `null`\).

Scoping is used to map object fields/properties to nodes of settings tree during [binding](binding-nodes-to-models.md). It also allows to [scope sources](../basic-scenarios/scope-sources.md) — create a source that returns a subtree of settings returned by the original source.

### Examples

* `{A: 1}` scoped to `a` is just a value `1`.
* `{A: 1}` scoped to `b` is `null`. 
* `{A: {B: [1, 2]}}` scoped to `A` is `{B: [1, 2]}`
* `{A: {B: [1, 2]}}` scoped to `[A, B]` is `[1, 2]`
* `{A: {B: [1, 2]}}` scoped to `[A, B, C]` is `null`.

### Related pages

{% page-ref page="../basic-scenarios/scope-sources.md" %}

{% page-ref page="binding-nodes-to-models.md" %}



