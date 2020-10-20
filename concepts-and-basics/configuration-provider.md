# Configuration provider

### Overview

[**Configuration provider**](https://github.com/vostok/configuration.abstractions/blob/master/Vostok.Configuration.Abstractions/IConfigurationProvider.cs) is responsible for the [binding process](binding-nodes-to-models.md) and offers methods to obtain final settings models. It's also responsible for [caching](caching-and-performance.md) and [error handling](error-handling.md). Providers are used directly by the application code to either [obtain settings on demand](../basic-scenarios/obtain-settings-from-provider.md) or [subscribe to updates](../basic-scenarios/observe-settings-via-provider.md).

### Methods

#### Get method

Fetches the newest version of settings of given type:

```text
var settings = provider.Get<MySettings>();
```

#### Observe method

Allows to subscribe for updates of settings of given type:

```text
provider.Observe<MySettings>.Subscribe(newSettings => {});
```

#### Method variants

Both **Get** and **Observe** methods have 2 variations:

* The one without any parameters requires a prior [assignment](../basic-scenarios/assign-sources-to-types.md) of a source to the requested type;
* The one with a [source](configuration-sources.md) parameter requires no such assignment \(but check out [caching](caching-and-performance.md) for gotchas\);

### Related pages

{% page-ref page="../basic-scenarios/obtain-settings-from-provider.md" %}

{% page-ref page="../basic-scenarios/observe-settings-via-provider.md" %}

{% page-ref page="binding-nodes-to-models.md" %}

{% page-ref page="configuration-sources.md" %}

{% page-ref page="../basic-scenarios/assign-sources-to-types.md" %}

{% page-ref page="caching-and-performance.md" %}

{% page-ref page="error-handling.md" %}



