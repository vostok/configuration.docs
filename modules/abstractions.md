# Abstractions

### Description

This library contains core interfaces \([IConfigurationSource](https://github.com/vostok/configuration.abstractions/blob/master/Vostok.Configuration.Abstractions/IConfigurationSource.cs), [IConfigurationProvider](https://github.com/vostok/configuration.abstractions/blob/master/Vostok.Configuration.Abstractions/IConfigurationProvider.cs)\), intermediate data model \([settings nodes](https://github.com/vostok/configuration.abstractions/tree/master/Vostok.Configuration.Abstractions/SettingsTree)\) and attributes used to annotate user models, such as [RequiredAttribute](https://github.com/vostok/configuration.abstractions/blob/master/Vostok.Configuration.Abstractions/Attributes/RequiredAttribute.cs).

### Source and packages

**GitHub repository:** [vostok/configuration.abstractions](https://github.com/vostok/configuration.abstractions)

**NuGet package**: [Vostok.Configuration.Abstractions](https://www.nuget.org/packages/Vostok.Configuration.Abstractions)

```text
Install-Package Vostok.Configuration.Abstractions
```

[Cement](https://github.com/skbkontur/cement) users should reference this module with the following command:

```text
cm ref add vostok.configuration.abstractions <path-to-project>
```

### Related pages

{% page-ref page="../concepts-and-basics/settings-nodes/" %}

{% page-ref page="../concepts-and-basics/settings-nodes-merging.md" %}

{% page-ref page="../concepts-and-basics/settings-nodes-scoping.md" %}

{% page-ref page="../concepts-and-basics/configuration-sources.md" %}

{% page-ref page="../concepts-and-basics/configuration-provider.md" %}

{% page-ref page="../basic-scenarios/" %}

{% page-ref page="../basic-scenarios/make-settings-secret.md" %}

{% page-ref page="../basic-scenarios/make-settings-required.md" %}



