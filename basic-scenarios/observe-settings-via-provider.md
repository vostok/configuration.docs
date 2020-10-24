# Observe settings via provider

**Requires**: [main module](../modules/configuration.md).

One can subscribe to settings updates for a type with [configuration provider](../concepts-and-basics/configuration-provider.md)'s **Observe** method.

With prior [assignment of sources](assign-sources-to-types.md):

```text
provider.Observe<MySettings>().Subscribe(newSettings => {});
```

With sources passed on per-call basis:

```text
provider.Observe<MySettings>(new JsonFileSource("settings1.json"))
    .Subscribe(newSettings => {});
```

Temporary subscriptions should be disposed of as they might hold on to resources in [sources](../concepts-and-basics/configuration-sources.md):

```text
var subscription = provider.Observe<MySettings>().Subscribe(OnNewSettings);

using (subscription)
{
    // ...
}
```

### Observe method behavior

* `OnError` and `OnCompleted` notifications are never produced. Only successful settings updates are propagated to the observers. This means that there will be no notifications if initial attempt to provide settings [fails with an error](../concepts-and-basics/error-handling.md) and no further data updates are published by the [source](../concepts-and-basics/configuration-sources.md).
  * The only way to notice errors when using **Observe** is to [enable error logging](log-errors.md).
* The subscription is not guaranteed to immediately produce a notification. The first notification may be delayed due to data not having been fetched from the source yet. However, once a valid settings instance has been observed, all new observers receive a notification with current actual settings upon subscription. This notification is published on a background thread, so don't count on it being delivered after `Subscribe` call completes.

 

### Best practices

It's recommended to obtain initial settings instance with **Get** method before subscribing to updates with **Observe**. This practice ensures correct error propagation, warms up the [cache](../concepts-and-basics/caching-and-performance.md) and eliminates situations where the settings are not ready yet on access attempt. 

```text
private volatile MySettings settings;
 
public Task InitializeAsync(IConfigurationProvider provider)
{
    OnSettingsUpdated(settings = provider.Get<MySettings>());
         
    provider.Observe<MySettings>()
      .Subscribe(newSettings => OnSettingsUpdated(settings = newSettings));
 
    return Task.CompletedTask;
}
 
private void OnSettingsUpdated(MySettings settings) 
{
    // ... 
}
```

### Related pages

{% page-ref page="../concepts-and-basics/configuration-provider.md" %}

{% page-ref page="../concepts-and-basics/configuration-sources.md" %}

{% page-ref page="../concepts-and-basics/caching-and-performance.md" %}

{% page-ref page="../concepts-and-basics/error-handling.md" %}

