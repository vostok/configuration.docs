# Use value substitutions

**Requires**: [sources module](../modules/sources.md).

Value substitution feature allows to replace placeholders in settings data. It's based on the [transformation extensions](transform-sources.md) and uses `#{}` syntax for placeholders.

```text
var originalSource = new JsonFileSource("settings.json");

var substitutions = new []
{
    new Substitution("param1", "value1"),
    new Substitution("param2", () => "value2")
};

var templatedSource = originalSource.Substitute(substitutions);
```

```text
Data in originalSource:
{
    "param1": "#{param1}",
    "param2": "#{param2}",
    "param3": "value3",
    "param4": "#{param4}"
}
```

```text
Data in templatedSource:
{
    "param1": "value1",
    "param2": "value2",
    "param3": "value3",
    "param4": "#{param4}"
}
```

### Related pages

{% page-ref page="../modules/sources.md" %}

{% page-ref page="transform-sources.md" %}

