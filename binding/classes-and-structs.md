# Classes and structs

### How it works

The binder starts off by creating an instance of the bound type with default values of public fields and properties \(the same way as `Activator.CreateInstance` does\) and then recursively binds the value of every field and property to a corresponding subsection of the settings tree. See [binding nodes to models](../concepts-and-basics/binding-nodes-to-models.md) page for a step-by-step illustration of this process.

Fields and properties don't have to be mutable: readonly fields and properties with private setters \(or even without one\) are fine.

Following members are **ignored**: indexers, constants, static and non-public fields and properties, computed properties without backing fields.

### Settings tree navigation

When binding a field or property value, the settings tree is [scoped](../concepts-and-basics/settings-nodes-scoping.md) to the member name. This imposes a requirement to synchronize naming in configuration data provided by [sources](../concepts-and-basics/configuration-sources.md) and models in the application code. In order to bind a model property named `Timeout` from a section of JSON file, this section must contain a property with the same name \(barring case\).

[Name aliases](../advanced-scenarios/use-name-aliases.md) allow to decouple property names from configuration data names.

### Required and optional members

By default all fields and properties are treated as optional: they are just left with default values if no data could be found in the settings tree. It's possible to [make members required](../basic-scenarios/make-settings-required.md) though. Required members with no data in the settings tree cause the binding process to fail and produce an exception.

### Model requirements

Model classes must have a parameterless constructor.

### Binder requirements

Binders are required for all public fields and properties.

### Node requirements

Only [object nodes](../concepts-and-basics/settings-nodes/object-nodes.md) are supported.

### Related pages

{% page-ref page="../concepts-and-basics/binding-nodes-to-models.md" %}

{% page-ref page="../basic-scenarios/make-settings-required.md" %}

{% page-ref page="../basic-scenarios/make-settings-secret.md" %}

{% page-ref page="../advanced-scenarios/use-name-aliases.md" %}

{% page-ref page="../advanced-scenarios/apply-custom-binders.md" %}

