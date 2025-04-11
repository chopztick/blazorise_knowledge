# Blazorise DropdownList component

The DropdownList component allows you to select a value from a list of predefined items.

To be able to use DropdownList component you first need to install it.

## Installation

The DropdownList extension is part of the  NuGet package.

### NuGet

Install extension from NuGet.

```
Install-Package Blazorise.Components
```

### Example

Selected item: CN

Selected text: China

```
<DropdownList TItem="Country" TValue="string"
              Data="@Countries"
              TextField="@((item)=>item.Name)"
              ValueField="@((item)=>item.Iso)"
              @bind-SelectedValue="@selectedDropValue"
              Color="Color.Primary"
              MaxMenuHeight="200px">
    Select item
</DropdownList>

<Field Horizontal>
    <FieldBody ColumnSize="ColumnSize.Is12">
        Selected item: @selectedDropValue
    </FieldBody>
    <FieldBody ColumnSize="ColumnSize.Is12">
        Selected text: @Countries?.FirstOrDefault(x=> x.Iso == @selectedDropValue)?.Name
    </FieldBody>
</Field>
```

```
@code{
    [Inject]
    public CountryData CountryData { get; set; }
    public IEnumerable<Country> Countries;

    protected override async Task OnInitializedAsync()
    {
        Countries = await CountryData.GetDataAsync();
        await base.OnInitializedAsync();
    }

    string selectedDropValue { get; set; } = "CN";

}
```

### Checkbox Selection

The multiple selection feature in Blazorise's DropdownList component enables users to select multiple options from a dropdown menu via checkboxes. Each option in the menu comes with a checkbox for selection. Upon clicking the DropdownList, users can tick multiple checkboxes to select various options. This feature provides an efficient way of making multiple selections, enhancing user flexibility and interaction.

Selected values: AM,AF;

Selected texts: Armenia,Afghanistan

```
<DropdownList TItem="Country" TValue="string"
              Data="@Countries"
              TextField="@((item)=>item.Name)"
              ValueField="@((item)=>item.Iso)"
              @bind-SelectedValues="@selectedDropValues"
              SelectionMode="DropdownListSelectionMode.Checkbox"
              Color="Color.Primary"
              MaxMenuHeight="200px">
    Select item
</DropdownList>

<Field Horizontal>
    <FieldBody ColumnSize="ColumnSize.Is12">
        Selected values: @(selectedDropValues is not null ? string.Join( ',', selectedDropValues ) : "");
    </FieldBody>
    <FieldBody ColumnSize="ColumnSize.Is12">
        Selected texts: @(selectedDropValues is not null 
                        ? string.Join( ',', selectedDropValues.Select( x => Countries.FirstOrDefault( country => country.Iso == x )?.Name ?? string.Empty )) 
                        : string.Empty )
    </FieldBody>
</Field>
```

```
@code{
    [Inject]
    public CountryData CountryData { get; set; }
    public IEnumerable<Country> Countries;

    protected override async Task OnInitializedAsync()
    {
        Countries = await CountryData.GetDataAsync();
        await base.OnInitializedAsync();
    }

    private IReadOnlyList<string> selectedDropValues { get; set; } = new[] { "AM", "AF" };

}
```

## API

### Parameters

| Parameter          | Description                                                                                                   | Type                       | Default                           |
|--------------------|---------------------------------------------------------------------------------------------------------------|----------------------------|-----------------------------------|
| Attributes         | Captures all the custom attribute that are not part of Blazorise component.                                   | Dictionary<string, object> | null                              |
| ChildContent       | Specifies the content to be rendered inside this Components.DropdownList.                                     | RenderFragment             | null                              |
| Class              | Custom classname for dropdown element.                                                                        | string                     |                                   |
| Color              | Defines the color of toggle button.                                                                           | Color                      | null                              |
| Data               | Gets or sets the DropdownList data-source.                                                                    | IEnumerable<TItem>         | null                              |
| Direction          | Dropdown-menu slide direction.Possible values:Default, Down, Up, End, Start                                   | Direction                  | Default                           |
| Disabled           | If true, dropdown would not react to button click.                                                            | bool                       | false                             |
| DropdownToggleSize | Defines the size of toggle button.Possible values:Default, ExtraSmall, Small, Medium, Large, ExtraLarge       | Size                       | Default                           |
| ElementId          | Gets or sets the dropdown element id.                                                                         | string                     |                                   |
| MaxMenuHeight      | Sets the maximum height of the dropdown menu.                                                                 | string                     |                                   |
| RightAligned       | If true, a dropdown menu will be right aligned.                                                               | bool                       | false                             |
| SelectedValue      | Currently selected item value.                                                                                | TValue                     | null                              |
| SelectedValues     | Currently selected item values.                                                                               | IReadOnlyList<TValue>      | null                              |
| SelectionMode      | Gets or sets the Components.DropdownList Selection Mode.Possible values:Default, Checkbox                     | DropdownListSelectionMode  | DropdownListSelectionMode.Default |
| Style              | Custom styles for dropdown element.                                                                           | string                     |                                   |
| TabIndex           | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation. | int?                       | null                              |
| Virtualize         | Gets or sets whether the dropdown will use the Virtualize functionality.                                      | bool                       | false                             |

### Events

| Event                 | Description                                                          | Type                                 |
|-----------------------|----------------------------------------------------------------------|--------------------------------------|
| DisabledItem          | Method used to get the disabled items from the supplied data source. | Func<TItem, bool>                    |
| SelectedValueChanged  | Occurs after the selected value has changed.                         | EventCallback<TValue>                |
| SelectedValuesChanged | Occurs after the selected item values have changed.                  | EventCallback<IReadOnlyList<TValue>> |
| TextField             | Method used to get the display field from the supplied data source.  | Func<TItem, string>                  |
| ValueField            | Method used to get the value field from the supplied data source.    | Func<TItem, TValue>                  |

### Methods

| Method   | Description                                            | Return   | Parameters           |
|----------|--------------------------------------------------------|----------|----------------------|
| Focus    | Sets focus on the input element, if it can be focused. | Task     | bool scrollToElement |

###### On this page

#### 

## 