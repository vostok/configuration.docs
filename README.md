# Home

## Vostok.Configuration in a nutshell

Vostok.Configuration is a [set](modules/) of libraries offering configuration tools to .NET applications. It handles fetching configuration data from files or APIs, parsing and converting it to user-defined model classes.

## Guiding design principles

* **Configuration data sources should be composable regardless of storage formats**.

  * It should be easy to combine settings from JSON files, environment variables and custom APIs. This is achieved with [configuration source](concepts-and-basics/configuration-sources.md) concept and universal [settings nodes](concepts-and-basics/settings-nodes/) abstraction. 

* **"Hot" configuration updates should be easy to leverage**. 

  * Hot configuration implies handling changes in settings without application restart. This is enabled by explicitly reactive [source](concepts-and-basics/configuration-sources.md) design and [settings provider methods](concepts-and-basics/configuration-provider.md).

* **Rich object models should be supported for user convenience**.

  * [Binding](concepts-and-basics/binding-nodes-to-models.md) process supports a wide range of [primitives](binding/primitives.md), [collections](binding/collections.md), [classes](binding/classes-and-structs.md), [interfaces](advanced-scenarios/use-dynamic-interfaces.md) and employs a number of conventions for arbitrary types \(anything with a `TryParse` method works\).

* **It should be possible to extend the library with arbitrary data sources and object models**.

  * Two major extensions points are [custom configuration sources](advanced-scenarios/create-custom-sources.md) and [binders](advanced-scenarios/apply-custom-binders.md).

## Features

* [On-demand](basic-scenarios/obtain-settings-from-provider.md) and [subscription-based](basic-scenarios/observe-settings-via-provider.md) methods to obtain settings;

* Support for [required](basic-scenarios/make-settings-required.md) and [secret](basic-scenarios/make-settings-secret.md) settings;

* Support for custom settings [validation](advanced-scenarios/apply-custom-validators.md);

* Wide selection of [built-in sources](sources/);

* Composable [binders](concepts-and-basics/binding-nodes-to-models.md);

* Sources can be [combined](basic-scenarios/combine-sources.md), [navigated](basic-scenarios/scope-sources.md) and [transformed](advanced-scenarios/transform-sources.md);

* [Integration]() with Microsoft configuration system;

## Guarantees

See [obtain](basic-scenarios/obtain-settings-from-provider.md) / [observe](basic-scenarios/observe-settings-via-provider.md) settings scenarios, [caching](concepts-and-basics/caching-and-performance.md) and [error handling](concepts-and-basics/error-handling.md) sections for details.

## Good starting points

{% page-ref page="quickstart.md" %}

{% page-ref page="concepts-and-basics/" %}

{% page-ref page="basic-scenarios/" %}

{% page-ref page="modules/" %}

