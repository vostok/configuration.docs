# Sources.Yaml

### Description

This library contains [YAML-based](../sources/yaml-sources.md) configuration [source](../concepts-and-basics/configuration-sources.md) implementations: [file](https://github.com/vostok/configuration.sources.yaml/blob/master/Vostok.Configuration.Sources.Yaml/YamlFileSource.cs) and [string](https://github.com/vostok/configuration.sources.yaml/blob/master/Vostok.Configuration.Sources.Yaml/YamlStringSource.cs). It also exposes a configuration [parser](https://github.com/vostok/configuration.sources.yaml/blob/master/Vostok.Configuration.Sources.Yaml/YamlConfigurationParser.cs) for integration with other sources, such as [ClusterConfig](../sources/clusterconfig-source.md).

### Source and packages

**GitHub repository:** [vostok/configuration.sources.yaml](https://github.com/vostok/configuration.sources.yaml)

**NuGet package**: [Vostok.Configuration.Sources.Yaml](https://www.nuget.org/packages/Vostok.Configuration.Sources.Yaml)

```text
Install-Package Vostok.Configuration.Sources.Yaml
```

[Cement](https://github.com/skbkontur/cement) users should reference this module with the following command:

```text
cm ref add vostok.configuration.sources.yaml <path-to-project>
```

### Related pages

{% page-ref page="../sources/yaml-sources.md" %}

{% page-ref page="../sources/clusterconfig-source.md" %}



