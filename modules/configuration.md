# Configuration

### Description

This library contains an [implementation](https://github.com/vostok/configuration/blob/master/Vostok.Configuration/ConfigurationProvider.cs) of [configuration provider](../concepts-and-basics/configuration-provider.md), [binding](../binding/), and a couple of custom configuration primitives \(such as [DataSize](https://github.com/vostok/configuration/blob/master/Vostok.Configuration/Primitives/DataSize.cs) and [DataRate](https://github.com/vostok/configuration/blob/master/Vostok.Configuration/Primitives/DataRate.cs)\).  

### Source and packages

**GitHub repository:** [vostok/configuration](https://github.com/vostok/configuration)

**NuGet package**: [Vostok.Configuration](https://www.nuget.org/packages/Vostok.Configuration)

```text
Install-Package Vostok.Configuration
```

[Cement](https://github.com/skbkontur/cement) users should reference this module with the following command:

```text
cm ref add vostok.configuration <path-to-project>
```

### Related pages

{% page-ref page="../concepts-and-basics/configuration-provider.md" %}

{% page-ref page="../concepts-and-basics/binding-nodes-to-models.md" %}

{% page-ref page="../binding/" %}

{% page-ref page="../basic-scenarios/assign-sources-to-types.md" %}

{% page-ref page="../basic-scenarios/obtain-settings-from-provider.md" %}

{% page-ref page="../basic-scenarios/observe-settings-via-provider.md" %}



