# XML sources

**Location**: [Sources.Xml module](../modules/sources.xml.md).

[**XmlStringSource**](https://github.com/vostok/configuration.sources.xml/blob/master/Vostok.Configuration.Sources.Xml/XmlStringSource.cs) parses well-formed XML documents from in-memory strings and supports manual external updates:

```text
var source = new XmlStringSource("<xml content>")

source.Push("<xml content>") // update with new content
```

[**XmlFileSource**](https://github.com/vostok/configuration.sources.xml/blob/master/Vostok.Configuration.Sources.Xml/XmlFileSource.cs) parses XML files and automatically watches for changes:

```text
var source = new XmlFileSource("settings/config.xml");
```

A file that does not exist simply leads to a `null` [node](../concepts-and-basics/settings-nodes/), which implies default settings values unless something is [explicitly required](../basic-scenarios/make-settings-required.md).

### Related pages

{% page-ref page="../concepts-and-basics/configuration-sources.md" %}



