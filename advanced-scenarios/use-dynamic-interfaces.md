# Use dynamic interfaces

**Requires**: [main module](../modules/configuration.md).

The basic recommended way to get most up-to-date settings in the presence of background updates is to use [provider](../concepts-and-basics/configuration-provider.md)'s **Get** method \(see the [relevant scenario](../basic-scenarios/obtain-settings-from-provider.md)\) on each access attempt. However, it's also possible to obtain an inherently dynamic settings model whose properties are updated under the hood. This requires to use an interface as the settings model:

```text
interface IMySettings
{
    string Option1 { get; }
    string Option2 { get; }
    ISubConfig Section { get; }
}

// Get once, use as a singleton:
var hotSettings = provider.CreateHot<IMySettings>(); 

// Properties of the 'hotSettings' object are mutable. 
// They will automatically return most up-to-date values.
```

Note that in order to get a guaranteed consistent view of the settings without "tearing" \(observing a mix of values from before and after update due to a race condition\) when using a nested object \(section\), it's recommended to access a snapshot of this nested object saved in a variable:

```text
var section = hotSettings.Section;

// access a consistent view of 'section` properties
```

### Related pages

{% page-ref page="../basic-scenarios/obtain-settings-from-provider.md" %}

{% page-ref page="../basic-scenarios/assign-sources-to-types.md" %}

