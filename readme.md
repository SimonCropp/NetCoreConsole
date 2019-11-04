<!--
GENERATED FILE - DO NOT EDIT
This file was generated by [MarkdownSnippets](https://github.com/SimonCropp/MarkdownSnippets).
Source File: /readme.source.md
To change this file edit the source file and then run MarkdownSnippets.
-->

This shows how to use the various publish profile options when building a netcore 3 console app.

<!-- toc -->
## Contents

  * [Console project settings](#console-project-settings)
  * [Publish Profiles](#publish-profiles)
    * [Default](#default)
    * [Framework Dependent](#framework-dependent)
    * [Single-File Exe](#single-file-exe)
    * [Single Exe and Framework Dependent](#single-exe-and-framework-dependent)
    * [Trimmed](#trimmed)
    * [Single Exe and Trimmed](#single-exe-and-trimmed)
  * [ReadyToRun images](#readytorun-images)
  * [Further Reading](#further-reading)
<!-- endtoc -->



## Console project settings

 * This sample references and makes use of NodaTime to illustrate a dependency being consumed.
 * This sample references, but does not use, Newtonsoft for illustrate a dependency being trimmed.
 * The [Runtime IDentifier](https://docs.microsoft.com/en-us/dotnet/core/rid-catalog) is hard coded to `win-x64`. All profiles will inherit this setting.
 * `AppendRuntimeIdentifierToOutputPath` and `AppendTargetFrameworkToOutputPath` are disabled to simplify the resulting directory structure. See [Change the build output directory](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-change-the-build-output-directory)

<!-- snippet: MyConsole.csproj -->
<a id='snippet-MyConsole.csproj'/></a>
```csproj
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
    <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
    <TargetLatestRuntimePatch>true</TargetLatestRuntimePatch>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
  </PropertyGroup>
  <ItemGroup>
    <Content Include="ContentFile.txt">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </Content>
    <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
    <PackageReference Include="NodaTime" Version="2.4.7" />
    <PackageReference Include="System.Configuration.ConfigurationManager" Version="4.6.0" />
  </ItemGroup>
</Project>
```
<sup>[snippet source](/src/MyConsole/MyConsole.csproj#L1-L18) / [anchor](#snippet-MyConsole.csproj)</sup>
<!-- endsnippet -->


## Publish Profiles

Publish profiles are located in [src/MyConsole/Properties/PublishProfiles](/src/MyConsole/Properties/PublishProfiles)


### Default

Uses the default publish profile settings:

<!-- snippet: Default.pubxml -->
<a id='snippet-Default.pubxml'/></a>
```pubxml
<Project>
  <PropertyGroup>
    <PublishDir>bin\Release\publish\Default\</PublishDir>
  </PropertyGroup>
</Project>
```
<sup>[snippet source](/src/MyConsole/Properties/PublishProfiles/Default.pubxml#L1-L5) / [anchor](#snippet-Default.pubxml)</sup>
<!-- endsnippet -->

<!--
include: Default
path: C:\Code\NetCoreConsole\src\includes\Default.include.md
-->

 * Files: 234
 * Size: 67.86 MB

Publish Command:

```
dotnet publish MyConsole\MyConsole.csproj -c Release /p:PublishProfile=Default
```


### Framework Dependent

Same as the [Default](#default) but makes it [Framework-dependent](https://docs.microsoft.com/en-us/dotnet/core/deploying/#framework-dependent-deployments-fdd):

<!-- snippet: Fdd.pubxml -->
<a id='snippet-Fdd.pubxml'/></a>
```pubxml
<Project>
  <PropertyGroup>
    <PublishDir>bin\Release\publish\Fdd\</PublishDir>
    <SelfContained>false</SelfContained>
  </PropertyGroup>
</Project>
```
<sup>[snippet source](/src/MyConsole/Properties/PublishProfiles/Fdd.pubxml#L1-L6) / [anchor](#snippet-Fdd.pubxml)</sup>
<!-- endsnippet -->

<!--
include: Fdd
path: C:\Code\NetCoreConsole\src\includes\Fdd.include.md
-->

 * Files: 14
 * Size: 2.21 MB

Notes:

 * Depends on an installed runtime.

Publish Command:

```
dotnet publish MyConsole\MyConsole.csproj -c Release /p:PublishProfile=Fdd
```


### Single-File Exe

Same as [Default](#default) but creates a [Single-file executables](https://docs.microsoft.com/en-us/dotnet/core/whats-new/dotnet-core-3-0#single-file-executables):

<!-- snippet: SingleExe.pubxml -->
<a id='snippet-SingleExe.pubxml'/></a>
```pubxml
<Project>
  <PropertyGroup>
    <PublishDir>bin\Release\publish\SingleExe\</PublishDir>
    <PublishSingleFile>true</PublishSingleFile>
  </PropertyGroup>
</Project>
```
<sup>[snippet source](/src/MyConsole/Properties/PublishProfiles/SingleExe.pubxml#L1-L6) / [anchor](#snippet-SingleExe.pubxml)</sup>
<!-- endsnippet -->

<!--
include: SingleExe
path: C:\Code\NetCoreConsole\src\includes\SingleExe.include.md
-->

 * Files: 1
 * Size: 67.87 MB

Publish Command:

```
dotnet publish MyConsole\MyConsole.csproj -c Release /p:PublishProfile=SingleExe
```


### Single Exe and Framework Dependent

Combines [Single-File Exe](#single-file-exe) and [Framework Dependent](#framework-dependent):

<!-- snippet: SingleExeFdd.pubxml -->
<a id='snippet-SingleExeFdd.pubxml'/></a>
```pubxml
<Project>
  <PropertyGroup>
    <PublishDir>bin\Release\publish\SingleExeFdd\</PublishDir>
    <PublishSingleFile>true</PublishSingleFile>
    <SelfContained>false</SelfContained>
  </PropertyGroup>
</Project>
```
<sup>[snippet source](/src/MyConsole/Properties/PublishProfiles/SingleExeFdd.pubxml#L1-L7) / [anchor](#snippet-SingleExeFdd.pubxml)</sup>
<!-- endsnippet -->

<!--
include: SingleExeFdd
path: C:\Code\NetCoreConsole\src\includes\SingleExeFdd.include.md
-->

 * Files: 1
 * Size: 2.22 MB

Notes:

 * Depends on an installed runtime.

Publish Command:

```
dotnet publish MyConsole\MyConsole.csproj -c Release /p:PublishProfile=SingleExeFdd
```


### Trimmed

Same as the [Default](#default) but uses [assembly-linking](https://docs.microsoft.com/en-us/dotnet/core/whats-new/dotnet-core-3-0#assembly-linking):

<!-- snippet: Trimmed.pubxml -->
<a id='snippet-Trimmed.pubxml'/></a>
```pubxml
<Project>
  <PropertyGroup>
    <PublishDir>bin\Release\publish\Trimmed\</PublishDir>
    <PublishTrimmed>true</PublishTrimmed>
  </PropertyGroup>
</Project>
```
<sup>[snippet source](/src/MyConsole/Properties/PublishProfiles/Trimmed.pubxml#L1-L6) / [anchor](#snippet-Trimmed.pubxml)</sup>
<!-- endsnippet -->

<!--
include: Trimmed
path: C:\Code\NetCoreConsole\src\includes\Trimmed.include.md
-->

 * Files: 124
 * Size: 36.61 MB

Publish Command:

```
dotnet publish MyConsole\MyConsole.csproj -c Release /p:PublishProfile=Trimmed
```


### Single Exe and Trimmed

Combines [Single-File Exe](#single-file-exe) and [Trimmed](#trimmed):

<!-- snippet: SingleExeTrimmed.pubxml -->
<a id='snippet-SingleExeTrimmed.pubxml'/></a>
```pubxml
<Project>
  <PropertyGroup>
    <PublishDir>bin\Release\publish\SingleExeTrimmed\</PublishDir>
    <PublishSingleFile>true</PublishSingleFile>
    <PublishTrimmed>true</PublishTrimmed>
  </PropertyGroup>
</Project>
```
<sup>[snippet source](/src/MyConsole/Properties/PublishProfiles/SingleExeTrimmed.pubxml#L1-L7) / [anchor](#snippet-SingleExeTrimmed.pubxml)</sup>
<!-- endsnippet -->

<!--
include: SingleExeTrimmed
path: C:\Code\NetCoreConsole\src\includes\SingleExeTrimmed.include.md
-->

 * Files: 1
 * Size: 36.62 MB

Publish Command:

```
dotnet publish MyConsole\MyConsole.csproj -c Release /p:PublishProfile=SingleExeTrimmed
```


## ReadyToRun images

ReadyToRun images (`<PublishReadyToRun>true</PublishReadyToRun>`) are not covered in the above scenarios, but should be considered as an option for production apps.

> R2R binaries improve startup performance by reducing the amount of work the JIT needs to do as your application is loading. The binaries contain similar native code as what the JIT would produce, giving the JIT a bit of a vacation when performance matters most (at startup). R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code, to improve startup. - https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/


## Further Reading

 * [Announcing .NET Core 3.0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/)
 * [What's new in .NET Core 3.0](https://docs.microsoft.com/en-us/dotnet/core/whats-new/dotnet-core-3-0)
 * [Making a tiny .NET Core 3.0 entirely self-contained single executable - Scott Hanselman](https://www.hanselman.com/blog/MakingATinyNETCore30EntirelySelfcontainedSingleExecutable.aspx)
 * [Create a Trimmed Self-Contained Single Executable in .NET Core 3.0](https://www.talkingdotnet.com/create-trimmed-self-contained-executable-in-net-core-3-0/)
