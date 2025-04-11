# Blazorise Badge component

Badges are used to draw attention and display statuses or counts.

The &lt;Badge&gt; component is used to convey small pieces of information. They are used for labeling content, displaying metadata and/or highlighting information. Using the CloseClicked property, the badge becomes interactive, allowing user interaction.

## Examples

### Basic

Simply set the  attribute and you’re good to go.

```
<Badge Color="Color.Primary">Hello</Badge>
```

### Colors

Add any of the following variants via the  parameter to change the appearance of a .

```
<Badge Color="Color.Primary">Primary</Badge>
<Badge Color="Color.Secondary">Secondary</Badge>
<Badge Color="Color.Success">Success</Badge>
<Badge Color="Color.Danger">Danger</Badge>
<Badge Color="Color.Warning">Warning</Badge>
<Badge Color="Color.Info">Info</Badge>
<Badge Color="Color.Light">Light</Badge>
<Badge Color="Color.Dark">Dark</Badge>
```

### Shape

Applying the  parameter produces a badge with rounded corners. It can aid in making badges and buttons more distinct from one another.

```
<Badge Color="Color.Primary" Pill>Pending</Badge>
<Badge Color="Color.Success" Pill>Confirmed</Badge>
<Badge Color="Color.Danger" Pill>Denied</Badge>
<Badge Color="Color.Secondary" Pill>On hold</Badge>
```

### Icon-only

Badges can also be used with icons without a label. For accessibility, a  and  attribute is recommended to ensure that all users can identify their meaning.

```
<Badge Color="Color.Success">
    <Tooltip Text="Confirmed">
        <Icon Name="IconName.Check" aria-label="Confirmed" />
    </Tooltip>
</Badge>
<Badge Color="Color.Danger">
    <Tooltip Text="Cancelled">
        <Icon Name="IconName.Times" aria-label="Cancelled" />
    </Tooltip>
</Badge>
```

### With close button

To enable close button you only need to define the  event. Blazorise will automatically pickup and show close button.

```
<Badge Color="Color.Primary" CloseClicked="@(()=>Console.WriteLine("closed"))">Primary</Badge>
```

## Best Practices

### Badge vs Button

Badges and Buttons are similar in appearance. This might lead users to think that badges are interactive.

Placement, language, shape, and color can all help mitigate any confusion. First, badges should not be labeled with active verbs. This is because they are not actions but relatively static text/content. Second, avoid placing badges directly next to Buttons, in particular, if they are using similar themes. The pill theme variant may aid in making badges and Buttons more distinct from one another.

## API

### Parameters

| Parameter    | Description                                                                    | Type           | Default       |
|--------------|--------------------------------------------------------------------------------|----------------|---------------|
| ChildContent | Specifies the content to be rendered inside this Badge.                        | RenderFragment | null          |
| Color        | Sets the badge contextual color.                                               | Color          | Color.Default |
| Link         | Create a badge link and provide actionable badges with hover and focus states. | string         |               |
| Pill         | Make the badge more rounded.                                                   | bool           | false         |

### Events

| Event        | Description                   | Type          |
|--------------|-------------------------------|---------------|
| CloseClicked | Occurs on close button click. | EventCallback |

###### On this page

#### 

## 