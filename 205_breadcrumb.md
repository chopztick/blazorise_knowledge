# Blazorise Breadcrumb component

A simple breadcrumb component to improve your navigation experience.

Breadcrumbs are used to indicate the current page's location.

You can inform the current page using the Active attribute in a BreadcrumbItem.

- &lt; Breadcrumb&gt; the main container.
- &lt;Breadcrumb&gt; the main container.
    - &lt; BreadcrumbItem&gt; the breadcrumb item, which can be active or not.
    - &lt;BreadcrumbItem&gt; the breadcrumb item, which can be active or not.
        - &lt;BreadcrumbLink&gt; the link to the destination page.

## Examples

### Manual mode

This is the default mode. Meaning you need to set  property implicitly.

1. Home
2. Library
3. Data

```
<Breadcrumb>
    <BreadcrumbItem>
        <BreadcrumbLink To="#">Home</BreadcrumbLink>
    </BreadcrumbItem>
    <BreadcrumbItem>
        <BreadcrumbLink To="#">Library</BreadcrumbLink>
    </BreadcrumbItem>
    <BreadcrumbItem Active>
        <BreadcrumbLink To="#">Data</BreadcrumbLink>
    </BreadcrumbItem>
</Breadcrumb>
```

### Auto mode

In this mode breadcrumb items will respond to navigation changes and will be activates automatically.

1. Home
2. Account
3. Settings

```
<Breadcrumb Mode="BreadcrumbMode.Auto">
    <BreadcrumbItem>
        <BreadcrumbLink To="#">Home</BreadcrumbLink>
    </BreadcrumbItem>
    <BreadcrumbItem>
        <BreadcrumbLink To="#">Account</BreadcrumbLink>
    </BreadcrumbItem>
    <BreadcrumbItem>
        <BreadcrumbLink To="#">Settings</BreadcrumbLink>
    </BreadcrumbItem>
</Breadcrumb>
```

## API

### Parameters

#### Breadcrumb

| Parameter    | Description                                                            | Type           | Default             |
|--------------|------------------------------------------------------------------------|----------------|---------------------|
| ChildContent | Specifies the content to be rendered inside this Breadcrumb component. | RenderFragment | null                |
| Mode         | Defines the breadcrumb activation mode.Possible values:None, Auto      | BreadcrumbMode | BreadcrumbMode.None |

#### BreadcrumbItem

| Parameter    | Description                                                           | Type           | Default   |
|--------------|-----------------------------------------------------------------------|----------------|-----------|
| Active       | Indicates whether this breadcrumb item is the active (current) item.  | bool           | false     |
| ChildContent | Specifies the content to render inside this BreadcrumbItem component. | RenderFragment | null      |

#### BreadcrumbLink

| Parameter    | Description                                                                                   | Type           | Default        |
|--------------|-----------------------------------------------------------------------------------------------|----------------|----------------|
| ChildContent | Specifies the content to be rendered inside this BreadcrumbLink component.                    | RenderFragment | null           |
| Disabled     | When set to 'true', disables the component's functionality and places it in a disabled state. | bool           | false          |
| Match        | URL matching behavior for a link.Possible values:Prefix, All, Custom                          | Match          | Match.All      |
| Target       | The target attribute specifies where to open the linked document.                             | Target         | Target.Default |
| Title        | Defines the title of a link, which appears to the user as a tooltip.                          | string         |                |
| To           | Link to the destination page.                                                                 | string         |                |

### Events

#### BreadcrumbLink

| Event   | Description                      | Type                          |
|---------|----------------------------------|-------------------------------|
| Clicked | Occurs when the item is clicked. | EventCallback<MouseEventArgs> |

###### On this page

#### 

## 