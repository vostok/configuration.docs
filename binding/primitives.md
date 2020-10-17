# Primitives

Primitive types are parsed from string values in [value nodes](../concepts-and-basics/settings-nodes/value-nodes.md).

### Supported types

| Type | Allowed format examples |
| :--- | :--- |
| `string` | Literally any string. |
| `char` | Literally any single character. |
| `bool` | `true`, `True`, `TRUE` |
| `byte, sbyte` | Anything built-in `TryParse` method can grok. |
| `short, ushort` | Anything built-in `TryParse` method can grok. |
| `int, uint` | Anything built-in `TryParse` method can grok. |
| `long, ulong` | Anything built-in `TryParse` method can grok. |
| `float, double, decimal` | `1.23`, `1,23`, `5,12e2` |
| `Guid` | Anything built-in `TryParse` method can grok. |
| `Uri` | `http://example.com`, `example.com/some`, `/part/of/path` |
| `TimeSpan` | `00:12:34`, `2 seconds`, `500 ms`, `1.5 days`, `10s`, `0.5 minutes` |
| `DateTime(Offset)` | `2018-03-14 15:09:26.535`, `20050809T181142+0330` |
| `IPAddress` | `127.0.0.1`, `2001:0db8:11a3:09d7:1f34:8a2e:07a0:765d` |
| `IPEndPoint` | `192.168.1.10:80` |
| [`DataSize`](https://github.com/vostok/configuration/blob/master/Vostok.Configuration/Primitives/DataSize.cs)\`\` | `453453` \(just bytes\), `1 kb`, `24.3 megabytes`, `500 TB` |
| [`DataRate`](https://github.com/vostok/configuration/blob/master/Vostok.Configuration/Primitives/DataRate.cs)\`\` | `500` \(just bytes/sec\), `200 kilobytes/second`, `5 GB/sec`, `80 mb/s` |
| `Encoding` | `utf-8`, `us-ascii` |
| `Enum` types | Anything built-in `TryParse` method can grok. |
| Nullable structs | A valid value or `null`. |

[DataSize](https://github.com/vostok/configuration/blob/master/Vostok.Configuration/Primitives/DataSize.cs) and [DataRate](https://github.com/vostok/configuration/blob/master/Vostok.Configuration/Primitives/DataRate.cs) are custom new types. They also provide factory extensions and operators:

```text
DataSize size = 50.Megabytes();
DataRate rate = size / 2.Seconds();
```

### Parse method convention

There's also support for types that implement `Parse` or `TryParse` method with standard signature:

```text
class/struct T 
{
    T Parse(string input);
    
    bool TryParse(string input, out T result)
}
```

This allows to use arbitrary types with string representation without resorting to [implementation of custom binders](../advanced-scenarios/apply-custom-binders.md).

### Node requirements

[Value node](../concepts-and-basics/settings-nodes/value-nodes.md) or a container \(array/object\) node with a single value node child.

### Null node handling

Default type value is used unless [explictly required](../basic-scenarios/make-settings-required.md).

Explicitly specified `null` string value has the same effect.

### Incorrect format handling

Parsing errors arising from incorrect value formats lead to binder failure and result in exceptions, even for optional members \(see [classes and structs](classes-and-structs.md) for more context\).

### Related pages

{% page-ref page="../concepts-and-basics/binding-nodes-to-models.md" %}

