# Constructor wrappers

If a type has exactly one constructor with a single argument of a type that can be bound, then it can also be bound with argument injection. This is especially useful for [collections](collections.md) customization:

```text
public class PerServiceSettings : Dictionary<string, string>
{
    public PerServiceSettings(Dictionary<string, string> dictionary)
        : base(dictionary, StringComparer.OrdinalIgnoreCase)
    {
    }
}
```

### Related pages

{% page-ref page="collections.md" %}



