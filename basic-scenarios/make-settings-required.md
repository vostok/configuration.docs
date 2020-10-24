# Make settings required

**Requires**: [abstractions module](../modules/abstractions.md).

By default all settings are optional; that is, absence of relevant data in the [source](../concepts-and-basics/configuration-sources.md) results in default values during [binding](../concepts-and-basics/binding-nodes-to-models.md) and does not produce errors. 

Some parts of configuration may be crucial to the application to the point that it's pointless to start without them being initialized. These fields and properties should be annotated with `[Required]` attribute:

```text
class MySettings 
{
    [Required]
    public string DbConnectionString { get; }
    
    [Required]
    public MySecrets Secrets { get; }
}

class MySecrets 
{
    public string ApiKey { get; }
    public string Login { get; }
    public string Password { get; }
}
```

```text
provider.Get<MySettings>(); // will throw if DbConnectionString or Secrets are not initialized 
```

### 

### Changing defaults

Default behavior can be inverted in the scope of a type with `[RequiredByDefault]` attribute. Individual fields and properties can then be made optional with `[Optional]` attribute:

```text
[RequiredByDefault]
class MySettings 
{
    [Optional]
    public TimeSpan Timeout { get; } = TimeSpan.FromSeconds(30);
}
```

### 

### Related pages

{% page-ref page="obtain-settings-from-provider.md" %}

{% page-ref page="observe-settings-via-provider.md" %}

{% page-ref page="../concepts-and-basics/binding-nodes-to-models.md" %}

