<!--
GENERATED FILE - DO NOT EDIT
This file was generated by [MarkdownSnippets](https://github.com/SimonCropp/MarkdownSnippets).
Source File: /readme.source.md
To change this file edit the source file and then run MarkdownSnippets.
-->

This shows how to build a netcore3 console app, including all files needed to deploy to a system with netcore already installed.

This sample targets one dependency (NodaTime) for illustrative purposes


## Moving pieces


### Publish Profile


<!-- snippet: Win64.pubxml -->
<a id='snippet-Win64.pubxml'/></a>
```pubxml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PublishProtocol>FileSystem</PublishProtocol>
    <Configuration>Release</Configuration>
    <Platform>Any CPU</Platform>
    <TargetFramework>netcoreapp3.0</TargetFramework>
    <PublishDir>bin\Release\publish\</PublishDir>
    <PublishSingleFile>true</PublishSingleFile>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <SelfContained>false</SelfContained>
  </PropertyGroup>
</Project>
```
<sup>[snippet source](/src/MyConsole/Properties/PublishProfiles/Win64.pubxml#L1-L13) / [anchor](#snippet-Win64.pubxml)</sup>
<!-- endsnippet -->

dotnet publish MyConsole\MyConsole.csproj  /p:PublishProfile=Win64


## Final output

The full resultant file list

```
hostfxr.dll
hostpolicy.dll
MyConsole.deps.json
MyConsole.dll
MyConsole.exe
MyConsole.runtimeconfig.dev.json
MyConsole.runtimeconfig.json
NodaTime.dll
```

## Debug files

This project uses embedded symbols, so no pdb is created. However if a pdb is required, or it is necessary to include pdbs from referenced packages, consider using the [SourceLink.Copy.PdbFiles NuGet package](https://www.nuget.org/packages/SourceLink.Copy.PdbFiles/):

```xml
<PackageReference Include="SourceLink.Copy.PdbFiles" Version="2.8.3" PrivateAssets="All" />
```

See [dotnet/sdk/issues/1458](https://github.com/dotnet/sdk/issues/1458) for more information.

