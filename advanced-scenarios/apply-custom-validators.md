# Apply custom validators

**Requires**: [abstractions module](../modules/abstractions.md), [main module](../modules/configuration.md) \(constaints\).

Validation feature allows to associate a custom user-made validator with a settings type. Validation occurs during [binding](../concepts-and-basics/binding-nodes-to-models.md) and results in binding errors for incorrect settings.

```text
[ValidateBy(typeof(MySettingsValidator))]
class MySettings
{
    int CacheCapacity { get; }
}
```

```text
class MySettingsValidator: ISettingsValidator<MySettings>
{
    // Returns validation errors. Empty enumerable == success.
    public IEnumerable<string> Validate(MySettings settings)
    {
        if (settings.CacheCapacity <= 0)
            yield return "Cache capacity must be positive.";
    }
}
```

### Constraints

There are also built-in validation constraints you can use to create a custom validator. Just inherit your validator class from `ConstraintsValidator` and override a method returning constraints to be checked:

```text
[ValidateBy(typeof(TestConfigValidator))]
class TestConfig
{
    public int Number;
    public string String;
}
```

```text
class TestConfigValidator : ConstraintsValidator<TestConfig>
{
    protected override IEnumerable<Constraint<TestConfig>> GetConstraints()
    {
        yield return new NotNullOrWhitespaceConstraint<TestConfig>(settings => settings.String);
        yield return new RangeConstraint<TestConfig, int>(settings => settings.Number, 2, 10);
    }
}
```

Here's a list of all currently implemented constraint types:

* `NotNullConstraint` for arbitrary reference types;
* `NotNullOrEmptyConstraint` for strings;
* `NotNullOrWhitespaceConstraint` for strings;
* `RangeConstraint`, `LessConstraint`, `LessOrEqualConstraint`, `GreaterConstraint` and `GreaterOrEqualConstraint` for any types that implement `IComparable`;
* `UniqueConstraint` to check that a set of field/properties only contains unique values;

### Related pages

{% page-ref page="../basic-scenarios/obtain-settings-from-provider.md" %}

{% page-ref page="../concepts-and-basics/binding-nodes-to-models.md" %}

