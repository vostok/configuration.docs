# Sources.Json

### Description

This library contains [JSON-based](../sources/json-sources.md) configuration [source](../concepts-and-basics/configuration-sources.md) implementations: [file](https://github.com/vostok/configuration.sources.json/blob/master/Vostok.Configuration.Sources.Json/JsonFileSource.cs) and [string](https://github.com/vostok/configuration.sources.json/blob/master/Vostok.Configuration.Sources.Json/JsonStringSource.cs). It also exposes a configuration [parser ](https://github.com/vostok/configuration.sources.json/blob/master/Vostok.Configuration.Sources.Json/JsonConfigurationParser.cs)for integration with other sources, such as [ClusterConfig](../sources/clusterconfig-source.md).

### Source and packages

**GitHub repository:** [vostok/configuration.sources.json](https://github.com/vostok/configuration.sources.json)

**NuGet package**: [Vostok.Configuration.Sources.Json](https://www.nuget.org/packages/Vostok.Configuration.Sources.Json)

```text
Install-Package Vostok.Configuration.Sources.Json
```

[Cement](https://github.com/skbkontur/cement) users should reference this module with the following command:

```text
cm ref add vostok.configuration.sources.json <path-to-project>
```

### Related pages

{% page-ref page="../sources/json-sources.md" %}

{% page-ref page="../sources/clusterconfig-source.md" %}



