# Blazorise Bootstrap 5 Usage

Quickly install Blazorise with Bootstrap 5, one of the world's most popular Blazor UI framework.

Note: Before proceeding, ensure you have already created a Blazor project. If not, the simplest way to start with Blazorise is by using our Templates.

👀 Want to see it in action? Check out the
    Bootstrap 5 Demo here
    !

## Install Packages

First step is to install a Bootstrap provider for Blazorise:

```
Install-Package Blazorise.Bootstrap5
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
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
<link href="_content/Blazorise.Icons.FontAwesome/v6/css/all.min.css" rel="stylesheet">

<link href="_content/Blazorise/blazorise.css?v=1.7.5.0" rel="stylesheet" />
<link href="_content/Blazorise.Bootstrap5/blazorise.bootstrap5.css?v=1.7.5.0" rel="stylesheet" />
```

When Blazor project is created it will also include it’s own 
        and  files that can sometime be of older versions. To ensure we’re using the appropriate
        Bootstrap and FontAwesome files, you need to remove them or replace them with the links from above. If you forget to
        remove them, it’s possible that some components will not work as expected. Also, the links provided here might not always be the most up to date.
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
using Blazorise.Bootstrap5;
using Blazorise.Icons.FontAwesome;

builder.Services
    .AddBlazorise( options =>
    {
        options.Immediate = true;
    } )
    .AddBootstrap5Providers()
    .AddFontAwesomeIcons();
```

## PWA &amp; Offline Support (optional)

For information about PWAs &amp; offline support, please take a look at our PWA docs.

###### On this page

#### 

## 