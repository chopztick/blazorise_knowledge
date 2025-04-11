# Blazorise Object Fit Utilities

Use the object fit utilities to modify how the content of a replaced element, such as an &lt;Image&gt;, should be resized to fit its container.

## How it works

Change the value of the object-fit property  with our responsive ObjectFit utility classes. This property tells the content to fill the parent container in a variety of ways, such as preserving the aspect ratio or stretching to take up as much space as possible.

Classes for the value of ObjectFit are named using the format ObjectFit.{value}. Choose from the following values:

Contain
Cover
Fill
Scale (for scale-down)
None

## Examples

### Basic

Add the  class to the :

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

```
<Div Flex="Flex.Row" Overflow="Overflow.Auto" Gap="Gap.Is3">
    <Image Source="@imageSrc" Text="Placeholder : Object fit contain" ObjectFit="ObjectFit.Contain" Border="@border" Width="@width" Height="@height" />
    <Image Source="@imageSrc" Text="Placeholder : Object fit cover" ObjectFit="ObjectFit.Cover" Border="@border" Width="@width" Height="@height" />
    <Image Source="@imageSrc" Text="Placeholder : Object fit fill" ObjectFit="ObjectFit.Fill" Border="@border" Width="@width" Height="@height" />
    <Image Source="@imageSrc" Text="Placeholder : Object fit scale" ObjectFit="ObjectFit.Scale" Border="@border" Width="@width" Height="@height" />
    <Image Source="@imageSrc" Text="Placeholder : Object fit none" ObjectFit="ObjectFit.None" Border="@border" Width="@width" Height="@height" />
</Div>
```

```
@code {
    IFluentSizing width = Width.Px( 140 );
    IFluentSizing height = Height.Px( 120 );
    IFluentBorder border = Border.Is1.Rounded;
    string imageSrc = "_content/Blazorise.Docs/assets/img/photo/mountain.jpg";
}
```

### Resizing to cover a container

Use the  utility to resize an element’s content to cover its container.

<!-- image -->

```
<Div Width="Width.Rem(24)" Background="Background.Light" Margin="Margin.IsAuto.OnX">
    <Image Source="@imageSrc" Text="mountain" ObjectFit="ObjectFit.Cover" Height="Height.Rem( 12 )" Width="Width.Is100" Border="Border.Is1.Rounded" />
</Div>
```

```
@code {
    string imageSrc = "_content/Blazorise.Docs/assets/img/photo/mountain.jpg";
}
```

### Containing an element

Use the  utility to resize an element’s content to stay contained within its container.

<!-- image -->

```
<Div Width="Width.Rem(24)" Background="Background.Light" Margin="Margin.IsAuto.OnX">
    <Image Source="@imageSrc" Text="mountain" ObjectFit="ObjectFit.Contain" Height="Height.Rem( 12 )" Width="Width.Is100" Border="Border.Is1.Rounded" />
</Div>
```

```
@code {
    string imageSrc = "_content/Blazorise.Docs/assets/img/photo/mountain.jpg";
}
```

### Stretching to fit a container

Use the  utility to stretch an element’s content to fit its container.

<!-- image -->

```
<Div Width="Width.Rem(24)" Background="Background.Light" Margin="Margin.IsAuto.OnX">
    <Image Source="@imageSrc" Text="mountain" ObjectFit="ObjectFit.Fill" Height="Height.Rem( 12 )" Width="Width.Is100" Border="Border.Is1.Rounded" />
</Div>
```

```
@code {
    string imageSrc = "_content/Blazorise.Docs/assets/img/photo/mountain.jpg";
}
```

### Scaling down if too large

Use the  utility to display an element’s content at its original size but scale it down to fit its container if necessary.

<!-- image -->

```
<Div Width="Width.Rem(24)" Background="Background.Light" Margin="Margin.IsAuto.OnX">
    <Image Source="@imageSrc" Text="mountain" ObjectFit="ObjectFit.Scale" Height="Height.Rem( 12 )" Width="Width.Is100" Border="Border.Is1.Rounded" />
</Div>
```

```
@code {
    string imageSrc = "_content/Blazorise.Docs/assets/img/photo/mountain.jpg";
}
```

### Using an element's original size

Use the  utility to display an element’s content at its original size ignoring the container size.

<!-- image -->

```
<Div Width="Width.Rem(24)" Background="Background.Light" Margin="Margin.IsAuto.OnX">
    <Image Source="@imageSrc" Text="mountain" ObjectFit="ObjectFit.None" Height="Height.Rem( 12 )" Width="Width.Is100" Border="Border.Is1.Rounded" />
</Div>
```

```
@code {
    string imageSrc = "_content/Blazorise.Docs/assets/img/photo/mountain.jpg";
}
```

### Breakpoints and media queries

Responsive variations also exist for each ObjectFit value using the format ObjectFit.{Value}.{Breakpoint}, for the following breakpoint abbreviations: OnMobile, OnTablet, OnDesktop, OnWidescreen, OnFullHD, OnQuadHD. Classes can be combined for various effects as you need.

Note: To simulate and view it in action, turn on the DevTools responsive mode in your browser or click the view buttons below.

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

<!-- image -->

```
<Div Flex="Flex.Row" Overflow="Overflow.Auto" Gap="Gap.Is3">
    <Image Source="@imageSrc" Text="Placeholder : Contain on xs" ObjectFit="ObjectFit.Contain.OnMobile" Border="@border" Width="@width" Height="@height" />
    <Image Source="@imageSrc" Text="Placeholder : Contain on sm" ObjectFit="ObjectFit.Contain.OnTablet" Border="@border" Width="@width" Height="@height" />
    <Image Source="@imageSrc" Text="Placeholder : Contain on md" ObjectFit="ObjectFit.Contain.OnDesktop" Border="@border" Width="@width" Height="@height" />
    <Image Source="@imageSrc" Text="Placeholder : Contain on lg" ObjectFit="ObjectFit.Contain.OnWidescreen" Border="@border" Width="@width" Height="@height" />
    <Image Source="@imageSrc" Text="Placeholder : Contain on xl" ObjectFit="ObjectFit.Contain.OnFullHD" Border="@border" Width="@width" Height="@height" />
    <Image Source="@imageSrc" Text="Placeholder : Contain on xxl" ObjectFit="ObjectFit.Contain.OnQuadHD" Border="@border" Width="@width" Height="@height" />
</Div>
```

```
@code {
    IFluentSizing width = Width.Px( 140 );
    IFluentSizing height = Height.Px( 80 );
    IFluentBorder border = Border.Is1.Rounded;
    string imageSrc = "_content/Blazorise.Docs/assets/img/photo/mountain.jpg";
}
```

###### On this page

#### 

## 