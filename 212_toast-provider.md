# Blazorise ToastProvider component

Programatically instantiate toasts with custom messages.

The toast provider component provides an abstraction on top of Blazorize's Toast component, enabling you to programatically instantiate toasts with custom messages.

## Setup

You need to place &lt;ToastProvider&gt; somewhere in your application razor code. It can be placed anywhere, but a good approach is to place it in App.razor(.NET 7 and prior), or Routes.razor(.NET 8) like in the following example.

A IToastService will be registered by Blazorise providing you with an API to programatically instantiate toasts. Examples are provided further below.

```
<Router AppAssembly="typeof(App).Assembly">
    <Found>...</Found>
    <NotFound>...</NotFound>
</Router>

<ToastProvider />
```

## Examples

### Basic

Once you’re done you can start using it by injecting the  in your page and then simple calling the built-in methods.

```
<Button Color="Color.Primary" Clicked="@ShowToast">Show toast message!</Button>
```

```
@code {
    [Inject] IToastService ToastService { get; set; }

    Task ShowToast()
    {
        return ToastService.Info( "This is a simple toast message!", "Hello", BuildToastInstanceOptions );
    }

    private void BuildToastInstanceOptions( ToastInstanceOptions toastInstanceOptions )
    {
        toastInstanceOptions.Animated = true;
        toastInstanceOptions.AnimationDuration = 300;
        toastInstanceOptions.Autohide = true;
        toastInstanceOptions.AutohideDelay = 3000;
        toastInstanceOptions.Closing = ( e ) => { Console.WriteLine("Closing"); return Task.CompletedTask; };
        toastInstanceOptions.Opening = ( e ) => { Console.WriteLine("Opening"); return Task.CompletedTask; };
    }
}
```

## Best Practices

### Use Sparingly

Notifications are disruptive by design and should be used sparingly. Use fewer notifications by reserving them for more important information that may otherwise go unnoticed by the user.

Less urgent notifications can be provided through a link or drop-down in the application header or footer, instead of immediate notifications.

### Limit Content Length

Aim for one or two lines of content. Notifications should be brief and to the point. More information can be provided through an embedded link or Button.

### Toast Positions

Toasts can be dispatched to all four corners of a page. We do not recommend to use more than one position for toasts in an application because that could be disorienting for users. Pick one desired position and configure it in the Toaster.

###### On this page

#### 

## 