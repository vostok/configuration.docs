# Make settings secret

**Requires**: [abstractions module](../modules/abstractions.md).

By default settings are subject to [logging](log-new-settings.md), which is generally not appropriate for secrets. This can be fixed either by disabling logging entirely on the [configuration provider](../concepts-and-basics/configuration-provider.md) or by annotating fields and properties of the model with `[Secret]` attribute:

```text
class MySettings 
{
    [Secret]
    public MySecrets Secrets { get; } = new MySecrets();
    
    public TimeSpan Timeout { get; } = TimeSpan.FromSeconds(30);
    
    [Secret]
    public string EncryptionKey { get; }
}

class MySecrets 
{
    public string ApiKey { get; }
    public string Login { get; }
    public string Password { get; }
}
```

### Related pages

{% page-ref page="log-new-settings.md" %}

{% page-ref page="log-errors.md" %}

