# Object source

**Location**: [main sources module](../modules/sources.md).

[**ObjectSource**](https://github.com/vostok/configuration.sources/blob/master/Vostok.Configuration.Sources/Object/ObjectSource.cs) converts an arbitrary object \(including anonymous types\) to a [settings node](../concepts-and-basics/settings-nodes/):

```text
var source = new ObjectSource(new {A = 1, B = 2, C = new[] {1, 2, 3});
```

Conversion process obeys the following priority list:

* Objects with overridden `ToString` are converted to [value nodes](../concepts-and-basics/settings-nodes/value-nodes.md);
* Dictionaries with primitive key types are converted to [object nodes](../concepts-and-basics/settings-nodes/object-nodes.md);
  * Conversion is performed recursively for keys and values;
* Objects that implement `IEnumerable` are converted to [array nodes](../concepts-and-basics/settings-nodes/array-nodes.md);
  * Conversion is performed recursively for sequence elements;
* Everything else is converted to [object nodes](../concepts-and-basics/settings-nodes/object-nodes.md);
  * Conversion is performed recursively for public instance fields and properties;

Like [constant sources](constant-source.md), object source does not produce any updates by itself; conversion exceptions are exposed via `(null, error)` notifications.

### Related pages

{% page-ref page="../concepts-and-basics/configuration-sources.md" %}

