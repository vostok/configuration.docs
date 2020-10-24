# Error handling

This page describes how [configuration providers](configuration-provider.md) deal with errors arising from [sources](configuration-sources.md) and [binders](../binding/).

It can be summarized in two simple rules:

* If an error occurs and no correct settings instance has been observed for the requested type thus far, the error is propagated to the calling code, resulting in exceptions from **Get** method. A subsequent settings update with correct data automatically "heals" future **Get** calls.  

* If an error occurs and a correct settings instance has already been observed for the requested type at least once, the error is [reported in background](../basic-scenarios/log-errors.md) and does not cause **Get** method to fail: last seen correct instance is returned from cache instead.

```text
// the source contains incorrect data

provider.Get<MySettings>(); // throws an exception

// the source updates with correct data

provider.Get<MySettings>(); // returns settings

// the source updates with incorrect data once again

provider.Get<MySettings>(); // returns settings from cache
```

{% hint style="warning" %}
The second guarantee can be violated by cache overflow events. Read the [caching section](caching-and-performance.md) to find out how to avoid them.
{% endhint %}

{% hint style="info" %}
**Observe** method never produces `OnError` or `OnCompleted` notifications. It only reports successful settings updates. The errors are handled in background and [can be logged](../basic-scenarios/log-errors.md).
{% endhint %}

### Related pages

{% page-ref page="configuration-provider.md" %}

{% page-ref page="../basic-scenarios/log-errors.md" %}

{% page-ref page="../basic-scenarios/obtain-settings-from-provider.md" %}

{% page-ref page="../basic-scenarios/obtain-settings-from-provider.md" %}



