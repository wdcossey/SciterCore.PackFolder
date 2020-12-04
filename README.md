#### SciterCore.PackFolder
PackFolder MSBuild Task(s) for embedding Sciter packed binaries into Project resources.

![Nuget](https://img.shields.io/nuget/v/SciterCore.PackFolder)

| Command                      |  Options                  |  Default  | Description                       |
| ---------------------------: | :------------------------ | :-------: | :-------------------------------- |
| `SciterCorePackType`         | `binary`                  | `binary`  | The PackFolder option; Only `binary` is currently supported, to disable folder packing use any other value (i.e `none`). |
| `SciterCorePackDirectory`    | absolute or relative path | `wwwroot` | Path to the folder you would like to pack.                                                                               |
| `SciterCorePackCopyToOutput` | `true` or `false`         | `false`   | Useful if you do not want to pack the files and simply want them copied to the `$(TargetDir)` during the build process.  |

Example:
```
<PropertyGroup>
  <SciterCorePackDirectory>..\common\wwwroot</SciterCorePackDirectory>
  <SciterCorePackType>binary</SciterCorePackType>
  <SciterCorePackCopyToOutput Condition=" '$(Configuration)' == 'Debug' ">true</SciterCorePackCopyToOutput>
</PropertyGroup>
```
