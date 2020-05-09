# Sources.Xml

### Description

This library contains [XML-based](../sources/xml-sources.md) configuration [source](../concepts-and-basics/configuration-sources.md) implementations: [file](https://github.com/vostok/configuration.sources.xml/blob/master/Vostok.Configuration.Sources.Xml/XmlFileSource.cs) and [string](https://github.com/vostok/configuration.sources.xml/blob/master/Vostok.Configuration.Sources.Xml/XmlStringSource.cs). It also exposes a configuration [parser](https://github.com/vostok/configuration.sources.xml/blob/master/Vostok.Configuration.Sources.Xml/XmlConfigurationParser.cs) for integration with other sources, such as [ClusterConfig](../sources/clusterconfig-source.md).

### Source and packages

**GitHub repository:** [vostok/configuration.sources.xml](https://github.com/vostok/configuration.sources.xml)

**NuGet package**: [Vostok.Configuration.Sources.Xml](https://www.nuget.org/packages/Vostok.Configuration.Sources.Xml)

```text
Install-Package Vostok.Configuration.Sources.Xml
```

[Cement](https://github.com/skbkontur/cement) users should reference this module with the following command:

```text
cm ref add vostok.configuration.sources.xml <path-to-project>
```

### Related pages

{% page-ref page="../sources/xml-sources.md" %}

{% page-ref page="../sources/clusterconfig-source.md" %}



