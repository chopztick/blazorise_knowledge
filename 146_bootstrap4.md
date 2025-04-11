# Blazorise Bootstrap 4 Usage

Quickly install Blazorise with Bootstrap 4, one of the world's most popular Blazor UI framework.

Note: Before proceeding, ensure you have already created a Blazor project. If not, the simplest way to start with Blazorise is by using our Templates.

👀 Want to see it in action? Check out the
    Bootstrap 4 Demo here
    !

## Install Packages

First step is to install a Bootstrap provider for Blazorise:

```
Install-Package Blazorise.Bootstrap
```

You also need to install the icon package:

```
Install-Package Blazorise.Icons.FontAwesome
```

## Add Static Files

Modify your project's HTML template to include the necessary CSS files. The files you add depend on whether you're working with a WebAssembly or Server project:

For WebAssembly, update index.html.
        

            For Server, update \_Layout.cshtml or \_Host.cshtml.
        

            For .NET 8, update App.razor.

Add these lines inside the  section:

```
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.6.1/dist/css/bootstrap.min.css" integrity="sha384-zCbKRCUGaJDkqS1kPbPd7TveP5iyJE0EjAuZQTgFLD2ylzuqKfdKlfG/eSrtxUkn" crossorigin="anonymous">
<link href="_content/Blazorise.Icons.FontAwesome/v6/css/all.min.css" rel="stylesheet">

<link href="_content/Blazorise/blazorise.css?v=1.7.5.0" rel="stylesheet" />
<link href="_content/Blazorise.Bootstrap/blazorise.bootstrap.css?v=1.7.5.0" rel="stylesheet" />
```

When Blazor project is created it will also include it’s own 
        and  files that can sometime be of older versions. To ensure we’re using the appropriate
        Bootstrap and FontAwesome files, you need remove them or replace them with the links from above. If you forget to
        remove them it’s possible that some components will not work as expected. Also, the links provided here might not always be the most up to date.
        You may update your sources, but do take note, that  has been tested with the versions listed here.

## Add Imports

In your main  add:

```
@using Blazorise
```

## Register Services

Add the following lines to the relevant sections of .

```
using Blazorise;
using Blazorise.Bootstrap;
using Blazorise.Icons.FontAwesome;

builder.Services
    .AddBlazorise( options =>
    {
        options.Immediate = true;
    } )
    .AddBootstrapProviders()
    .AddFontAwesomeIcons();
```

## PWA &amp; Offline Support (optional)

For information about PWAs &amp; offline support, please take a look at our PWA docs.

###### On this page

#### 

## 