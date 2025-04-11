# Position

Use these shorthand utilities for quickly configuring the position of an element.

### Position values

Quick positioning classes are available, though they are not responsive.

```
<Div Position="Position.Static">...</Div>
<Div Position="Position.Relative">...</Div>
<Div Position="Position.Absolute">...</Div>
<Div Position="Position.Fixed">...</Div>
<Div Position="Position.Sticky">...</Div>
```

### Arrange elements

Arrange elements easily with the edge positioning utilities. The format is {Property}.Is{Position}.

Where property is one of:

- Top - for the vertical top position
- Left - for the horizontal left position
- Bottom - for the vertical bottom position
- Right - for the horizontal right position

Where position is one of:

- 0 - for the 0 position
- 50 - for the 50% position
- 100 - for the 100% position

```
<Div Position="Position.Relative">
    <Div Position="Position.Absolute.Top.Is0.Start.Is0"></Div>
    <Div Position="Position.Absolute.Top.Is0.End.Is0"></Div>
    <Div Position="Position.Absolute.Top.Is50.Start.Is50"></Div>
    <Div Position="Position.Absolute.Bottom.Is50.End.Is50"></Div>
    <Div Position="Position.Absolute.Bottom.Is0.Start.Is0"></Div>
    <Div Position="Position.Absolute.Bottom.Is0.End.Is0"></Div>
</Div>
```

### Center elements

In addition, you can also center the elements with the transform utility class Translate.Middle.

```
<Div Position="Position.Relative">
    <Div Position="Position.Absolute.Top.Is0.Start.Is0.Translate.Middle"></Div>
    <Div Position="Position.Absolute.Top.Is0.Start.Is50.Translate.Middle"></Div>
    <Div Position="Position.Absolute.Top.Is0.Start.Is100.Translate.Middle"></Div>
    <Div Position="Position.Absolute.Top.Is50.Start.Is0.Translate.Middle"></Div>
    <Div Position="Position.Absolute.Top.Is50.Start.Is50.Translate.Middle"></Div>
    <Div Position="Position.Absolute.Top.Is50.Start.Is100.Translate.Middle"></Div>
    <Div Position="Position.Absolute.Top.Is100.Start.Is0.Translate.Middle"></Div>
    <Div Position="Position.Absolute.Top.Is100.Start.Is50.Translate.Middle"></Div>
    <Div Position="Position.Absolute.Top.Is100.Start.Is100.Translate.Middle"></Div>
</Div>
```

By adding .Translate.MiddleX or .Translate.MiddleY classes,
        elements can be positioned only in horizontal or vertical direction.

```
<Div Position="Position.Relative">
    <Div Position="Position.Absolute.Top.Is0.Start.Is0"></Div>
    <Div Position="Position.Absolute.Top.Is0.Start.Is50.Translate.MiddleX"></Div>
    <Div Position="Position.Absolute.Top.Is0.End.Is0"></Div>
    <Div Position="Position.Absolute.Top.Is50.Start.Is0.Translate.MiddleY"></Div>
    <Div Position="Position.Absolute.Top.Is50.Start.Is50.Translate.Middle"></Div>
    <Div Position="Position.Absolute.Top.Is50.End.Is0.Translate.MiddleY"></Div>
    <Div Position="Position.Absolute.Bottom.Is0.Start.Is0"></Div>
    <Div Position="Position.Absolute.Bottom.Is0.Start.Is50.Translate.MiddleX"></Div>
    <Div Position="Position.Absolute.Bottom.Is0.End.Is0"></Div>
</Div>
```

### Examples

Here are some real life examples of these classes:

```
<Button Color="Color.Primary" Position="Position.Relative">
    Mails
    <Badge Color="Color.Secondary" Pill Position="Position.Absolute.Top.Is0.Start.Is100.Translate.Middle">
        +99
    </Badge>
</Button>
<Button Color="Color.Primary" Position="Position.Relative">
    Alerts
    <Badge Color="Color.Danger" Pill Position="Position.Absolute.Top.Is0.Start.Is100.Translate.Middle" Border="Border.Light.OnAll.RoundedCircle" Padding="Padding.Is2">
        <Span Visibility="Visibility.Invisible" Position="Position.Absolute">unread messages</Span>
    </Badge>
</Button>
```

###### On this page

#### 

## 