# Sources

### Description

This library contains a few basic implementations of [configuration sources](../concepts-and-basics/configuration-sources.md), such as [ObjectSource](https://github.com/vostok/configuration.sources/blob/master/Vostok.Configuration.Sources/Object/ObjectSource.cs), [FileSource](https://github.com/vostok/configuration.sources/blob/master/Vostok.Configuration.Sources/File/FileSource.cs), [ConstantSource](https://github.com/vostok/configuration.sources/blob/master/Vostok.Configuration.Sources/Constant/ConstantSource.cs), [CommandLineSource](https://github.com/vostok/configuration.sources/blob/master/Vostok.Configuration.Sources/CommandLine/CommandLineSource.cs), [EnvironmentVariablesSource](https://github.com/vostok/configuration.sources/blob/master/Vostok.Configuration.Sources/Environment/EnvironmentVariablesSource.cs). It also hosts a set of extensions to manipulate sources \([combine](../basic-scenarios/combine-sources.md), [scope](../basic-scenarios/scope-sources.md), [freeze](../advanced-scenarios/freeze-sources.md), [nest](../advanced-scenarios/nest-sources.md), [transform](../advanced-scenarios/transform-sources.md), [template](../advanced-scenarios/use-source-templating.md)\) and helpers aiding in [creation of custom sources](../advanced-scenarios/create-custom-sources.md).

### Source and packages

**GitHub repository:** [vostok/configuration.sources](https://github.com/vostok/configuration.sources)

**NuGet package**: [Vostok.Configuration.Sources](https://www.nuget.org/packages/Vostok.Configuration.Sources)

```text
Install-Package Vostok.Configuration.Sources
```

[Cement](https://github.com/skbkontur/cement) users should reference this module with the following command:

```text
cm ref add vostok.configuration.sources <path-to-project>
```

### Related pages

{% page-ref page="../concepts-and-basics/configuration-sources.md" %}

{% page-ref page="../sources/" %}

{% page-ref page="../basic-scenarios/combine-sources.md" %}

{% page-ref page="../basic-scenarios/scope-sources.md" %}

{% page-ref page="../advanced-scenarios/create-custom-sources.md" %}

{% page-ref page="../advanced-scenarios/transform-sources.md" %}





