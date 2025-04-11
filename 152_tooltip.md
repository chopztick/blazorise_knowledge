# Blazorise Tooltip component

Tooltips display additional information based on a specific action.

The &lt;Tooltip&gt; component is useful for conveying information when a user hovers over an element. When activated,
    tooltips display a text label identifying an element, such as a description of its function.

Starting with v0.9.4, Tooltip component is powered by Tippy.js.

## Examples

### Basic

```
<Tooltip Text="Hello tooltip">
    <Button Color="Color.Primary">Hover me</Button>
</Tooltip>
```

### Positions

You can use one of the following modifiers to change positions of the tooltip:

- Top
- Bottom
- Left
- Right

```
<Tooltip Text="Hello tooltip" Placement="TooltipPlacement.Top">
    <Button Color="Color.Primary">Top tooltip</Button>
</Tooltip>
<Tooltip Text="Hello tooltip" Placement="TooltipPlacement.Right">
    <Button Color="Color.Primary">Right tooltip</Button>
</Tooltip>
<Tooltip Text="Hello tooltip" Placement="TooltipPlacement.Left">
    <Button Color="Color.Primary">Left tooltip</Button>
</Tooltip>
<Tooltip Text="Hello tooltip" Placement="TooltipPlacement.Bottom">
    <Button Color="Color.Primary">Bottom tooltip</Button>
</Tooltip>
```

### Different trigger target

You may want the tooltip to appear at a different location from its trigger (event listeners) target.

```
<Div ElementId="tooltip-custom-target">
    Trigger target vs
    <Tooltip Text="I'm a tooltip!" TriggerTargetId="tooltip-custom-target" Inline>
        <Badge Color="Color.Warning">positioning target</Badge>
    </Tooltip>
</Div>
```

### HTML Content

Your tooltip can also contain HTML.

```
<Tooltip Text="<span style='color: aqua;'>Hello</span>, this is a <strong>bolded content</strong>!">
    <Button Color="Color.Primary">Html content</Button>
</Tooltip>
```

### Delay

Your Tooltip can delay hiding or showing after a trigger.

```
<Tooltip Text="I'm a Blazorise Tooltip!" ShowDelay="1000" HideDelay="500">
    <Button Color="Color.Primary">Delay: (1000, 500)</Button>
</Tooltip>
```

## API

### Parameters

| Parameter       | Description                                                                                                                                                                              | Type             | Default                 |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|-------------------------|
| AlwaysActive    | Always show tooltip, instead of just when hovering over the element.                                                                                                                     | bool             | false                   |
| AppendTo        | The element to append the tooltip to. If Tooltip.Interactive = true, the default behavior is appendTo: "parent".                                                                         | string           |                         |
| ChildContent    | Specifies the content to be rendered inside this Tooltip.                                                                                                                                | RenderFragment   | null                    |
| Fade            | Makes the tooltip fade transition.                                                                                                                                                       | bool             | false                   |
| FadeDuration    | Duration in ms of the fade transition animation.                                                                                                                                         | int              | 300                     |
| HideDelay       | Specifies the delay in ms once a trigger event is fired before a Tooltip hides.                                                                                                          | int?             | null                    |
| Inline          | Force inline block instead of trying to detect the element block.                                                                                                                        | bool             | false                   |
| Interactive     | Determines if the tooltip has interactive content inside of it, so that it can be hovered over and clicked inside without hiding.                                                        | bool             | false                   |
| Multiline       | Force the multiline display.                                                                                                                                                             | bool             | false                   |
| Placement       | Gets or sets the tooltip location relative to its component.Possible values:Top, TopStart, TopEnd, Bottom, BottomStart, BottomEnd, Left, LeftStart, LeftEnd, Right, RightStart, RightEnd | TooltipPlacement | TooltipPlacement.Top    |
| ShowArrow       | Gets or sets the tooltip arrow visibility.                                                                                                                                               | bool             | true                    |
| ShowDelay       | Specifies the delay in ms once a trigger event is fired before a Tooltip shows.                                                                                                          | int?             | null                    |
| Text            | Gets or sets a regular tooltip's content.                                                                                                                                                | string           |                         |
| Trigger         | Determines the events that cause the tooltip to show.Possible values:MouseEnterFocus, Click, Focus, MouseEnterClick                                                                      | TooltipTrigger   | default(TooltipTrigger) |
| TriggerTargetId | Which element the trigger event listeners are applied to (instead of the reference element).                                                                                             | string           |                         |
| ZIndex          | Specifies the z-index CSS on the root popper node.                                                                                                                                       | int?             | 9999                    |

###### On this page

#### 

## 