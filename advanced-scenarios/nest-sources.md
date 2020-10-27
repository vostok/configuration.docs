# Nest sources

**Requires**: [sources module](../modules/sources.md).

This operation allows to embed source's data into a nested object section:

```text
var source = new ObjectSource(new {A = 1, B = 2});

var nestedSource = source.Nest("obj1", "obj2");
```

```text
Data in nestedSource:

{
    "obj1":
    {
        "obj2":
        {
            "A": "1",
            "B": "2"
        }
    }
}
```

### Related pages

{% page-ref page="../concepts-and-basics/configuration-sources.md" %}

{% page-ref page="../basic-scenarios/scope-sources.md" %}

