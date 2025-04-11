# Blazorise Alert component

Provide contextual feedback messages for typical user actions with the handful of available and flexible alert messages.

The &lt;Alert&gt; component is used to convey important information to the user through the use of contextual types, icons, and colors.

## Overview

- &lt; Alert&gt; the main container.
- &lt;Alert&gt; the main container.
    - &lt;AlertMessage&gt; the main content of the Alert.
    - &lt;AlertDescription&gt; an optional description of the Alert.
    - &lt;CloseButton&gt; an optional close button, which will hide the Alert.

## When to use

- When you need to show alert messages to users.
- When you need a persistent static container which is closable by user actions.

## Examples

### Basic

You successfully read this important alert message.

```
<Alert Color="Color.Success" Visible>
    <AlertMessage>Well done!</AlertMessage>
    <AlertDescription>You successfully read this important alert message.</AlertDescription>
</Alert>
```

### Close button

You can also add a .

```
<Alert Color="Color.Success" @bind-Visible="@visible">
    <AlertDescription>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit.
    </AlertDescription>
    <AlertMessage>
        Alert Link.
    </AlertMessage>
    <CloseButton />
</Alert>
```

```
@code {
    bool visible = true;
}
```

### Extra content

can also contain additional HTML elements like headings and paragraphs, which will be styled with the appropriate color matching the variant.

#### Big one!

Lorem ipsum dolor sit amet, consectetur adipisicing elit. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Cras mattis consectetur purus sit amet fermentum.

Wanna do this
Or do this

```
<Alert Color="Color.Info" @bind-Visible="@visible">
    <Heading Size="HeadingSize.Is4" TextColor="TextColor.Success">
        Big one!
        <CloseButton />
    </Heading>
    <Paragraph>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Cras mattis consectetur purus sit amet fermentum.
    </Paragraph>
    <Paragraph>
        <Button Color="Color.Info">Wanna do this</Button>
        <Button Color="Color.Light">Or do this</Button>
    </Paragraph>
</Alert>
```

```
@code {
    bool visible = true;
}
```

## Usages

### Two-way binding

To show alert just set  attribute to true.

```
<Alert Color="Color.Success" @bind-Visible="@visible">
    <AlertMessage>
        Alert test.
    </AlertMessage>
</Alert>

<Button Clicked="@OnButtonClick" Color="Color.Primary">Toggle alert</Button>
```

```
@code {
    bool visible = true;

    Task OnButtonClick()
    {
        visible = !visible;

        return Task.CompletedTask;
    }
}
```

### Programmatically

```
<Alert @ref="myAlert" Color="Color.Success">
    <AlertMessage>
        Alert test.
    </AlertMessage>
</Alert>

<Button Clicked="@OnButtonClick" Color="Color.Primary">Show alert</Button>
```

```
@code{
    Alert myAlert;

    Task OnButtonClick()
    {
        return myAlert.Show();
    }
}
```

## API

### Parameters

| Parameter    | Description                                                             | Type           | Default   |
|--------------|-------------------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this Alert.                 | RenderFragment | null      |
| Color        | Gets or sets the alert color.                                           | Color          | null      |
| Dismisable   | Enables the alert to be closed by placing the padding for close button. | bool           | false     |
| Visible      | Sets the alert visibility.                                              | bool           | false     |

### Events

| Event          | Description                                     | Type                |
|----------------|-------------------------------------------------|---------------------|
| VisibleChanged | Occurs when the alert visibility state changes. | EventCallback<bool> |

### Methods

| Method   | Description                          | Return   | Parameters   |
|----------|--------------------------------------|----------|--------------|
| Show     | Displays the alert to the user.      | Task     |              |
| Hide     | Conceals the alert from the user.    | Task     |              |
| Toggle   | Toggles the visibility of the alert. | Task     |              |

###### On this page

#### 

## 