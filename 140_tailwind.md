# Blazorise Tailwind Usage

Quickly install Blazorise with Tailwind, one of the world's most popular Blazor UI framework.

Blazorise Tailwind provider is made possible with the help of Flowbite, an open-source Tailwind CSS Components.

Note: Before proceeding, ensure you have already created a Blazor project. If not, the simplest way to start with Blazorise is by using our Templates.

👀 Want to see it in action? Check out the
    Tailwind Demo here
    !

## Install Packages

First step is to install a Tailwind provider for Blazorise:

```
Install-Package Blazorise.Tailwind
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

### Using in Development

For development, you should use the JIT version of the CSS files. We have already included the necessary files in the Blazorise.Tailwind package.

Add these lines inside the  section:

```
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&amp;display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://unpkg.com/flowbite@1.5.4/dist/flowbite.min.css" />
<link href="_content/Blazorise.Icons.FontAwesome/v6/css/all.min.css" rel="stylesheet">

<script src="https://cdn.tailwindcss.com"></script>
<script src="_content/Blazorise.Tailwind/blazorise.tailwind.config.js?v=1.7.5.0"></script>

<link href="_content/Blazorise/blazorise.css?v=1.7.5.0" rel="stylesheet" />
<link href="_content/Blazorise.Tailwind/blazorise.tailwind.css?v=1.7.5.0" rel="stylesheet" />
```

In the same file add the following. It should be placed just before the default blazor script.

```
<script src="https://unpkg.com/flowbite@1.5.4/dist/flowbite.js"></script>
```

### Using in Production

For production, you should use the prebuilt version of the CSS files. We have already included the necessary files in the Blazorise.Tailwind package.

If you're interested in integrating Tailwind CSS with your Blazor projects, check out our blog post that guides you through the process of using Tailwind CSS with Blazor.

Add these lines inside the  section:

```
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&amp;display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://unpkg.com/flowbite@1.5.4/dist/flowbite.min.css" />
<link href="_content/Blazorise.Icons.FontAwesome/v6/css/all.min.css" rel="stylesheet">

<link href="_content/Blazorise/blazorise.css?v=1.7.5.0" rel="stylesheet" />
<link href="_content/Blazorise.Tailwind/blazorise.tailwind.prod.css?v=1.7.5.0" rel="stylesheet" />
```

Don't forget to remove Bootstrap JS and CSS files that comes with the default Blazor project template.

## Add Imports

In your main  add:

```
@using Blazorise
```

## Register Services

Add the following lines to the relevant sections of .

```
using Blazorise;
using Blazorise.Tailwind;
using Blazorise.Icons.FontAwesome;

builder.Services
    .AddBlazorise()
    .AddTailwindProviders()
    .AddFontAwesomeIcons();
```

## PWA &amp; Offline Support (optional)

For information about PWAs &amp; offline support, please take a look at our PWA docs.

###### On this page

#### 

## 