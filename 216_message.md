# Blazorise Message service

Message service is used for quick user confirmation actions.

The IMessageService is a powerful helper utility built on top of Modal component
    and is used for showing the messages and confirmation dialogs to the user.

## Quick Setup

To install and use Message service you only need to define one simple thing.

### Step 1. Define wrapper component

is automatically registered by Blazorise but it needs just one thing on
        your side to make it work. You need to place  somewhere in your application
        razor code. It can be placed anywhere, but a good approach is to place it in  like in
        the following example.

```
<Router AppAssembly="typeof(App).Assembly">
    <Found>...</Found>
    <NotFound>...</NotFound>
</Router>

<MessageProvider />
```

## Examples

### Basic

```
<Button Color="Color.Primary" Clicked="@ShowInfoMessage">Say hi!</Button>
<Button Color="Color.Danger" Clicked="@ShowConfirmMessage">Confirm</Button>
```

```
@code{
    [Inject] IMessageService MessageService { get; set; }

    Task ShowInfoMessage()
    {
        return MessageService.Info( "This is a simple info message!", "Hello" );
    }

    async Task ShowConfirmMessage()
    {
        if ( await MessageService.Confirm( "Are you sure you want to confirm?", "Confirmation" ) )
        {
            Console.WriteLine( "OK Clicked" );
        }
        else
        {
            Console.WriteLine( "Cancel Clicked" );
        }
    }
}
```

###### On this page

#### 

## 