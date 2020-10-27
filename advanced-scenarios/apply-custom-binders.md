# Apply custom binders

**Requires**: [abstractions module](../modules/abstractions.md).

This extension point covers scenarios where [existing binders](../binding/) are not sufficient to handle required types.

Custom binders should be used as a last resort when [constructor injection](../binding/constructors.md) and [parsing conventions](../binding/primitives.md#parse-method-convention) are not powerful enough.

Creating a binder for a type is just a matter of implementing an interface:

```text
class MyComplexTypeBinder : ISettingsBinder<MyComplexType>
{
    public MyComplexType Bind([CanBeNull] ISettingsNode node)
    {
        ...
    }
}
```

Custom binders can be applied to specific fields and properties or whole types:

```text
class MySettings 
{
    [BindBy(typeof(MyComplexTypeBinder))]
    public MyComplexType ComplexProperty { get; }
}
```

```text
[BindBy(typeof(MyComplexTypeBinder))]
class MyComplexType
{
}
```

### Related pages

{% page-ref page="../concepts-and-basics/binding-nodes-to-models.md" %}

{% page-ref page="../binding/" %}

