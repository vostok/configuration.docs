# Environment variables source

**Location**: [main sources module](../modules/sources.md).

[**EnvironmentVariablesSource**](https://github.com/vostok/configuration.sources/blob/master/Vostok.Configuration.Sources/Environment/EnvironmentVariablesSource.cs) **** converts process environment variables into settings nodes.

```
var source = new EnvironmentVariablesSource();
```

Keys with dots, colons and double underscores are treated as hierarchical and get split into segments:

```
throttling.capacity=50 --> { "throttling": { "capacity": "50" } }
throttling:capacity=50 --> { "throttling": { "capacity": "50" } }
throttling__capacity=50 --> { "throttling": { "capacity": "50" } }
```

This source is static and never issues data updates.

### Related pages

{% content-ref url="../concepts-and-basics/configuration-sources.md" %}
[configuration-sources.md](../concepts-and-basics/configuration-sources.md)
{% endcontent-ref %}
