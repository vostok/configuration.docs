# Quickstart

Here's the simplest way to experience Vostok.Configuration for the first time:

* Install [main](modules/configuration.md), [abstractions](modules/abstractions.md) and [sources.json](modules/sources.json.md) modules:

```text
Install-Package Vostok.Configuration
Install-Package Vostok.Configuration.Abstractions
Install-Package Vostok.Configuration.Sources.Json
```

* Define a settings model class:

```text
class MySettings 
{
    public string Key1 { get; }
    public string Key2 { get; }
}
```

* Create a JSON file with settings:

```text
{
    "key1": "value1",
    "key2": "value2"
}
```

* Obtain a model instance with a [configuration provider](concepts-and-basics/configuration-provider.md) from a file [source](concepts-and-basics/configuration-sources.md) and print it:

```text
var provider = new ConfigurationProvider();

provider.SetupSourceFor<MySettings>(new JsonFileSource("settings.json"));

var settings = provider.Get<MySettings>();

Console.Out.WriteLine(ConfigurationPrinter.Print(settings));
```

Great job! Here are some possible next steps:

* Learn the most basic concepts: [settings nodes](concepts-and-basics/settings-nodes/), [sources](concepts-and-basics/configuration-sources.md), [binding](concepts-and-basics/binding-nodes-to-models.md), [provider](concepts-and-basics/configuration-provider.md);
* Explore available [modules](modules/) and [source implementations](modules/sources.md);
* Go over the [basic scenarios section](basic-scenarios/).

