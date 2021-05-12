# Apply source data to existing object

**Requires**: [abstractions module](../modules/abstractions.md), [main module](../modules/configuration.md).

```text
var settings = new MySettings();

var source = GetSource(); // IConfigurationSource

source.ApplyTo(settings); // doesn't overwrite fields and properties not present in the source
```

