# Blazorise Page Progress service

Progress service is used to provide a page loading indicator to the user.

The IPageProgressService is built on top of PageProgress component and is used to show small progress bar at the top of the page.

## Quick Setup

To install and use Page Progress service you only need to define one simple thing.

### Step 1. Define wrapper component

is automatically registered by Blazorise but it needs just one thing on your
        side to make it work. You need to place  somewhere in your application razor code.
        It can be placed anywhere, but a good approach is to place it in  like in the following example.

```
<Router AppAssembly="typeof(App).Assembly">
    <Found>...</Found>
    <NotFound>...</NotFound>
</Router>

<PageProgressProvider />
```

## Examples

### Basic

Once you’re done you can start using it by injecting the  in your page and then
        simple calling the built-in methods.

```
<Button Color="Color.Primary" Clicked="@SetPageProgress25">25 %</Button>
<Button Color="Color.Primary" Clicked="@SetPageProgress50">50 %</Button>
<Button Color="Color.Primary" Clicked="@SetPageProgress75">75 %</Button>
<Button Color="Color.Primary" Clicked="@SetPageProgress100">100 %</Button>

<Button Color="Color.Secondary" Clicked="@SetPageProgressIndeterminate">Indeterminate</Button>

<Button Color="Color.Secondary" Clicked="@SetPageProgressHidden">Hide</Button>
```

```
@code{
    [Inject] IPageProgressService PageProgressService { get; set; }

    Task SetPageProgress25()
    {
        return PageProgressService.Go( 25, options => { options.Color = Color.Warning; } );
    }

    Task SetPageProgress50()
    {
        return PageProgressService.Go( 50, options => { options.Color = Color.Warning; } );
    }

    Task SetPageProgress75()
    {
        return PageProgressService.Go( 75, options => { options.Color = Color.Warning; } );
    }

    Task SetPageProgress100()
    {
        return PageProgressService.Go( 100, options => { options.Color = Color.Warning; } );
    }

    Task SetPageProgressIndeterminate()
    {
        return PageProgressService.Go( null, options => { options.Color = Color.Warning; } );
    }

    Task SetPageProgressHidden()
    {
        // setting it to -1 will hide the progress bar
        return PageProgressService.Go( -1 );
    }
}
```

###### On this page

#### 

## 