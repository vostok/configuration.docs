# Collections

### Supported types

Arrays and lists:

* `T[]`
* `List<T>`
* `IEnumerable<T>`  \(backed by `T[]`\)
* `IReadOnlyList<T>`\(backed by `T[]`\)
* `IReadOnlyCollection<T>`\(backed by `T[]`\)
* `ICollection<T>` \(backed by `List<T>`\)
* `IList<T>`\(backed by `List<T>`\)

Dictionaries:

* `Dictionary<TKey, TValue>`
* `IDictionary<TKey, TValue>` \(backed by `Dictionary`\)
* `IReadOnlyDictionary<TKey, TValue>` \(backed by `Dictionary`\)

Sets:

* `HashSet<T>`
* `ISet<T>` \(backed by `HashSet`\)

### Binder requirements

Collections require binders defined for element types \(both keys and values in case of dictionaries\).

### Node requirements

[Array](../concepts-and-basics/settings-nodes/array-nodes.md) or [object](../concepts-and-basics/settings-nodes/object-nodes.md) node. Empty nodes are converted to empty collections.

### Null node handling

An empty collection is returned unless [explictly required](../basic-scenarios/make-settings-required.md).

Nulls are not valid as dictionary keys.

### Related pages

{% page-ref page="../concepts-and-basics/binding-nodes-to-models.md" %}

