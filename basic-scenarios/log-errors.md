# Log errors

**Requires**: [logging module](../modules/logging.md).

See [error handling](../concepts-and-basics/error-handling.md) for cases where this logging is useful.

See [logging documentation](https://vostok.gitbook.io/logging/) for the log interface required here. 

```text
var providerSettings = new ConfigurationProviderSettings();

providerSettings = providerSettings.WithErrorLogging(log);

var provider = new ConfigurationProvider(providerSettings);
```

{% hint style="info" %}
Secret settings should be [marked with an attribute](make-settings-secret.md) to avoid being logged.
{% endhint %}

