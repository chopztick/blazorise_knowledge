# Blazorise Notification service

Notification service is used to provide feedback to the user.

They communicate information about activities, processes, and events in the application.

The INotificationService is built on top of Snackbar component and is used for showing simple
    alerts and notifications.

## Quick Setup

To install and use Notifications you just need to follow a few simple steps.

### Step 1: Download from NuGet

Install extension from NuGet.

```
Install-Package Blazorise.Components
```

### Step 2. Define Usings

Since notification service is created as a wrapper around the  component so it is also required to define the namespace inside of your main  file.

```
@using Blazorise.Components
@using Blazorise.Snackbar
```

### Step 3. Define wrapper component

is automatically registered by Blazorise but it needs just one thing on your side
        to make it work. You need to place  somewhere in your application razor code. It can
        be placed anywhere, but a good approach is to place it in  like in the following example.

```
<Router AppAssembly="typeof(App).Assembly">
    <Found>...</Found>
    <NotFound>...</NotFound>
</Router>

<NotificationProvider />
```

### Step 4. Static files

This step is only needed if you didn't already define any CSS files for the Snackbar component. Remember,  The  is built on top of .

```
<link href="_content/Blazorise.Snackbar/blazorise.snackbar.css" rel="stylesheet" />
```

## Examples

### Basic

Once you’re done you can start using it by injecting the  in your page and then simple
        calling the built-in methods.

```
<Button Color="Color.Warning" Clicked="@ShowWarningNotification">Show alert!</Button>
```

```
@code{
    [Inject] INotificationService NotificationService { get; set; }

    Task ShowWarningNotification()
    {
        return NotificationService.Warning( "This is a simple notification message!", "Hello" );
    }
}
```

## Best Practices

### Use Sparingly

Notifications are disruptive by design and should be used sparingly. Use fewer notifications by reserving them for more important information that may otherwise go unnoticed by the user.

Less urgent notifications can be provided through a link or drop-down in the application header or footer, instead of immediate notifications.

### Limit Content Length

Aim for one or two lines of content. Notifications should be brief and to the point. More information can be provided through an embedded link or Button.

###### On this page

#### 

## 