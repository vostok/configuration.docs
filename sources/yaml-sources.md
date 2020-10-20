# YAML sources

**Location**: [Sources.Yaml module](../modules/sources.yaml.md).

[**YamlStringSource**](https://github.com/vostok/configuration.sources.yaml/blob/master/Vostok.Configuration.Sources.Yaml/YamlStringSource.cs) parses well-formed YAML documents from in-memory strings and supports manual external updates:

```text
var source = new YamlStringSource("<...>")

source.Push("<...>") // update with new content
```

[**YamlFileSource**](https://github.com/vostok/configuration.sources.yaml/blob/master/Vostok.Configuration.Sources.Yaml/YamlFileSource.cs) parses YAML files and automatically watches for changes:

```text
var source = new YamlFileSource("settings/config.yml");
```

A file that does not exist simply leads to a `null` [node](../concepts-and-basics/settings-nodes/), which implies default settings values unless something is [explicitly required](../basic-scenarios/make-settings-required.md).

