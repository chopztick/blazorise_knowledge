# Blazorise Snackbar component

Snackbar provide brief messages about app processes. The component is also known as a toast.

The snackbar extension is defined of several different components:

- &lt; Snackbar&gt; main snackbar component
    - &lt;SnackbarBody&gt; container for the snackbar content
    - &lt;SnackbarAction&gt; snackbar action button

## Installation

### NuGet

Install extension from NuGet.

```
Install-Package Blazorise.Snackbar
```

### Imports

In your main  add:

```
@using Blazorise.Components
@using Blazorise.Snackbar
```

### Static files

Include CSS link into your  or  /  file, depending if you’re using a Blazor WebAssembly or Blazor Server side project.

```
<link href="_content/Blazorise.Snackbar/blazorise.snackbar.css" rel="stylesheet" />
```

### Basic example

A basic snackbar that aims to reproduce standard snackbar behavior.

Single line of text directly related to the operation performed

```
<Button Clicked="@(()=>snackbar.Show())">Snackbar</Button>

<Snackbar @ref="snackbar">
    <SnackbarBody>
        Single line of text directly related to the operation performed
    </SnackbarBody>
</Snackbar>
```

```
@code{
    Snackbar snackbar;
}
```

### Variant snackbars

You can also define variant  to override default snackbar style.

```
<Button Color="Color.Primary" Clicked="@(()=>snackbarPrimary.Show())">Primary</Button>
<Button Color="Color.Secondary" Clicked="@(()=>snackbarSecondary.Show())">Secondary</Button>

<Snackbar @ref="snackbarPrimary" Color="SnackbarColor.Primary">
  <SnackbarBody>
    Single line of text directly related to the operation performed
    <SnackbarAction Clicked="@(()=>snackbarPrimary.Hide())">ACTION</SnackbarAction>
  </SnackbarBody>
</Snackbar>
<Snackbar @ref="snackbarSecondary" Color="SnackbarColor.Secondary">
  <SnackbarBody>
    Single line of text directly related to the operation performed
    <SnackbarAction Clicked="@(()=>snackbarSecondary.Hide())">ACTION</SnackbarAction>
  </SnackbarBody>
</Snackbar>
```

```
@code{
    private Snackbar snackbarPrimary;
    private Snackbar snackbarSecondary;
}
```

### Stacked snackbars

When you want to show multiple snackbars stacked on top of each other you can use a wrapper component . 
        You can specify  when calling  in order to specify the  parameters available below.

```
<Button Color="Color.Primary" Clicked="@(()=>snackbarStack.PushAsync("Current time is: " + DateTime.Now, SnackbarColor.Info))">Primary</Button>

<Button Color="Color.Info" Clicked="@(()=>snackbarStack.PushAsync("Some info message! Timeout: " + intervalBeforeMsgClose, SnackbarColor.Info, options => {  options.IntervalBeforeClose = intervalBeforeMsgClose; } ))">Show Info</Button>

<SnackbarStack @ref="snackbarStack" Location="SnackbarStackLocation.BottomEnd" />
```

```
@code{
    SnackbarStack snackbarStack;
    double intervalBeforeMsgClose = 2000;
}
```

## API

### Parameters

| Parameter                 | Description                                                                                                              | Type             | Default                  |
|---------------------------|--------------------------------------------------------------------------------------------------------------------------|------------------|--------------------------|
| AnimationDuration         | Defines the base animation duration in milliseconds.                                                                     | double           | 0                        |
| ChildContent              | Specifies the content to be rendered inside this Snackbar.Snackbar.                                                      | RenderFragment   | null                     |
| Color                     | Defines the snackbar color.Possible values:Default, Primary, Secondary, Success, Danger, Warning, Info, Light, Dark      | SnackbarColor    | SnackbarColor.Default    |
| DelayCloseOnClick         | If clicked on snackbar, a close action will be delayed by increasing the Snackbar.Snackbar.Interval time.                | bool             | false                    |
| DelayCloseOnClickInterval | Defines the interval (in milliseconds) by which the snackbar will be delayed from closing.                               | double?          | null                     |
| Interval                  | Defines the interval (in milliseconds) after which the snackbar will be automatically closed.                            | double           | 0                        |
| Key                       | Unique key associated by this snackbar.                                                                                  | string           |                          |
| Location                  | Defines the snackbar location.Possible values:Default, Bottom, BottomStart, BottomEnd, Start, End, Top, TopStart, TopEnd | SnackbarLocation | SnackbarLocation.Default |
| Multiline                 | Allow snackbar to show multiple lines of text.                                                                           | bool             | false                    |
| Visible                   | Defines the visibility of snackbar.                                                                                      | bool             | false                    |

### Events

| Event   | Description                           | Type                                   |
|---------|---------------------------------------|----------------------------------------|
| Closed  | Occurs after the snackbar has closed. | EventCallback<SnackbarClosedEventArgs> |

### Methods

| Method   | Description         | Return   | Parameters   |
|----------|---------------------|----------|--------------|
| Show     | Shows the snackbar. | Task     |              |
| Hide     | Hides the snackbar. | Task     |              |

###### On this page

#### 

## 