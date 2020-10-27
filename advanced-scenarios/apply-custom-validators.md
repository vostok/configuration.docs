# Apply custom validators

**Requires**: [abstractions module](../modules/abstractions.md).

Validation feature allows to associate a custom user-made validator to a settings type. Validation occurs during [binding](../concepts-and-basics/binding-nodes-to-models.md) and results in binding errors for incorrect settings.

```text
[ValidateBy(typeof(MySettingsValidator))]
class MySettings
{
    int CacheCapacity { get; }
}
```

```text
class MySettingsValidator: ISettingsValidator<MySettings>
{
    // Returns validation errors. Empty enumerable == success.
    public IEnumerable<string> Validate(MySettings settings)
    {
        if (settings.CacheCapacity <= 0)
            yield return "Cache capacity must be positive.";
    }
}
```

### Related pages

{% page-ref page="../basic-scenarios/obtain-settings-from-provider.md" %}

{% page-ref page="../concepts-and-basics/binding-nodes-to-models.md" %}

