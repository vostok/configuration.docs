# Combine sources

**Requires**: [main sources module](../modules/sources.md).

Multiple configuration sources can be combined into a single composite source whose data is produced by [merging](../concepts-and-basics/settings-nodes-merging.md) the [settings trees](../concepts-and-basics/settings-nodes/) provided by original sources. 

```text
var source1 = new JsonStringSource(...);
var source2 = new YamlStringSource(...);
var source3 = new XmlStringSource(...);

var combined = source1.CombineWith(source2, source3);

// combined == Merge(source1, source2, source3)

// combined.Data == Merge(Merge(source1.data, source2.data), source3.data)
```

Order of the sources is important: settings from sources that come later in the list have greater priority, hence the rightmost source should be the most specific/significant. In other words, merging is performed in a left-to-right fashion.

Updates are pushed to subscribers each time one of the component sources generates new settings.

### Related pages

{% page-ref page="../concepts-and-basics/settings-nodes-merging.md" %}

{% page-ref page="../concepts-and-basics/configuration-sources.md" %}



