# Blazorise Theming

Customize Blazorise with your theme. You can change the colors, the typography and much more.

## Overview

Easily change the colors of your application programmatically. Rebuild the default stylesheet and customize various
    aspects of the framework for your particular needs.

Blazorise offers its own theme provider to control your application look and feel. Generally, if you stick
    to the built-in provider(s) and it’s CSS classes and variants, there isn’t anything else you need to do to
    use a custom theme with Blazorise. It just works. But we also make coloring outside the lines easy to do.

## Setup

To prepare your application for theming you need to wrap your root component with the ThemeProvider component tag.
    The best option is to add it to the App.razor where you wrap the Router tag with the ThemeProvider tag.
    Next you must set the Theme attribute where you can configure colors, borders, , paddings etc.

If no properties are specified, default settings will be used.

```
<Blazorise.ThemeProvider Theme="@theme">
    <Router AppAssembly="typeof(App).Assembly">
        <Found>...</Found>
        <NotFound>...</NotFound>
    </Router>
</Blazorise.ThemeProvider>
```

```
@code{
    private Theme theme = new Theme
    {
        // theme settings
    };
}
```

What this little peace of code is doing behind the scene? Basically it’s generating a fully customized CSS
    and styles based on the setting provided in the Theme attribute. It will also generate for you a list of CSS
    variables that you can use later if you want to expand your applications styles even further. The things like
    colors and element settings will be saved as CSS variables to the :root.

### Changing at runtime

To dynamically change theme settings you can use  from anywhere in your application.

```
<Button Clicked="@(()=>OnThemeColorChanged("#d16f9e"))">Change theme</Button>
```

```
@code{
    Task OnThemeColorChanged( string value )
    {
        if ( Theme?.ColorOptions != null )
            Theme.ColorOptions.Primary = value;

        if ( Theme?.BackgroundOptions != null )
            Theme.BackgroundOptions.Primary = value;

        Theme.ThemeHasChanged();

        return Task.CompletedTask;
    }

    [CascadingParameter] Theme Theme { get; set; }
}
```

### Colors

With  you can customize your application variant colors. Note that colors must be defined in hex format!

```
<Blazorise.ThemeProvider Theme="@theme">
    <Router AppAssembly="typeof(App).Assembly">
        <Found>...</Found>
        <NotFound>...</NotFound>
    </Router>
</Blazorise.ThemeProvider>
```

```
@code{
    private Theme theme = new Theme
    {
        ColorOptions = new ThemeColorOptions
        {
            Primary = "#45B1E8",
            Secondary = "#A65529",
            // other
        }
    };
}
```

### Gradients

Enables the gradient background colors.

```
<Blazorise.ThemeProvider Theme="@theme">
    <Router AppAssembly="typeof(App).Assembly">
        <Found>...</Found>
        <NotFound>...</NotFound>
    </Router>
</Blazorise.ThemeProvider>
```

```
@code {
    private Theme theme = new Theme
    {
        IsGradient = true,
    };
}
```

### Border Radius

Globally enable or disable rounded elements.

```
<Blazorise.ThemeProvider Theme="@theme">
    <Router AppAssembly="typeof(App).Assembly">
        <Found>...</Found>
        <NotFound>...</NotFound>
    </Router>
</Blazorise.ThemeProvider>
```

```
@code{
    private Theme theme = new Theme
    {
        IsRounded = false,
    };
}
```

### Body Theming

You can also apply some basic styles to the  element.

## API

See the documentation below for a complete reference to all of the props and classes available to the components mentioned here.

Theme
Colors
Options
Palettes

###### On this page

#### 

## 