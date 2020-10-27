# Print contents of a source

**Requires**: [main module](../modules/configuration.md).

```text
var source = new JsonFileSource("settings.json");

ISettingsNode contents = source.Get();

Console.Out.WriteLine(contents);
```

### Related pages

{% page-ref page="../concepts-and-basics/settings-nodes/" %}

{% page-ref page="../basic-scenarios/print-settings.md" %}

