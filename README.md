# ArgsParser
A recreation of the GNU arguments parser written in C#

# Example

```
$ dotnet new console
```
```
<ItemGroup>
  <Reference Include="ArgsParser">
    <HintPath>ArgsParser.dll</HintPath>
  </Reference>
</ItemGroup>
```
```
using System;
using ArgsParserNS;

public class Program 
{
    public static void Main(string[] args)
    {
        ArgsParser argsParser = new ArgsParser();
        argsParser.RegisteredArguments.Add(new Argument {
            Name = "help",
            ShortName = "h"
        });
        FilledArgument[] parsedArgs = argsParser.ParseArguments(args);

        foreach (FilledArgument parsedArg in parsedArgs)
        {
            Console.WriteLine($"{parsedArg.Arg.Name} ({parsedArg.Arg.ShortName}): {parsedArg.Value}");
        }
    }
}
```
```
$ dotnet build
```
```
$ dotnet bin/Debug/net6.0/Example.dll --help
help (h):
```
```
$ dotnet bin/Debug/net6.0/Example.dll --help=AValue
help (h): AValue
```
```
$ dotnet bin/Debug/net6.0/Example.dll -h
help (h):
```
```
$ dotnet bin/Debug/net6.0/Example.dll -h=AValue
help (h): AValue
```
