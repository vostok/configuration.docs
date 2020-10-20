# Configuration sources

Configuration sources fetch data from storage \(local files or remote APIs\) and convert it to [settings nodes](settings-nodes/), abstracting away actual data formats such as JSON or YAML. 

They are not meant to be consumed directly and should be used in conjunction with a [configuration provider](configuration-provider.md) \(see [assign sources to types](../basic-scenarios/assign-sources-to-types.md) and [obtain settings from provider](../basic-scenarios/obtain-settings-from-provider.md) scenarios\).

Sources are also responsible for data change detection. They expose a [reactive interface](https://github.com/vostok/configuration.abstractions/blob/master/Vostok.Configuration.Abstractions/IConfigurationSource.cs) with subscription support:

```text
IObservable<(ISettingsNode settings, Exception error)> Observe();
```

On each update, triggered either periodically or by an internal event, the source emits a pair: `(settings, null)` on success or `(null, error)` on failure. It's not required to deduplicate settings or errors at this level, although it's never wrong to do so.

Sources must never block indefinitely while waiting for data and should rather publish `null` settings after a short initial timeout.

Sources must be thread-safe and should be designed to support multiple concurrent observers. It is also expected that every new observer would immediately receive a notification with current state upon subscription.

Here are some of the often used source implementations:

* [JSON source](../sources/json-sources.md)
* [ClusterConfig source](../sources/clusterconfig-source.md)
* [In-memory object source](../sources/object-source.md)

It's also possible to [implement a custom source](../advanced-scenarios/create-custom-sources.md).

### Related pages

{% page-ref page="../modules/sources.md" %}

{% page-ref page="../basic-scenarios/combine-sources.md" %}

{% page-ref page="../basic-scenarios/scope-sources.md" %}

{% page-ref page="../advanced-scenarios/nest-sources.md" %}

{% page-ref page="../advanced-scenarios/transform-sources.md" %}

{% page-ref page="../advanced-scenarios/create-custom-sources.md" %}

{% page-ref page="../basic-scenarios/assign-sources-to-types.md" %}

{% page-ref page="../basic-scenarios/obtain-settings-from-provider.md" %}

