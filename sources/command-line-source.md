# Command line source

**Location**: [main sources module](../modules/sources.md).

[**CommandLineSource**](https://github.com/vostok/configuration.sources/blob/master/Vostok.Configuration.Sources/CommandLine/CommandLineSource.cs) converts CLI arguments into settings nodes.

```text
public static void Main(string[] args)
{
    var source = new CommandLineSource(args);
}
```

It supports 7 syntax options for key-value parameters:

* `--key=value`
* `--key value`
* `-key=value`
* `-key value`
* `/key=value`
* `/key value`
* `key=value`

Keys with dots \(such as `a.b.c`\) are treated as hierarchical and get split into segments:

```text
--throttling.capacity=50 --> { "throttling": { "capacity": "50" } }
```

Multiple occurrences of the same key are merged into arrays.

This source is static and never issues data updates.

### Defaults

Standalone keys may be optionally supplied with a default value.

Standalone values may be optionally grouped under default key.

```text
var source = new CommandLineSource(args, "main", "true");

--enable --> { "enable": "true" }
100 200 --> { "main": ["100", "200"] }
```

### Related pages

{% page-ref page="../concepts-and-basics/configuration-sources.md" %}



