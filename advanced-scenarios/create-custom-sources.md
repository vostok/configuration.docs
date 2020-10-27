# Create custom sources

**Requires**: [sources module](../modules/sources.md).

[Sources module](../modules/sources.md) offers a couple of base classes to assist in implementing custom [configuration sources](../concepts-and-basics/configuration-sources.md).

### [**ManualFeedSource**](https://github.com/vostok/configuration.sources/blob/master/Vostok.Configuration.Sources/Manual/ManualFeedSourceOfT.cs)

_For in-memory sources or sources that can update an in-memory one from a remote API_.

```text
class MySource : ManualFeedSource<string>
{
    public MySource()
        : base(Parse) { }

    private static ISettingsNode Parse(string input) { ... }
}

var source = new MySource();

source.Push("input1");
source.Push("input2");

// Push method can be used by an internal periodical/event-based update routine.
```

### [FileSource](https://github.com/vostok/configuration.sources/blob/master/Vostok.Configuration.Sources/File/FileSource.cs)

_For sources based on local files. Includes automatic reload on file updates._

```text
class MyFileSource : FileSource
{
    public MyFileSource(string filePath)
        : base(new FileSourceSettings(filePath), Parse) { }
        
    private static ISettingsNode Parse(string input) { ... }
}
```

### Related pages

{% page-ref page="../concepts-and-basics/configuration-sources.md" %}

{% page-ref page="../sources/constant-source.md" %}

{% page-ref page="../basic-scenarios/combine-sources.md" %}

{% page-ref page="../basic-scenarios/scope-sources.md" %}

{% page-ref page="nest-sources.md" %}

{% page-ref page="freeze-sources.md" %}

