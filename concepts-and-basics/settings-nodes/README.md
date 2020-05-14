# Settings nodes

Settings nodes are the intermediate representation of configuration data and one of the core concepts of the library. Their main purpose is to abstract away various configuration formats \(JSON, XML, etc.\) so that [binding to model classes](../binding-nodes-to-models.md) can be implemented once without regard to the nature of [configuration sources](../configuration-sources.md) being used.

### Key points

* A settings node is a tree with string keys and string values in its leaf nodes.
* [Configuration sources](../configuration-sources.md) produce settings nodes as their primary artifacts.
* [Binding](../binding-nodes-to-models.md) is the process of converting a settings node to an arbitrary .NET object.
* Settings nodes are implemented in the [abstractions module](../../modules/abstractions.md).
* Settings nodes are immutable objects.

### Why is it necessary to learn about settings nodes?

Despite being a somewhat internal API used directly only in a handful of advanced scenarios, settings nodes are crucial for a solid understanding of how configuration data [translates](../binding-nodes-to-models.md) to objects in C\# code via different node types and [scoping](../settings-nodes-scoping.md).

### When is there a need to use settings nodes directly?

* Implementation of a [custom configuration source](../../advanced-scenarios/create-custom-sources.md);
* Implementation of a [custom model binder](../../advanced-scenarios/apply-custom-binders.md);
* [Transformation](../../advanced-scenarios/transform-sources.md) of configuration sources

### Node types

There are three types of nodes:

* [Value nodes](value-nodes.md), used to hold data;
* [Array nodes](array-nodes.md), used to represent sequences;
* [Object nodes](object-nodes.md), used to represent objects with named properties.

Users are not expected to implement custom node types.

`Null` node instances represent absence of settings \(e.g. a configuration file that does not exist\).

### Node interface

All node types implement the [ISettingsNode](https://github.com/vostok/configuration.abstractions/blob/master/Vostok.Configuration.Abstractions/SettingsTree/ISettingsNode.cs) interface and have following properties:

| Property | Type | Description |
| :--- | :--- | :--- |
| `Name` | `string` | Node name. Case-insensitive. |
| `Value` | `string` | Node value. Only present in [value nodes](value-nodes.md). |
| `Children` | `IEnumerable<ISettingsNode>` | Sequence of child nodes in containers: [arrays](array-nodes.md) and [objects](object-nodes.md).  |
| `this[name]` | `ISettingsNode` | Name-based indexer used to navigate [objects](object-nodes.md) \(see [scoping](../settings-nodes-scoping.md)\). |

All nodes also implement a [merge](../settings-nodes-merging.md) operation.

### Representation

All node types implement a JSON-like `ToString()` method. Its result may look like this for a sample [object node](object-nodes.md) with two nested [value nodes](value-nodes.md):

```text
{
   "A": "1",
   "B": "2"
}
```

This representation is extensively used on the rest of the pages. 

### Related pages

{% page-ref page="value-nodes.md" %}

{% page-ref page="array-nodes.md" %}

{% page-ref page="object-nodes.md" %}

{% page-ref page="../settings-nodes-merging.md" %}

{% page-ref page="../settings-nodes-scoping.md" %}

{% page-ref page="../configuration-sources.md" %}

{% page-ref page="../binding-nodes-to-models.md" %}



