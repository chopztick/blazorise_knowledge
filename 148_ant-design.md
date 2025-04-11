# Blazorise Ant Design Usage

Quickly install Blazorise with Ant Design, one of the world's most popular Blazor UI framework.

Note: Before proceeding, ensure you have already created a Blazor project. If not, the simplest way to start with Blazorise is by using our Templates.

👀 Want to see it in action? Check out the
    Ant Design Demo here
    !

## Install Packages

First step is to install a AntDesign provider for Blazorise:

```
Install-Package Blazorise.AntDesign
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
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/antd/4.24.15/antd.min.css" integrity="sha512-Ac6zlwN6S+uQSinFAcV27Gd/TtKEDt7XWXn2xWO4Xi9dTbbpT9/vJb+VT5af6nZywrgBD3qUFTb5y1VN4YD94Q==" crossorigin="anonymous" referrerpolicy="no-referrer" />
<link href="_content/Blazorise.Icons.FontAwesome/v6/css/all.min.css?v=1.7.5.0" rel="stylesheet">

<link href="_content/Blazorise/blazorise.css?v=1.7.5.0" rel="stylesheet" />
<link href="_content/Blazorise.AntDesign/blazorise.antdesign.css?v=1.7.5.0" rel="stylesheet" />
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
using Blazorise.AntDesign;
using Blazorise.Icons.FontAwesome;

builder.Services
    .AddBlazorise( options =>
    {
        options.Immediate = true;
    } )
    .AddAntDesignProviders()
    .AddFontAwesomeIcons();
```

## PWA &amp; Offline Support (optional)

For information about PWAs &amp; offline support, please take a look at our PWA docs.

###### On this page

#### 

## 