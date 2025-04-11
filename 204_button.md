# Blazorise Button component

Use Blazorise custom button styles for actions in forms, dialogs, and more with support for multiple sizes, states, and more.

The Button component replaces the standard html button with a multitude of options. Any color helper class can be used to alter the background or text color. Try out an interactive examples on how Blazorise buttons work.

## Overview

Blazorise &lt;Button&gt; component generates either a &lt;button&gt; element, or &lt;a&gt; element with the styling of a button.

## Examples

### Basic button

To create a basic button you need to use a Button component.

```
<Button Color="Color.Primary">Click me</Button>
```

### Clicked event

To use button you just handle a button  event.

```
<Button Color="Color.Primary" Clicked="@OnButtonClicked">Click me</Button>
<Span>
    Clicked @counter times
</Span>
```

```
@code {
    int counter;

    Task OnButtonClicked()
    {
        counter++;

        return Task.CompletedTask;
    }
}
```

### Colors variants

The following variants can be used to distinguish between actions of different importance in the UI:

```
<Button Color="Color.Primary">Primary</Button>
<Button Color="Color.Secondary">Secondary</Button>
<Button Color="Color.Success">Success</Button>
<Button Color="Color.Warning">Warning</Button>
<Button Color="Color.Danger">Danger</Button>
<Button Color="Color.Info">Info</Button>
<Button Color="Color.Light">Light</Button>
<Button Color="Color.Dark">Dark</Button>
<Button>None</Button>
```

### Outline variants

To define button color with a borders use an  attribute.

```
<Button Color="Color.Primary" Outline>Primary</Button>
<Button Color="Color.Secondary" Outline>Secondary</Button>
<Button Color="Color.Success" Outline>Success</Button>
<Button Color="Color.Warning" Outline>Warning</Button>
<Button Color="Color.Danger" Outline>Danger</Button>
<Button Color="Color.Info" Outline>Info</Button>
<Button Color="Color.Light" Outline>Light</Button>
<Button Color="Color.Dark" Outline>Dark</Button>
<Button Outline>None</Button>
```

### Sizes

The following size variants are available for Button instances whose size needs to be different from the default:

```
<Button Color="Color.Primary" Size="Size.Large">Large</Button>
<Button Color="Color.Primary">Normal</Button>
<Button Color="Color.Primary" Size="Size.Small">Small</Button>
```

### Block

```
<Button Color="Color.Primary" Block>Blocked primary</Button>
<Button Color="Color.Secondary" Block>Blocked secondary</Button>
```

### Active

```
<Button Color="Color.Primary" Active>Primary</Button>
<Button Color="Color.Secondary" Active>Secondary</Button>
```

### Disabled

Buttons representing actions that are not currently available to the user should be either hidden or disabled. A disabled button is rendered as "dimmed", and is excluded from the focus order (such as when interactive UI elements are focused using the tab key).

```
<Button Color="Color.Primary" Disabled>Primary</Button>
<Button Color="Color.Secondary" Disabled>Secondary</Button>
```

### Hidden vs Disabled

Hiding an unavailable action entirely is often preferable to a disabled button, as this reduces UI clutter. However, in certain situations this can be problematic:

- If the user expects a button to be present, such as at the end of a form, hiding the button can cause confusion, even if the form clearly indicates the presence of one or more invalid fields.
- As a hidden button does not occupy any space in the UI, toggling its visibility can cause unwanted changes in the layout of other elements.

### Loading

Use  attribute to add spinners within buttons to indicate an action is currently processing or taking place. Use  to add a custom loading template

```
<Button Color="Color.Primary" Loading>Primary</Button>
<Button Color="Color.Primary" Clicked="@ShowLoading" Loading="@isLoading">
    <LoadingTemplate>
        This is a custom loading template
    </LoadingTemplate>
    <ChildContent>
        Click to load
    </ChildContent>
</Button>
```

```
@code{
    private bool isLoading;

    private async Task ShowLoading()
    {
        isLoading = true;

        await Task.Delay( TimeSpan.FromSeconds( 3 ) );

        isLoading = false;
    }
}
```

### Button group

If you want to group buttons together on a single line, use the  component.

```
<Buttons>
    <Button Color="Color.Secondary">LEFT</Button>
    <Button Color="Color.Secondary">CENTER</Button>
    <Button Color="Color.Secondary">RIGHT</Button>
</Buttons>
```

### Link Button

By default,  works with  element, but you can also create an  element that will still appear as regular button.

```
<Button Color="Color.Primary" Type="ButtonType.Link" To="#">Primary link</Button>
<Button Color="Color.Secondary" Type="ButtonType.Link" To="#" Target="Target.Blank">Secondary link</Button>
```

### Stretched link

Add StretchedLink attribute to a link to make its containing block clickable via a ::after pseudo element. In most cases, this means that an element with position: relative that contains a link with the stretched link class is clickable. Please note given how CSS position works, stretched-link cannot be mixed with most table elements.

Cards have position: relative by default, so in this case you can safely add the StretchedLink attribute to a link in the card without any other HTML changes.

Please note that on some CSS providers the &lt;Button&gt; component can have position: relative by default, so the link would assume the button to be its relative parent element.

<!-- image -->

### Card with stretched link

Some quick example text to build on the card title and make up the bulk of the card's content.

```
<Card Width="Width.Rem(18)">
    <CardImage Source="/img/gallery/5.jpg" Alt="Placeholder image" />
    <CardBody>
        <CardTitle Size="3">
            Card with stretched link
        </CardTitle>
        <CardText>
            Some quick example text to build on the card title and make up the bulk of the card's content.
        </CardText>
        <Button Type="ButtonType.Link" To="#" Color="Color.Primary" StretchedLink>
            Go somewhere
        </Button>
    </CardBody>
</Card>
```

### Toolbar

To attach buttons together use a  role.

```
<Buttons Role="ButtonsRole.Toolbar">
    <Buttons Margin="Margin.Is2.FromEnd">
        <Button Color="Color.Primary">Primary</Button>
        <Button Color="Color.Secondary">Secondary</Button>
        <Button Color="Color.Info">Info</Button>
    </Buttons>
    <Buttons>
        <Button Color="Color.Danger">Danger</Button>
        <Button Color="Color.Warning">Warning</Button>
    </Buttons>
    <Buttons Margin="Margin.Is2.OnX">
        <Button Color="Color.Success">Success</Button>
    </Buttons>
</Buttons>
```

### Submit button

When using a submit button inside of  element the browser will automatically try to post the page. This is the default browser behavior. Because of this a new attribute is introduced to the  element, called . Basically it prevents a default browser behavior when clicking the submit button. So instead of posting the page it will stop it and just call the  event handler. Pressing the  key will still work just as it’s supposed to do.

```
<Form>
    <Field Horizontal>
        <FieldLabel ColumnSize="ColumnSize.Is2">Name</FieldLabel>
        <FieldBody ColumnSize="ColumnSize.Is10">
            <TextEdit Placeholder="Some text value..." />
        </FieldBody>
    </Field>
    <Field>
        <Button Color="Color.Primary" Type="ButtonType.Submit" PreventDefaultOnSubmit>Submit</Button>
    </Field>
</Form>
```

## Best Practices

### Button Labels

- The label should describe the action, preferably using active verbs, such as "View details" rather than just "Details".
- In cases of possible ambiguity, also specify the object of the verb, such as "Save changes" instead of "Save".
- Button groups representing options, such as the buttons of a Confirm Dialog, should state what each option represents, such as "Save changes", instead of "Yes", as the latter forces the user to read the question being asked, and increases the risk of selecting the wrong option.
- Keep labels short, ideally less than three words or 25 characters.
- Use ellipsis (…) when an action is not immediate but requires more steps to complete. This is useful, for example, for destructive actions like "Delete…​" when a Confirm Dialog is used to confirm the action before it is executed.

### ARIA Labels

The aria-label attribute can be used to provide a separate label for accessibility technologies (AT) such as screen readers. This is important, for example, for icon-only buttons that lack a visible label.

Buttons with regular, visible labels can also benefit from separate aria-label to provide more context that may otherwise be difficult for the AT user to perceive.

### Buttons in Forms

```
<Fields>
    <Field ColumnSize="ColumnSize.IsHalf">
        <FieldLabel>First name</FieldLabel>
        <FieldBody>
            <TextEdit Text="John" />
        </FieldBody>
    </Field>
    <Field ColumnSize="ColumnSize.IsHalf">
        <FieldLabel>Last name</FieldLabel>
        <FieldBody>
            <TextEdit Text="Smith" />
        </FieldBody>
    </Field>
    <Field ColumnSize="ColumnSize.IsFull">
        <FieldLabel>Email address</FieldLabel>
        <FieldBody>
            <TextEdit Text="john.smith@example.com" />
        </FieldBody>
    </Field>
    <Field>
        <Button Color="Color.Primary">Create account</Button>
        <Button Color="Color.Secondary">Cancel</Button>
    </Field>
</Fields>
```

### Buttons in Dialogs

- Buttons should be placed at the bottom of the dialog.
- Buttons should be aligned right.
- Primary action last, preceded by other actions.
- Dangerous actions should be aligned left, to avoid accidental clicks, especially if no confirmation step is included.

```
<Fields>
    <Field ColumnSize="ColumnSize.IsHalf">
        <FieldLabel>First name</FieldLabel>
        <FieldBody>
            <TextEdit Text="John" />
        </FieldBody>
    </Field>
    <Field ColumnSize="ColumnSize.IsHalf">
        <FieldLabel>Last name</FieldLabel>
        <FieldBody>
            <TextEdit Text="Smith" />
        </FieldBody>
    </Field>
    <Field ColumnSize="ColumnSize.IsFull">
        <FieldLabel>Email address</FieldLabel>
        <FieldBody>
            <TextEdit Text="john.smith@example.com" />
        </FieldBody>
    </Field>
    <Field Flex="Flex.JustifyContent.Between">
        <Button Color="Color.Danger">Delete</Button>
        <Div>
            <Button Color="Color.Secondary">Cancel</Button>
            <Button Color="Color.Primary">Create account</Button>
        </Div>
    </Field>
</Fields>
```

## API

### Parameters

| Parameter              | Description                                                                                                   | Type           | Default           |
|------------------------|---------------------------------------------------------------------------------------------------------------|----------------|-------------------|
| Active                 | When set to 'true', places the component in the active state with active styling.                             | bool           | false             |
| Block                  | Makes the button to span the full width of a parent.                                                          | bool           | false             |
| ChildContent           | Specifies the content to be rendered inside this Button.                                                      | RenderFragment | null              |
| Color                  | Gets or sets the button color.                                                                                | Color          | Color.Default     |
| Command                | Gets or sets the command to be executed when clicked on a button.                                             | ICommand       | null              |
| CommandParameter       | Reflects the parameter to pass to the CommandProperty upon execution.                                         | object         | null              |
| Disabled               | When set to 'true', disables the component's functionality and places it in a disabled state.                 | bool           | false             |
| Loading                | Shows the loading spinner or a Button.LoadingTemplate.                                                        | bool           | false             |
| LoadingTemplate        | Gets or sets the component loading template.                                                                  | RenderFragment | null              |
| Outline                | Makes the button to have the outlines.                                                                        | bool           | false             |
| PreventDefaultOnSubmit | Prevents a default form-post when button type is set to ButtonType.Submit.                                    | bool           | false             |
| Size                   | Changes the size of a button.                                                                                 | Size?          | null              |
| StretchedLink          | Makes any HTML element or component clickable by “stretching” a nested link.                                  | bool           | false             |
| TabIndex               | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation. | int?           | null              |
| Target                 | The target attribute specifies where to open the linked document for a ButtonType.Link.                       | Target         | Target.Default    |
| To                     | Denotes the target route of the ButtonType.Link button.                                                       | string         |                   |
| Type                   | Defines the button type.Possible values:Button, Submit, Reset, Link                                           | ButtonType     | ButtonType.Button |

### Events

| Event   | Description                        | Type                          |
|---------|------------------------------------|-------------------------------|
| Clicked | Occurs when the button is clicked. | EventCallback<MouseEventArgs> |

### Methods

| Method   | Description                                             | Return   | Parameters           |
|----------|---------------------------------------------------------|----------|----------------------|
| Focus    | Sets focus on the button element, if it can be focused. | Task     | bool scrollToElement |

###### On this page

#### 

## 