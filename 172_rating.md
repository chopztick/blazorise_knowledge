# Blazorise Rating component

Ratings provide insight regarding others opinions and experiences with a product.

Rating component can be used to allow the users to share their opinion about the product, documentation page, photo and more.

## Examples

### Basic

To start with a basic example just define the rating color.

```
<Rating Color="Color.Primary" />
```

### Two-way binding

Binding the selected value to a variable will make it more usable.

```
<Rating Color="Color.Primary" @bind-SelectedValue="@SelectedValue" MaxValue="10" />
```

```
@code{
    int SelectedValue = 7;
}
```

### Show Tooltips

By defining the GetTooltip callback you can show the extra information to the user.

Along with the tooltip Text, it is also possible to control tooltip arrow visibility, multiline mode, and placement.

```
<Rating Color="Color.Primary" @bind-SelectedValue="@SelectedValue" MaxValue="10" GetTooltip="@GetTooltip" />
```

```
@code {
    int SelectedValue = 7;

    RatingTooltip GetTooltip( int value )
    {
        if ( value <= 2 )
            return new RatingTooltip( "Very bad" );
        else if ( value <= 4 )
            return new RatingTooltip( "Bad", TooltipPlacement.Bottom );
        else if ( value <= 6 )
            return new RatingTooltip( "Fair" );
        else if ( value <= 8 )
            return new RatingTooltip( "Good", TooltipPlacement.Top, false, false );
        else if ( value <= 10 )
            return new RatingTooltip( "Very good" );

        return null;
    }
}
```

## API

### Parameters

| Parameter        | Description                                                        | Type       | Default       |
|------------------|--------------------------------------------------------------------|------------|---------------|
| Color            | Not work now                                                       | Color      | Color.Warning |
| Disabled         | Prevent the user interactions and make it appear lighter.          | bool       | false         |
| EmptyIcon        | Defines the non-selected icon name.                                | object     | 276           |
| EmptyIconStyle   | Defines the non-selected icon style.                               | IconStyle? | null          |
| FullIcon         | Defines the selected icon name.                                    | object     | 276           |
| FullIconStyle    | Defines the selected icon style.                                   | IconStyle? | null          |
| MaxValue         | Maximum rating value that is allowed to be selected. Default is 5. | int        | 5             |
| RatingItemsClass | User class names for RatingItems, separated by space               | string     |               |
| RatingItemsStyle | User styles for RatingItems.                                       | string     |               |
| ReadOnly         | Prevent the user interactions and make it appear normal.           | bool       | false         |
| SelectedValue    | Gets or sets the currently selected rating value.                  | int        | 0             |

### Events

| Event                | Description                                                                                                                                                                          | Type                     |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|
| GetTooltip           | Expression that provides the tooltip for the rating item to have additional user-friendly information.Remarks The expression receives the rating item Value to determine the result. | Func<int, RatingTooltip> |
| HoveredValueChanged  | Occurs after the Rating.HoveredValue has changed.                                                                                                                                    | EventCallback<int?>      |
| SelectedValueChanged | Occurs after the Rating.SelectedValue has changed.                                                                                                                                   | EventCallback<int>       |

### Methods

| Method          | Description                                       | Return   | Parameters   |
|-----------------|---------------------------------------------------|----------|--------------|
| IsSelectedRange | Indicates if item value is in the selected range. | bool     | int value    |
| IsHoveredRange  | Indicates if item value is in the hovered range.  | bool     | int value    |

###### On this page

#### 

## 