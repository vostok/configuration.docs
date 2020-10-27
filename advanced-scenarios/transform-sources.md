# Transform sources

**Requires**: [sources module](../modules/sources.md).

This operation allows to modify source contents by applying a custom delegate. Most often this involves rewriting values stored in [value nodes](../concepts-and-basics/settings-nodes/value-nodes.md):

```text
class MyTransformer : ValueNodeTransformer
{
    public MyTransformer()
        : base(node => new ValueNode(node.Name, node.Value?.Replace(..., ...)))
    {
    }
}
```

```text
var transformedSource = source.Transform(new MyTransformer());
```

### Related pages

{% page-ref page="../concepts-and-basics/configuration-sources.md" %}

{% page-ref page="../concepts-and-basics/settings-nodes/" %}

{% page-ref page="use-source-templating.md" %}

