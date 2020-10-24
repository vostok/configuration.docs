# Print settings

**Requires**: [main module](../modules/configuration.md).

Settings models can be printed in JSON or YAML formats to generate configuration file examples.

```text
var printSettings = new PrintSettings 
{
    Format = PrintFormat.Json
};

var defaultSettings = new MySettings();

var printed = ConfigurationPrinter.Print(defaultSettings);

Console.Out.WriteLine(printed);
```



