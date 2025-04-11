# Blazorise Material Usage

Quickly install Blazorise with Material, one of the world's most popular Blazor UI framework.

Note: Before proceeding, ensure you have already created a Blazor project. If not, the simplest way to start with Blazorise is by using our Templates.

Since Material CSS is based on a Bootstrap you only need to change the CSS and JS sources. The code in
    \_Imports.razor will stay the same as for the Bootstrap provider.

👀 Want to see it in action? Check out the
    Material Demo here
    !

## Install Packages

First step is to install a Material provider for Blazorise:

```
Install-Package Blazorise.Material
```

You also need to install the icon package:

```
Install-Package Blazorise.Icons.Material
```

## Add Material CSS

Material CSS is not available through the CDN so you must download it yourself from  web page.
        After the download is finished you must extract the CSS and JS to the  folder inside of you Blazor project.

```
blazorproject.client/
└── wwwroot/
    ├── css/
    └── js/
```

## Add Static Files

Modify your project's HTML template to include the necessary CSS files. The files you add depend on whether you're working with a WebAssembly or Server project:

For WebAssembly, update index.html.
        

            For Server, update \_Layout.cshtml or \_Host.cshtml.
        

            For .NET 8, update App.razor.

Add these lines inside the  section:

```
<!-- Material CSS -->
<link href="css/material.min.css" rel="stylesheet">

<!-- Add Material font (Roboto) and Material icon as needed -->
<link href="https://fonts.googleapis.com/css?family=Roboto:300,300i,400,400i,500,500i,700,700i|Roboto+Mono:300,400,700|Roboto+Slab:300,400,700" rel="stylesheet">
<link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">

<link href="_content/Blazorise/blazorise.css?v=1.7.5.0" rel="stylesheet" />
<link href="_content/Blazorise.Material/blazorise.material.css?v=1.7.5.0" rel="stylesheet" />
<link href="_content/Blazorise.Icons.Material/blazorise.icons.material.css?v=1.7.5.0" rel="stylesheet" />

<!-- Optional JavaScript -->
<!-- These are the standard js dependencies this provider typically dependes upon, but Blazorise deems these as optional as Blazorise Components should work correctly without these  -->
<!-- jQuery first, then Popper.js, then Material JS -->
<script src="https://code.jquery.com/jquery-3.5.0.slim.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.1/js/bootstrap.min.js"></script>

<!-- Mandatory JavaScript -->
<script src="js/material.min.js"></script>
<script src="_content/Blazorise.Material/blazorise.material.js?v=1.7.5.0"></script>
```

Don't forget to remove bootstrap JS and CSS files that comes with the default Blazor project template.

## Add Imports

In your main  add:

```
@using Blazorise
```

## Register Services

Add the following lines to the relevant sections of .

```
using Blazorise;
using Blazorise.Material;
using Blazorise.Icons.Material;

builder.Services
    .AddBlazorise( options =>
    {
        options.Immediate = true;
    } )
    .AddMaterialProviders()
    .AddMaterialIcons();
```

## PWA &amp; Offline Support (optional)

For information about PWAs &amp; offline support, please take a look at our PWA docs.

###### On this page

#### 

## 