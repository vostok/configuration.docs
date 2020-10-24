# Constant sources

**Location**: [main sources module](../modules/sources.md).

### [ConstantSource](https://github.com/vostok/configuration.sources/blob/master/Vostok.Configuration.Sources/Constant/ConstantSource.cs)

A constant source returns a preconfigured [settings node](../concepts-and-basics/settings-nodes/) and never issues any updates.

```text
var source = new ConstantSource(new ValueNode("value"));
```

### [LazyConstantSource](https://github.com/vostok/configuration.sources/blob/master/Vostok.Configuration.Sources/Constant/LazyConstantSource.cs)

A lazy constant source does the same but defers the node acquisition until first subscription:

```text
var source = new LazyConstantSource(() => new ValueNode("value"));
```

Errors in the provided delegate are propagated via `(null, error)` notification. It's guaranteed to execute not more than once.

### Practical use

Constant sources are handy for unit testing and may serve as base classes for [custom sources](../advanced-scenarios/create-custom-sources.md).

### Related pages

{% page-ref page="../concepts-and-basics/configuration-sources.md" %}



