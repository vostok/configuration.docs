# Freeze sources

**Requires**: [sources module](../modules/sources.md).

This operation allows to effectively disable data updates on a source:

```text
var source = new JsonFileSource("settings.json");

var frozenSource = source.Freeze();

// frozenSource will not issue updates after first successful one
```

### Related pages

{% page-ref page="../concepts-and-basics/configuration-sources.md" %}



