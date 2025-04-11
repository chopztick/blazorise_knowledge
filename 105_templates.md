# Blazorise Templates Guide

The Blazorise Templates allows you to quickly setup a Blazor project of your choice (Server or WebAssembly),
    with any of our Providers, and with a default starting look.

The Blazorise Templates are based on the dotnet templates feature.

## Install packages

You do so by using the CLI  feature.

```
dotnet new install Blazorise.Templates
```

### Versioning

We use our Templates versioning to match &amp; install the latest corresponding Blazorise major &amp; minor version.

For example:

Blazorise.Templates: 1.1.* will always try to install the latest 1.1 Blazorise
                

                    Blazorise.Templates: 1.2.* will always try to install the latest 1.2 Blazorise
                

                    Blazorise.Templates: 1.3.* will always try to install the latest 1.3 Blazorise
                

                    and so on...

If you want to install a specific version, you may do so by passing in the desired version.

```
dotnet new install Blazorise.Templates::1.1.0
```

## Create New Project

With Blazorise.Templates installed you may now use the CLI or the Visual Studio IDE to create your new Blazorise solution!

Both options provide you with several parameters to create a new Blazorise solution. In this document you will find some sample commands to create your customized solution.

### CLI

Blazorise CLI is the fastest way to start a new solution with the Blazorise components.

The new blazorise command creates a Blazorise solution or other artifacts based on an Blazorise template. Take note that you may ommit the options and the defaults for those will be considered.

```
dotnet new blazorise -n MyNewBlazoriseApp -p Bootstrap5 -bh Server -ut false -f net7.0
```

### Visual Studio IDE

When creating a new Project, you will find a new Project Type, .

After choosing the project type you will be presented with extra options to customize your project.

## Options

| Name              | Description                                                       | Type   | Default   |
|-------------------|-------------------------------------------------------------------|--------|-----------|
| -f                | The target framework for the project.                               net6.0                                       net7.0                                       net8.0                                       net9.0                                                                   | Choice | net7.0    |
| -bh               | Specifies the project blazor host type.                               Server                                       WebAssembly                                       WebApp                      (It is of note that this option mirrors the new .NET8 blazor web app template with the RenderMode feature and is adapted to work with Blazorise, and as such is only supported in .NET8)                                                                   | Choice | Server    |
| -p                | Specifies the Blazorise CSS provider that will be used to render components.                               Bootstrap4                                       Bootstrap5                                       Tailwind                                       Material                                       AntDesign                                       Bulma                                       FluentUI2                                                                   | Choice | Server    |
| -ut               | Whether the program entry point, should use top level statements. | bool   | true      |
| -tcolor-primary   | The Theme's starting primary color.                               | string | #0288D1   |
| -tcolor-secondary | The Theme's starting secondary color.                             | string | #A65529   |
| -tcolor-success   | The Theme's starting success color.                               | string | #23C02E   |
| -tcolor-info      | The Theme's starting info color.                                  | string | #9BD8FE   |
| -tcolor-warning   | The Theme's starting warning color.                               | string | #F8B86C   |
| -tcolor-danger    | The Theme's starting danger color.                                | string | #F95741   |
| -tcolor-light     | The Theme's starting light color.                                 | string | #F0F0F0   |
| -tcolor-dark      | The Theme's starting dark color.                                  | string | #535353   |

###### On this page

#### 

## 