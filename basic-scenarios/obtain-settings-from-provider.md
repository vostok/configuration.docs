# Obtain settings from provider

**Requires**: [main module](../modules/configuration.md).

Settings can be obtained on-demand with [configuration provider](../concepts-and-basics/configuration-provider.md)'s **Get** method.

With prior [assignment of sources](assign-sources-to-types.md):

```text
var settings = provider.Get<MySettings>();
```

With sources passed on per-call basis:

```text
var settings = provider.Get<MySettings>(new JsonFileSource("settings.json"));
```

### Get method behavior

* Always returns the most recent version of settings \(updates may happen in background\):

  * Call **Get** on every settings access for "hot" configuration;
  * Call **Get** once and cache the result for "cold" configuration;

* First call for a type may block or [throw exceptions](../concepts-and-basics/error-handling.md) due to source latency, data unavailability or incorrect data format. This behavior persists until a data update remedies the error;

* Once warmed up, subsequent calls never block or throw errors and are extremely cheap due to [caching](../concepts-and-basics/caching-and-performance.md). Future errors are not propagated to the calling code, but [can be logged](log-errors.md). **Get** calls return the last seen correct settings object;



### Related pages

{% page-ref page="../concepts-and-basics/configuration-provider.md" %}

{% page-ref page="../concepts-and-basics/configuration-sources.md" %}

{% page-ref page="../concepts-and-basics/caching-and-performance.md" %}

{% page-ref page="../concepts-and-basics/error-handling.md" %}



