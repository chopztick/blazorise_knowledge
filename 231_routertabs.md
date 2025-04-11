# Blazorise RouterTabs component

Automatically create tabs per each page the user navigates to.

RouterTabs is a Blazorise extension that allows you to render a tab for each navigation page. This extension is useful when you want to create a tabbed interface for your application.

### Installation

The RouterTabs extension is part of the  NuGet package.

### Step 1. Download from NuGet

Install extension from NuGet:

```
Install-Package Blazorise.Components
```

### Step 2. Define Usings

In your main  add:

```
@using Blazorise.Components
```

### Step 3. Registering Services

Incorporate RouterTabs services by adding the following code to the relevant sections of .

```
using Blazorise.Components;

builder.Services
	.AddBlazorise()
	.AddBlazoriseRouterTabs();
```

### Step 4. Setting the necessary CascadingValue

Cascade the necessary routeData to be captured by the RouterTabs

```
<Router AppAssembly="typeof(App).Assembly">
    <Found Context="routeData">
        <CascadingValue Value="routeData">
            <RouteView RouteData="routeData" DefaultLayout="typeof(MainLayout)" />
        </CascadingValue>
    </Found>
    <NotFound>
        <p>Sorry, there's nothing at this address.</p>
    </NotFound>
</Router>
```

### Step 5. Configure the Layout.

Replace the Layout @Body RenderFragment with the RouterTabs component. RouterTabs will handle the page content rendering for you when the page that makes use of this layout is navigated to.

```
@inherits LayoutComponentBase

<Div Class="layout">
    <RouterTabs />
</Div>
```

### Step 6. Configure the pages as tabs

Use RouterTabsPageAttribute to configure how your pages will behave when rendered as tabs.

```
@attribute [RouterTabsPageAttribute( Name: "Example", Closeable: true )]
```

### Basic example

This page uses a custom layout with the RouterTabs component, try navigating between these pages, tabs will be created for each one of the navigations.

- Router Tabs
- Router Tabs 2
- Router Tabs 3

## API

### RouterTabsPageAttribute

| Name          | Description                                 | Type   | Default   |
|---------------|---------------------------------------------|--------|-----------|
| Name          | Sets the name of the router tab.            | string |           |
| TabClass      | Sets the css class of the router tab.       | string |           |
| TabPanelClass | Sets the css class of the router tab panel. | string |           |
| Closeable     | Whether the router tab is closeable.        | bool   | true      |

###### On this page

#### 

## 