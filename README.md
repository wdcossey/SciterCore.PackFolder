## SciterCore.PackFolder
PackFolder MSBuild Task(s) for embedding Sciter packed binaries into Project resources.

[![Build status](https://dev.azure.com/wdcossey/SciterCore/_apis/build/status/SciterCore.PackFolder-import)](https://dev.azure.com/wdcossey/SciterCore/_build/latest?definitionId=12)
[![Nuget](https://img.shields.io/nuget/v/SciterCore.PackFolder)](https://www.nuget.org/packages/SciterCore.PackFolder/)

| Command                      |  Options                  |  Default  | Description                       |
| ---------------------------: | :------------------------ | :-------: | :-------------------------------- |
| `SciterCorePackType`         | `binary`                  | `binary`  | The PackFolder option; Only `binary` is currently supported, to disable folder packing use any other value (i.e `none`). |
| `SciterCorePackDirectory`    | absolute or relative path | `wwwroot` | Path to the folder you would like to pack.                                                                               |
| `SciterCorePackCopyToOutput` | `true` or `false`         | `false`   | Useful if you do not want to pack the files and simply want them copied to the `$(TargetDir)` during the build process.  |

#### Notes:

Unlike Sciter[Sharp], the default directory used for packing/copying is `wwwroot` (like `ASP.Net Core`), this can be modified using the `SciterCorePackDirectory` option.

Example(s):

1. Default settings

```
<PropertyGroup>
  <SciterCorePackDirectory>wwwroot</SciterCorePackDirectory>
  <SciterCorePackType>binary</SciterCorePackType>
  <SciterCorePackCopyToOutput>false</SciterCorePackCopyToOutput>
</PropertyGroup>
```

2. Packs the folder located at `$(ProjectDir)..\common\wwwroot`, using `binary` packing option, conditionally copying the specified folder to the output directory (when debugging)

```
<PropertyGroup>
  <SciterCorePackDirectory>..\common\wwwroot</SciterCorePackDirectory>
  <SciterCorePackType>binary</SciterCorePackType>
  <SciterCorePackCopyToOutput Condition=" '$(Configuration)' == 'Debug' ">true</SciterCorePackCopyToOutput>
</PropertyGroup>
```

3. Copies the folder located at `$(ProjectDir)res` to the output directory w/o packing

```
<PropertyGroup>
  <SciterCorePackDirectory>res</SciterCorePackDirectory>
  <SciterCorePackType>none</SciterCorePackType>
  <SciterCorePackCopyToOutput>true</SciterCorePackCopyToOutput>
</PropertyGroup>
```

