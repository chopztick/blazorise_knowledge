# Blazorise Icons

Icons are symbols that can be used to represent various options within an application.

Blazorise comes with over 300 icons. These icons are part of the default icon library. If you prefer, you can register custom icon libraries as well.

## Installation

### NuGet

Install extension from NuGet.

```
Install-Package Blazorise.Icons.FontAwesome
```

### Font Awesome Icons CSS

Include CSS link into your  or  /  file, depending if you’re using a Blazor WebAssembly or Blazor Server side project.

```
<link href="_content/Blazorise.Icons.FontAwesome/v6/css/all.min.css" rel="stylesheet">
```

### Material Icons CSS

Note: If instead of FontAwesome icons you want to use Material icons you will need to define static  in your  or  /  file. This file is required for some custom icon styles to work.

```
<link href="_content/Blazorise.Icons.Material/blazorise.icons.material.css" rel="stylesheet" />
```

### Bootstrap Icons CSS

Note: If instead of FontAwesome icons you want to use Bootstrap icons you will need to define static  in your  or  /  file. This file is required for some custom icon styles to work.

```
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css">
```

### Fluent Icons CSS

Note: If instead of Fluent icons you want to use Bootstrap icons you will need to define static  in your  or  /  file. This file is required for some custom icon styles to work.

```
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css">
```

### Registrations

```
builder.Services
	.AddBlazorise()
	.AddBootstrapProviders()
+   .AddFontAwesomeIcons();
```

### Basic Example

To define an icon it’s simple as this.

```
<Icon Name="IconName.Mail" />
```

### Custom

You can also use a real icon name instead of predefined enum.

```
<Icon Name="@("fa-phone")" />
```

### Icon Names

Preferred way to define icon is to use an enum . That way every icon will be applied automatically based on the icon package that you’re using.

        In case you cannot find an icon in the provided enum, you can also use prebuilt list of icon names that comes with every icon package. For example for font-awesome you would use , while for material that would be .

```
<Icon Name="Blazorise.Icons.FontAwesome.FontAwesomeIcons.Voicemail" />
```

### Style

By default all icons will have Solid style. To change it you can use one of the supported styles:

- Solid
- Regular
- Light
- DuoTone

```
<Icon Name="IconName.Mail" IconStyle="IconStyle.Regular" />
```

### Size

You can set the size to one of the supported below.

```
<Div Flex="Flex.Row.Wrap.JustifyContent.Start.AlignItems.Start">
    @foreach ( var iconSize in Enum.GetValues<IconSize>() )
    {
        @if ( iconSize == IconSize.Default )
            continue;

        <Div Flex="Flex.Column.JustifyContent.Center">
            <Span Flex="Flex.JustifyContent.Center.AlignItems.Center" Padding="Padding.Is5">
                <Icon Name="IconName.Camera" IconSize="@iconSize" />
            </Span>
            <Text TextAlignment="TextAlignment.Center">
                @iconSize
            </Text>
        </Div>
    }
</Div>
```

### Global options

Defining styles on each icon can become very tedious with time. That's why we give you an option to specify them globally. This way, you will have consistent styling across the application, and you can still override them on the icon if you need to.

```
services.AddBlazorise( options =>
{
    options.IconStyle = IconStyle.Light;
    options.IconSize = IconSize.Small;
} );
```

## API

### Parameters

| Parameter   | Description                                        | Type       | Default   |
|-------------|----------------------------------------------------|------------|-----------|
| IconSize    | Defines the icon size.                             | IconSize?  | null      |
| IconStyle   | Suggested icon style.                              | IconStyle? | null      |
| Name        | Icon name that can be either a string or IconName. | object     | null      |

### Events

| Event     | Description                                      | Type                          |
|-----------|--------------------------------------------------|-------------------------------|
| Clicked   | Occurs when the icon is clicked.                 | EventCallback<MouseEventArgs> |
| MouseOut  | Occurs when the mouse has left the icon area.    | EventCallback<MouseEventArgs> |
| MouseOver | Occurs when the mouse has entered the icon area. | EventCallback<MouseEventArgs> |

###### On this page

#### 

## 