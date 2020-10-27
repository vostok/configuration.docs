# Use name aliases

**Requires**: [abstractions module](../modules/abstractions.md).

Name aliases provide alternative keys to look for in [settings nodes](../concepts-and-basics/settings-nodes/) when performing [binding](../concepts-and-basics/binding-nodes-to-models.md).

They can be applied to fields and properties with a special attribute:

```text
class MySettings 
{
    [Alias("LegacyTimeout")]
    public TimeSpan Timeout { get; }
}

// The property can be initialized from either "timeout" or "legacytimeout" key
```

It's allowed to assign multiple aliases to a single member:

```text
[Alias("alias1")]
[Alias("alias2")]
public TimeSpan Timeout { get; }
```

**Aliases cannot handle ambiguity**. If the source returns data with more than one of the lookup keys assigned to a field or property, binding fails with an error.

```text
Ambiguous data examples:
{ "timeout": "...", "alias1": "..." }
{ "alias1": "...", "alias2": "..." }
```

### Related pages

{% page-ref page="../concepts-and-basics/binding-nodes-to-models.md" %}

{% page-ref page="../binding/classes-and-structs.md" %}

