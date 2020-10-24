# Log settings updates

**Requires**: [logging module](../modules/logging.md).

See [logging documentation](https://vostok.gitbook.io/logging/) for the log interface required here. 

```text
var providerSettings = new ConfigurationProviderSettings();

providerSettings = providerSettings.WithSettingsLogging(log);

var provider = new ConfigurationProvider(providerSettings);
```

{% hint style="info" %}
Secret settings should be [marked with an attribute](make-settings-secret.md) to avoid being logged.
{% endhint %}



