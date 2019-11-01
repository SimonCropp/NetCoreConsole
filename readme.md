<!--
GENERATED FILE - DO NOT EDIT
This file was generated by [MarkdownSnippets](https://github.com/SimonCropp/MarkdownSnippets).
Source File: /readme.source.md
To change this file edit the source file and then run MarkdownSnippets.
-->

This shows how to build a netcore3 console app, including all files needed to deploy to a system with netcore already installed.

This sample targets one dependency (NodaTime) for illustrative purposes

<!-- toc -->
## Contents

  * [Publish Profile](#publish-profile)
    * [Default](#default)
    * [Framework Dependent](#framework-dependent)
    * [Single Exe](#single-exe)
    * [Single Exe and Framework Dependent](#single-exe-and-framework-dependent)
    * [Default Trimmed](#default-trimmed)
<!-- endtoc -->



## Publish Profile


### Default

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

~250 files
~70MB

```
dotnet publish MyConsole\MyConsole.csproj  /p:PublishProfile=Default
```


### Framework Dependent

<!-- snippet: Fwd.pubxml -->
<a id='snippet-Fwd.pubxml'/></a>
```pubxml
<Project>
  <PropertyGroup>
    <PublishDir>bin\Release\publish\Fwd\</PublishDir>
    <SelfContained>false</SelfContained>
  </PropertyGroup>
</Project>
```
<sup>[snippet source](/src/MyConsole/Properties/PublishProfiles/Fwd.pubxml#L1-L6) / [anchor](#snippet-Fwd.pubxml)</sup>
<!-- endsnippet -->

~5 files
~600KB

```
dotnet publish MyConsole\MyConsole.csproj  /p:PublishProfile=Fwd
```


### Single Exe

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

~1 file
~70MB

```
dotnet publish MyConsole\MyConsole.csproj  /p:PublishProfile=SingleExe
```


### Single Exe and Framework Dependent

<!-- snippet: SingleExeFwd.pubxml -->
<a id='snippet-SingleExeFwd.pubxml'/></a>
```pubxml
<Project>
  <PropertyGroup>
    <PublishDir>bin\Release\publish\SingleExeFwd\</PublishDir>
    <PublishSingleFile>true</PublishSingleFile>
    <SelfContained>false</SelfContained>
  </PropertyGroup>
</Project>
```
<sup>[snippet source](/src/MyConsole/Properties/PublishProfiles/SingleExeFwd.pubxml#L1-L7) / [anchor](#snippet-SingleExeFwd.pubxml)</sup>
<!-- endsnippet -->

~1 file
~600KB

```
dotnet publish MyConsole\MyConsole.csproj  /p:PublishProfile=SingleExeFwd
```


### Default Trimmed

<!-- snippet: DefaultTrimmed.pubxml -->
<a id='snippet-DefaultTrimmed.pubxml'/></a>
```pubxml
<Project>
  <PropertyGroup>
    <PublishDir>bin\Release\publish\DefaultTrimmed\</PublishDir>
    <PublishTrimmed>true</PublishTrimmed>
  </PropertyGroup>
</Project>
```
<sup>[snippet source](/src/MyConsole/Properties/PublishProfiles/DefaultTrimmed.pubxml#L1-L6) / [anchor](#snippet-DefaultTrimmed.pubxml)</sup>
<!-- endsnippet -->

~225 files
~55MB

```
dotnet publish MyConsole\MyConsole.csproj  /p:PublishProfile=DefaultTrimmed
```

