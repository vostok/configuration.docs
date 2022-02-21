# Caching and performance

[Configuration providers](configuration-provider.md) cache [bound](binding-nodes-to-models.md) settings for each `(type, source)` pair where sources are compared by reference. Caching ensures a solid performance level: only the first **Get** call **** is somewhat expensive while all the subsequent ones are extremely cheap. The cache is automatically updated when the underlying [source](configuration-sources.md) issues new data.

```
provider.Get<MySettings>(); // may block and incurs binding costs

provider.Get<MySettings>(); // instantly returns a cached object

// ... the source issues a data update ...

provider.Get<MySettings>(); // instantly returns the old cached object

// ... the cache is automatically updated in background...

provider.Get<MySettings>(); // instantly returns an updated cached object
```

{% hint style="info" %}
Due to caching, [configuration provider](configuration-provider.md) instances should be reused as much as possible. Ideally there should be just one singleton instance in the application.
{% endhint %}

{% hint style="warning" %}
Special care should be taken when using **Get** and **Observe** methods with short-lived source instances passed on per-call basis. This could cause poor performance due to cache misses and even lead to cache overflow events. Overflow events may cause violations of [error handling guarantees](error-handling.md). Default cache capacity [is 50](https://github.com/vostok/configuration/blob/master/Vostok.Configuration/ConfigurationProviderSettings.cs#L50) but can be tuned in provider settings:

```
var settings = new ConfigurationProviderSettings 
{
    MaxSourceCacheSize = 100_000
};

var provider = new ConfigurationProvider(settings);
```

This pitfall is easy to fall into as all of the source-related extensions ([combine](../basic-scenarios/combine-sources.md), [scope](../basic-scenarios/scope-sources.md), [transform](../advanced-scenarios/transform-sources.md), etc) return decorators that are treated as distinct sources. The only viable solution is to cache these derivative sources. &#x20;
{% endhint %}

### Related pages

{% content-ref url="configuration-provider.md" %}
[configuration-provider.md](configuration-provider.md)
{% endcontent-ref %}

{% content-ref url="../basic-scenarios/log-new-settings.md" %}
[log-new-settings.md](../basic-scenarios/log-new-settings.md)
{% endcontent-ref %}

{% content-ref url="../basic-scenarios/obtain-settings-from-provider.md" %}
[obtain-settings-from-provider.md](../basic-scenarios/obtain-settings-from-provider.md)
{% endcontent-ref %}

{% content-ref url="../basic-scenarios/observe-settings-via-provider.md" %}
[observe-settings-via-provider.md](../basic-scenarios/observe-settings-via-provider.md)
{% endcontent-ref %}
