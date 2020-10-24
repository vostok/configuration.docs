# Assign sources to types

**Requires**: [main module](../modules/configuration.md).

When using [configuration providers](../concepts-and-basics/configuration-provider.md), **Get** and **Observe** method overloads without parameters require an explicit association of the model type with a [configuration source](../concepts-and-basics/configuration-sources.md).

```text
// This simply won't work (no source defined):

provider.Get<MySettings>();
provider.Observe<MySettings>();
```

```text
// This will work as expected:

provider.SetupSourceFor<MySettings>(new JsonFileSource("settings.json"));

provider.Get<MySettings>();
provider.Observe<MySettings>();
```

A source can only be assigned to a type before any **Get** or **Observe** calls are made for that type:

```text
provider.SetupSourceFor<MySettings>(source1); // succeeds

provider.SetupSourceFor<MySettings>(source2); // succeeds, overwrites

provider.Get<MySettings>();

provider.SetupSourceFor<MySettings>(source3); // fails
```

 

