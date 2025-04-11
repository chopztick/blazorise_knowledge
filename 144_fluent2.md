# Blazorise Fluent 2 Usage Guide

Quickly install Blazorise with Fluent 2 design system, one of the world's most popular Blazor UI framework.

Welcome to the quick start guide for integrating the Blazorise Fluent 2 design system into your Blazor applications. Blazorise is among the most popular UI frameworks for Blazor, and with the Fluent 2 provider, you can leverage the modern and intuitive design language of Microsoft's Fluent 2.

Note: Before proceeding, ensure you have already created a Blazor project. If not, the simplest way to start with Blazorise is by using our Templates.

👀 Want to see it in action? Check out the
    Fluent 2 Demo here
    !

## Installation Steps

### 1. Install Required Packages

To integrate Fluent 2 design with Blazorise, you need to install two NuGet packages:

Fluent 2 Provider for Blazorise:

```
Install-Package Blazorise.FluentUI2
```

Fluent Icon Package for Blazorise:

```
Install-Package Blazorise.Icons.FluentUI
```

### 2. Include Static Files

Modify your project's HTML template to include the necessary CSS files. The files you add depend on whether you're working with a WebAssembly or Server project:

For WebAssembly, update index.html.
        

            For Server, update \_Layout.cshtml or \_Host.cshtml.
        

            For .NET 8, update App.razor.

Add these lines inside the  section:

```
<link href="_content/Blazorise.Icons.FluentUI/FluentSystemIcons-Resizable.css?v=1.7.5.0" rel="stylesheet" />

<link href="_content/Blazorise/blazorise.css?v=1.7.5.0" rel="stylesheet" />
<link href="_content/Blazorise.FluentUI2/reboot.css?v=1.7.5.0" rel="stylesheet" />
<link href="_content/Blazorise.FluentUI2/blazorise.fluentui2.css?v=1.7.5.0" rel="stylesheet" />
```

Remove any Bootstrap JS and CSS references that come by default with the Blazor project template to avoid conflicts.

### 3. Update Imports

In the  file at the root of your project, add the following namespace declarations:

```
@using Blazorise
```

### 4. Register Blazorise Services

Configure your  to register Blazorise services, including the Fluent 2 providers and icons:

```
using Blazorise;
using Blazorise.FluentUI2;
using Blazorise.Icons.FluentUI;

builder.Services
    .AddBlazorise()
    .AddFluentUI2Providers()
    .AddFluentUIIcons();
```

## Optional: PWA &amp; Offline Support

To enhance your application with Progressive Web App (PWA) capabilities and offline support, refer to our PWA documentation. This step is optional but recommended for applications intended to offer a rich, offline-capable user experience.

###### On this page

#### 

## 