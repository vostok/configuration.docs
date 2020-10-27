# Use shared provider instance

**Requires**: [main module](../modules/configuration.md).

[Configuration provider](../concepts-and-basics/configuration-provider.md) class has a property named `Default` that serves as a global static source of `IConfigurationProvider` instance.

It's intended use case is self-sufficient configuration in libraries: library authors may not want to force their users to provide an `IConfigurationProvider` instance each time they're using library classes. Instead, these classes could just obtain a log from the shared property:

```text
ConfigurationProvider.Default.SetupSourceFor<MyLibrarySettings>(...);

var settings = ConfigurationProvider.Default.Get<MyLibrarySettings>();
```

By default this property returns a singleton provider with default settings. It can be configured explicitly in the application:

```text
var providerSettings = new ConfigurationProviderSettings { ... };
var provider = new ConfigurationProvider(providerSettings);

// Will return false if already explicitly configured:
ConfigurationProvider.TrySetDefault(provider);
```

### Related pages

{% page-ref page="../concepts-and-basics/configuration-provider.md" %}

