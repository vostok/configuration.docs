# Scope sources

**Requires**: [main sources module](../modules/sources.md).

A source can be scoped just like [settings nodes can](../concepts-and-basics/settings-nodes-scoping.md). Resulting source's data is exactly base source's data scoped to given path:

```text
var baseSource = new JsonFileSource("settings.json");
var scopedSource = baseSource.ScopeTo("secrets");
var scopedTooFarSource = baseSource.ScopeTo("timeouts", "unknown-section");
```

```text
Data in baseSource:

{
    "Timeouts":
    {
        "DbTimeout": "20 seconds"
    },
    "Secrets":
    {
        "ApiKey": "xxxx-xxxx-xxxx"
    } 
}
```

```text
Data in scopedSource:

{
    "Secrets":
    {
        "ApiKey": "xxxx-xxxx-xxxx"
    }
}
```

```text
Data in scopedTooFarSource:

{
}
```

### Related pages

{% page-ref page="../concepts-and-basics/settings-nodes-scoping.md" %}

{% page-ref page="../concepts-and-basics/configuration-sources.md" %}

