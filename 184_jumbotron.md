# Blazorise Jumbotron component

Lightweight, flexible component for showcasing hero unit style content.

A lightweight, flexible component that can optionally extend the entire viewport to showcase some special content or information.

- &lt; Jumbotron&gt; the main container.
- &lt;Jumbotron&gt; the main container.
    - &lt;JumbotronTitle&gt; required title of the jumbotron.
    - &lt;JumbotronSubtitle&gt; optional subtitle of the jumbotron.

## Examples

### Basic

Jumbotron is a full width card that is usually displayed at the top of the page, sometimes also referred to as a "Hero component".

The jumbotron color should be only slightly off the background of the page to make your design feel "light".

#### Hello, world!

This is a simple hero unit, a simple jumbotron-style component for calling extra attention to featured content or information.

It uses utility classes for typography and spacing to space content out within the larger container.

```
<Jumbotron Background="Background.Light" Margin="Margin.Is4.FromBottom">
    <JumbotronTitle Size="JumbotronTitleSize.Is4">Hello, world!</JumbotronTitle>
    <JumbotronSubtitle>
        This is a simple hero unit, a simple jumbotron-style component for calling extra attention to featured content or information.
    </JumbotronSubtitle>
    <Divider></Divider>
    <Paragraph>
        It uses utility classes for typography and spacing to space content out within the larger container.
    </Paragraph>
</Jumbotron>
```

## API

### Parameters

| Parameter    | Description                                                   | Type           | Default   |
|--------------|---------------------------------------------------------------|----------------|-----------|
| ChildContent | Gets or sets the reference to the parent Jumbotron component. | RenderFragment | null      |

###### On this page

#### 

## 