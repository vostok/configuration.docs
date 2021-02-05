# JSON sources

**Location**: [Sources.Json module](../modules/sources.json.md).

[**JsonStringSource**](https://github.com/vostok/configuration.sources.json/blob/master/Vostok.Configuration.Sources.Json/JsonStringSource.cs) parses well-formed JSON documents from in-memory strings and supports manual external updates:

```text
var source = new JsonStringSource("<json content>");

​source.Push("<json content>") // update with new content
```

​[**JsonFileSource**](https://github.com/vostok/configuration.sources.json/blob/master/Vostok.Configuration.Sources.Json/JsonFileSource.cs) parses JSON files and automatically watches for changes:

```text
var source = new JsonFileSource("settings/config.json");
```

A file that does not exist simply leads to a `null` [node](../concepts-and-basics/settings-nodes/), which implies default settings values unless something is [explicitly required](../basic-scenarios/make-settings-required.md).

### Related pages

{% page-ref page="../concepts-and-basics/configuration-sources.md" %}



