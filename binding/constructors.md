# Constructor injection

A type that has exactly one constructor with a single argument of a type that can be bound can also be bound with argument injection. This is especially useful for [collection](collections.md) customization:

```text
class PerServiceSettings : Dictionary<string, string>
{
    public PerServiceSettings(Dictionary<string, string> dictionary)
        : base(dictionary, StringComparer.OrdinalIgnoreCase)
    {
    }
}
```

This technique can also be used for additional initialization or settings data preprocessing:

```text
class PerServiceSettings
{
    public PerServiceSettings(Dictionary<string, string> data)
    {
        Index = data;
        
        InvertedIndex = Index.ToDictionary(
            pair => pair.Value,
            pair => pair.Key
        );
    }

    public Dictionary<string, string> Index { get; }
    
    public Dictionary<string, string> InvertedIndex { get; }
}
```

### Related pages

{% page-ref page="collections.md" %}



