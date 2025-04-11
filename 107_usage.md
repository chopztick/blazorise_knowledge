# Blazorise Integration Guides

Get started with the only UI component library for Blazor that can work with the most popular CSS framework.

## Introduction

Blazorise is the only Blazor UI components library offering development independent of CSS frameworks, exclusively using C#, with support for CSS frameworks like Bootstrap, Tailwind, Bulma, AntDesign, Fluent 2, and Material.

We achieve this through intelligently rendering the precise HTML and CSS needed for the underlying CSS framework.

It includes all of the commonly used components that a website requires, such as buttons, dropdowns, navigation bars, modals, but also some more advanced interactive elements such as datepickers.

## Supported CSS Providers

Blazorise is build as an abstration layer that can work with the most popular CSS frameworks. You can choose the one that fits your needs the best.

<!-- image -->

##### Bootstrap 4

<!-- image -->

##### Bootstrap 5

<!-- image -->

##### Tailwind

<!-- image -->

##### Material

<!-- image -->

##### Ant Design

<!-- image -->

##### Bulma

<!-- image -->

##### Fluent 2

## Components naming convention

Blazorise follows the ASP.NET Core Razor naming convention for components. See: ASP.NET Core Razor components

This means, that when you encounter a similar named Html and Blazorise component, the Blazorise component will be distinguished by the starting upper-case letter.
    For example:
    HTML dropdown list : &lt;select&gt;...&lt;/select&gt;
Blazorise dropdown list: &lt;Select&gt;...&lt;/Select&gt;

## Empty provider

Generally you will always want to use and register one of the provided CSS frameworks. But in the case that you
    only want to use any of the custom Blazorise extensions, like for example: Chart or Sidebar, you can register an “Empty” provider.
    This way the extensions will still work but the default Blazorise components will be unused.

```
public void ConfigureServices( IServiceCollection services )
{
  services
    .AddEmptyProviders();
}
```

## Testing with bUnit

For testing purposes, there is currently an internal Blazorise Service that should be configured as Transient so the bUnit test engine does not throw an error.
    You should add this setup:
    ctx.Services.AddBlazorise().Replace(ServiceDescriptor.Transient&lt;IComponentActivator, ComponentActivator&gt;());

    Other than that it should pretty much work out of the box. Let us know if you're having any difficulties.
    For some testing examples, you can look at some of our tests.

## Javascript resources

Blazorise loads any additional JavaScript it needs dynamically once a component needs it.
    This means that Blazorise expects that the resources are available and placed relative to the app root.
    You can configure this by using the app.UseStaticFiles(); and it does not need any other additional configuration from your part. If you're having any difficulties,
    please refer to the following issues:

- #3122
- #3150

## PWA &amp; Offline Support

For information about PWAs &amp; offline support, please take a look at our PWA docs.

###### On this page

#### 

## 