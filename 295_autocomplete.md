# Blazorise Autocomplete component

The Autocomplete component offers simple and flexible type-ahead functionality.

📊 The Community License has a limitation of 1000 items. Unlock full access to all features with
    
        our premium plans.

The Autocomplete component provides suggestions while you type into the field. The component is in essence
    a text box which, at runtime, filters data in a drop-down by a Filter operator when a user captures a value.
    You may also enable FreeTyping and Autocomplete can be used to just provide suggestions based on user input.

## Quick Installation

The Autocomplete extension is part of the  NuGet package.

### Step 1: Download from NuGet

Install extension from NuGet:

```
Install-Package Blazorise.Components
```

### Step 2. Define Usings

In your main  add:

```
@using Blazorise.Components
```

## Examples

### Searching single value

Selected search value:

Selected text value:

```
<Autocomplete TItem="Country"
              TValue="string"
              Data="@Countries"
              TextField="@(( item ) => item.Name)"
              ValueField="@(( item ) => item.Iso)"
              @bind-SelectedValue="@selectedSearchValue"
              @bind-SelectedText="selectedAutoCompleteText"
              Placeholder="Search..."
              Filter="AutocompleteFilter.StartsWith"
              FreeTyping
              CustomFilter="@(( item, searchValue ) => item.Name.IndexOf( searchValue, 0, StringComparison.CurrentCultureIgnoreCase ) >= 0 )">
    <NotFoundContent> Sorry... @context was not found! :( </NotFoundContent>
</Autocomplete>

<Field Horizontal>
    <FieldBody ColumnSize="ColumnSize.Is12">
        Selected search value: @selectedSearchValue
    </FieldBody>
    <FieldBody ColumnSize="ColumnSize.Is12">
        Selected text value: @selectedAutoCompleteText
    </FieldBody>
</Field>
```

```
@code {
    [Inject]
    public CountryData CountryData { get; set; }
    public IEnumerable<Country> Countries;

    protected override async Task OnInitializedAsync()
    {
        Countries = await CountryData.GetDataAsync();
        await base.OnInitializedAsync();
    }

    public string selectedSearchValue { get; set; }
    public string selectedAutoCompleteText { get; set; }
}
```

### Searching multiple values

Selected Values: AE,AL

Selected Texts: United Arab Emirates,Albania

```
<Autocomplete TItem="Country"
              TValue="string"
              Data="@Countries"
              TextField="@(( item ) => item.Name)"
              ValueField="@(( item ) => item.Iso)"
              Placeholder="Search..."
              SelectionMode="AutocompleteSelectionMode.Multiple"
              FreeTyping
              @bind-SelectedValues="multipleSelectionData"
              @bind-SelectedTexts="multipleSelectionTexts">
</Autocomplete>

<Field Horizontal>
    <FieldBody ColumnSize="ColumnSize.Is12">
        Selected Values: @string.Join(',', multipleSelectionData)
    </FieldBody>
    <FieldBody ColumnSize="ColumnSize.Is12">
        Selected Texts: @(multipleSelectionTexts == null ? null : string.Join(',', multipleSelectionTexts))
    </FieldBody>
</Field>
```

```
@code {
    [Inject]
    public CountryData CountryData { get; set; }
    public IEnumerable<Country> Countries;

    protected override async Task OnInitializedAsync()
    {
        Countries = await CountryData.GetDataAsync();
        multipleSelectionData = new List<string>() { Countries.ElementAt( 1 ).Iso, Countries.ElementAt( 3 ).Iso };
        await base.OnInitializedAsync();
    }

    List<string> multipleSelectionData;
    List<string> multipleSelectionTexts;
}
```

### Searching with data on demand (ReadData)

Make sure to check the  before commiting your values to . This will make sure to avoid race conditions and keep your  updated according to the user's last key stroke.

Selected search value:

Selected text value:

```
<Autocomplete TItem="Country"
              TValue="string"
              Data="@ReadDataCountries"
              ReadData="@OnHandleReadData"
              TextField="@(( item ) => item.Name)"
              ValueField="@(( item ) => item.Iso)"
              @bind-SelectedValue="@selectedSearchValue"
              @bind-SelectedText="selectedAutoCompleteText"
              Placeholder="Search..."
              FreeTyping>
    <NotFoundContent> Sorry... @context was not found! :( </NotFoundContent>
</Autocomplete>

<Field Horizontal>
    <FieldBody ColumnSize="ColumnSize.Is12">
        Selected search value: @selectedSearchValue
    </FieldBody>
    <FieldBody ColumnSize="ColumnSize.Is12">
        Selected text value: @selectedAutoCompleteText
    </FieldBody>
</Field>
```

```
@code {
    [Inject]
    public CountryData CountryData { get; set; }
    public IEnumerable<Country> Countries;
    public IEnumerable<Country> ReadDataCountries;

    private Random random = new();

    public string selectedSearchValue { get; set; }
    public string selectedAutoCompleteText { get; set; }

    protected override async Task OnInitializedAsync()
    {
        Countries = await CountryData.GetDataAsync();
        await base.OnInitializedAsync();
    }

    private async Task OnHandleReadData( AutocompleteReadDataEventArgs autocompleteReadDataEventArgs )
    {
        if ( !autocompleteReadDataEventArgs.CancellationToken.IsCancellationRequested )
        {
            await Task.Delay( random.Next( 100 ) );
            if ( !autocompleteReadDataEventArgs.CancellationToken.IsCancellationRequested )
            {
                ReadDataCountries = Countries.Where( x => x.Name.StartsWith( autocompleteReadDataEventArgs.SearchValue, StringComparison.InvariantCultureIgnoreCase ) );
            }
        }
    }
}
```

### Extending with custom item content

Customize the way you display the Autocomplete items by providing .

Selected search value:

Selected text value:

```
<Autocomplete TItem="Country"
              TValue="string"
              Data="@Countries"
              TextField="@(( item ) => item.Name)"
              ValueField="@(( item ) => item.Iso)"
              @bind-SelectedValue="@selectedSearchValue"
              @bind-SelectedText="selectedAutoCompleteText"
              Placeholder="Search..."
              Filter="AutocompleteFilter.StartsWith"
              FreeTyping
              CustomFilter="@(( item, searchValue ) => item.Name.IndexOf( searchValue, 0, StringComparison.CurrentCultureIgnoreCase ) >= 0 )">
    <NotFoundContent> Sorry... @context was not found! :( </NotFoundContent>
    <ItemContent>
        <Div Flex="Flex.InlineFlex.JustifyContent.Between" Width="Width.Is100">
            <Heading Margin="Margin.Is2.FromBottom">@context.Value</Heading>
            <Small>@context.Item.Capital</Small>
        </Div>
        <Paragraph Margin="Margin.Is2.FromBottom">@context.Text</Paragraph>
    </ItemContent>
</Autocomplete>

<Field Horizontal>
    <FieldBody ColumnSize="ColumnSize.Is12">
        Selected search value: @selectedSearchValue
    </FieldBody>
    <FieldBody ColumnSize="ColumnSize.Is12">
        Selected text value: @selectedAutoCompleteText
    </FieldBody>
</Field>
```

```
@code {
    [Inject]
    public CountryData CountryData { get; set; }
    public IEnumerable<Country> Countries;

    protected override async Task OnInitializedAsync()
    {
        Countries = await CountryData.GetDataAsync();
        await base.OnInitializedAsync();
    }
    string selectedSearchValue { get; set; }
    string selectedAutoCompleteText { get; set; }
}
```

### Suggesting already selected items &amp;&amp; Checkbox support

You can use  to suggest already selected items, and optionally use  to additionally add checkbox selection.
         Make sure to set  to false if you want to keep the dropdown open whenever an item is selected.

Selected Values: AE,AL

Selected Texts: United Arab Emirates,Albania

```
<Autocomplete TItem="Country"
              TValue="string"
              Data="@Countries"
              TextField="@(( item ) => item.Name)"
              ValueField="@(( item ) => item.Iso)"
              Placeholder="Search..."
              SelectionMode="AutocompleteSelectionMode.Checkbox"
              CloseOnSelection="false"
              @bind-SelectedValues="multipleSelectionData"
              @bind-SelectedTexts="multipleSelectionTexts">
</Autocomplete>

<Field Horizontal>
    <FieldBody ColumnSize="ColumnSize.Is12">
        Selected Values: @string.Join(',', multipleSelectionData)
    </FieldBody>
    <FieldBody ColumnSize="ColumnSize.Is12">
        Selected Texts: @(multipleSelectionTexts == null ? null : string.Join(',', multipleSelectionTexts))
    </FieldBody>
</Field>
```

```
@code {
    [Inject]
    public CountryData CountryData { get; set; }
    public IEnumerable<Country> Countries;

    protected override async Task OnInitializedAsync()
    {
        Countries = await CountryData.GetDataAsync();
        multipleSelectionData = new List<string>() { Countries.ElementAt( 1 ).Iso, Countries.ElementAt( 3 ).Iso };
        await base.OnInitializedAsync();
    }

    List<string> multipleSelectionData;
    List<string> multipleSelectionTexts;
}
```

### Highlight search text

Autocomplete  is a feature that allows you to highlight the search text that you have entered in a dropdown list of items. When you start typing in the search field, the dropdown list of items will automatically be filtered to show only the items that match the search text. The search text will also be highlighted in the dropdown list of items, so that you can easily see which items match your search. This can be a useful feature when you are trying to find a specific item in a long list of items, as it allows you to quickly locate the item you are looking for.

```
<Autocomplete TItem="Country"
              TValue="string"
              Data="@Countries"
              TextField="@(( item ) => item.Name)"
              ValueField="@(( item ) => item.Iso)"
              Placeholder="Search..."
              HighlightSearch>
    <NotFoundContent> Sorry... @context was not found! :( </NotFoundContent>
</Autocomplete>
```

```
@code {
    [Inject]
    public CountryData CountryData { get; set; }
    public IEnumerable<Country> Countries;

    protected override async Task OnInitializedAsync()
    {
        Countries = await CountryData.GetDataAsync();
        await base.OnInitializedAsync();
    }
}
```

### Virtualize

Blazorise Autocomplete's Virtualize feature allows for loading data on demand while scrolling, which improves the performance of the component when working with large datasets. With Virtualize, the Autocomplete component only loads the items that are currently visible in the list, and as the user scrolls, more items are loaded in the background. This allows for a much faster and smoother user experience, especially when working with large lists of items.

This feature can be easily enabled by setting the Virtualize property to "true" on the Autocomplete component.

```
<Autocomplete TItem="Country"
              TValue="string"
              Data="@Countries"
              TextField="@(( item ) => item.Name)"
              ValueField="@((item) => item.Iso)"
              @bind-SelectedValue="selectedSearchValue"
              Placeholder="Search..."
              Virtualize>
    <NotFoundContent> Sorry... @context was not found! :( </NotFoundContent>
</Autocomplete>
```

```
@code {
    [Inject]
    public CountryData CountryData { get; set; }
    public IEnumerable<Country> Countries;

    protected override async Task OnInitializedAsync()
    {
        Countries = await CountryData.GetDataAsync();
        await base.OnInitializedAsync();
    }

    public string selectedSearchValue { get; set; }
}
```

### Virtualize with ReadData

Blazorise Autocomplete's Virtualize and ReadData features work together to handle large datasets efficiently.
            The ReadData event allows you to load only the data needed for the current interaction, without loading the entire dataset into memory.
            Meanwhile, the Virtualize property ensures that only the visible items are rendered in the DOM, significantly improving performance when working with large lists.

In the provided example, the dataset is represented using IEnumerable for simplicity, but in real-world scenarios, you would typically use IQueryable.
            This allows for true deferred execution, ensuring only the required data is fetched and processed.

To enable Virtualize with ReadData, you must also set the TotalItems property.
            The TotalItems value represents the total count of items in your dataset and is required for proper virtualization.

```
<Autocomplete TItem="Country"
              TValue="string"
              Data="@ReadDataCountries"
              TotalItems="totalCountries"
              TextField="@(( item ) => item.Name)"
              ValueField="@((item) => item.Iso)"
              @bind-SelectedValue="@SelectedSearchValue"
              Placeholder="Search..."
              Virtualize
              ReadData="@OnHandleReadData">
    <NotFoundContent> Sorry... @context was not found! :( </NotFoundContent>
</Autocomplete>
```

```
@code {
    [Inject]
    public CountryData CountryData { get; set; }

    public IEnumerable<Country> Countries;
    IEnumerable<Country> ReadDataCountries;
    int totalCountries;

    public string SelectedSearchValue { get; set; }

    protected override async Task OnInitializedAsync()
    {
        Countries = await CountryData.GetDataAsync();
        totalCountries = Countries.Count();
        await base.OnInitializedAsync();
    }

    private Task OnHandleReadData( AutocompleteReadDataEventArgs autocompleteReadDataEventArgs )
    {
        if ( !autocompleteReadDataEventArgs.CancellationToken.IsCancellationRequested )
        {
            ReadDataCountries = Countries
                .Where(x => x.Name.StartsWith(autocompleteReadDataEventArgs.SearchValue, StringComparison.InvariantCultureIgnoreCase))
                .Skip(autocompleteReadDataEventArgs.VirtualizeOffset).Take(autocompleteReadDataEventArgs.VirtualizeCount);
        }

        return Task.CompletedTask;
    }
}
```

## API

### Parameters

| Parameter                  | Description                                                                                                                                                                                                                                                                                                                                                                          | Type                                                  | Default                           |
|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------|-----------------------------------|
| Attributes                 | Captures all the custom attribute that are not part of Blazorise component.                                                                                                                                                                                                                                                                                                          | Dictionary<string, object>                            | null                              |
| AutoPreSelect              | Gets or sets whether Components.Autocomplete auto preselects the first item displayed on the dropdown.     Defauls to true.                                                                                                                                                                                                                                                          | bool                                                  | true                              |
| AutoSelectFirstItem        | Gets or sets the whether first item in the list should be selected                                                                                                                                                                                                                                                                                                                   | bool                                                  | false                             |
| ChildContent               | Specifies the content to be rendered inside this Components.Autocomplete.                                                                                                                                                                                                                                                                                                            | RenderFragment                                        | null                              |
| Class                      | Custom class-name for dropdown element.                                                                                                                                                                                                                                                                                                                                              | string                                                |                                   |
| CloseOnSelection           | Specifies whether Components.Autocomplete dropdown closes on selection. This is only evaluated when multiple selection is set.     Defauls to true.                                                                                                                                                                                                                                  | bool                                                  | true                              |
| ConfirmKey                 | Gets or sets an array of the keyboard pressed values for the ConfirmKey.     If this is null or empty, there will be no confirmation key.     Defauls to: { "Enter", "NumpadEnter", "Tab" }.Remarks If the value has a printed representation, this attribute's value is the same as the char attribute.     Otherwise, it's one of the key value strings specified in 'Key values'. | string[]                                              | new[] { "Enter", "NumpadEnter" }  |
| CurrentSearch              | Gets or sets the currently selected item text.                                                                                                                                                                                                                                                                                                                                       | string                                                |                                   |
| Data                       | Gets or sets the autocomplete data-source.                                                                                                                                                                                                                                                                                                                                           | IEnumerable<TItem>                                    | null                              |
| Debounce                   | If true the entered text will be slightly delayed before submitting it to the internal value.                                                                                                                                                                                                                                                                                        | bool?                                                 | null                              |
| DebounceInterval           | Interval in milliseconds that entered text will be delayed from submitting to the internal value.                                                                                                                                                                                                                                                                                    | int?                                                  | null                              |
| Disabled                   | Prevents a user from entering a value to the search field.                                                                                                                                                                                                                                                                                                                           | bool                                                  | false                             |
| ElementId                  | Gets or sets the dropdown element id.                                                                                                                                                                                                                                                                                                                                                | string                                                |                                   |
| Filter                     | Defines the method by which the search will be done.Possible values:StartsWith, Contains                                                                                                                                                                                                                                                                                             | AutocompleteFilter                                    | AutocompleteFilter.StartsWith     |
| FreeTyping                 | Allows the value to not be on the data source.     The value will be bound to the Components.Autocomplete.SelectedText                                                                                                                                                                                                                                                               | bool                                                  | false                             |
| FreeTypingNotFoundTemplate | Specifies the not found content to be rendered inside this Components.Autocomplete when no data is found and FreeTyping is enabled.                                                                                                                                                                                                                                                  | RenderFragment<string>                                | null                              |
| HighlightSearch            | If true, the searched text will be highlighted in the dropdown list items based on Components.Autocomplete.Search value.                                                                                                                                                                                                                                                             | bool                                                  | false                             |
| Immediate                  | If true the text in will be changed after each key press.Remarks Note that setting this will override global settings in BlazoriseOptions.Immediate.                                                                                                                                                                                                                                 | bool?                                                 | null                              |
| ItemContent                | Specifies the item content to be rendered inside each dropdown item.                                                                                                                                                                                                                                                                                                                 | RenderFragment<ItemContext<TItem, TValue>>            | null                              |
| MaxEntryLength             | Specifies the maximum number of characters allowed in the input element.                                                                                                                                                                                                                                                                                                             | int?                                                  | null                              |
| MaxMenuHeight              | Sets the maximum height of the dropdown menu.                                                                                                                                                                                                                                                                                                                                        | string                                                |                                   |
| MinLength                  | The minimum number of characters a user must type before a search is performed. Set this to 0 to make the Autocomplete function like a dropdown.                                                                                                                                                                                                                                     | int                                                   | 1                                 |
| Multiple                   | Allows for multiple selection.                                                                                                                                                                                                                                                                                                                                                       | bool                                                  | false                             |
| MultipleBadgeColor         | Sets the Badge color for the multiple selection values. Used when multiple selection is set.                                                                                                                                                                                                                                                                                         | Color                                                 | Primary                           |
| MultipleDisabledBadgeColor | Sets the disabled Badge color for the multiple selection values. Used when multiple selection is set.                                                                                                                                                                                                                                                                                | Color                                                 | Light                             |
| NotFoundContent            | Specifies the not found content to be rendered inside this Components.Autocomplete when no data is found.                                                                                                                                                                                                                                                                            | RenderFragment<string>                                | null                              |
| Placeholder                | Sets the placeholder for the empty search.                                                                                                                                                                                                                                                                                                                                           | string                                                |                                   |
| PositionStrategy           | Defines the positioning strategy of the dropdown menu as a 'floating' element.Possible values:Absolute, Fixed                                                                                                                                                                                                                                                                        | DropdownPositionStrategy                              | Absolute                          |
| Search                     | Gets or sets the currently selected item text.                                                                                                                                                                                                                                                                                                                                       | string                                                |                                   |
| SearchBackground           | Defines the background color of the search field.                                                                                                                                                                                                                                                                                                                                    | Background                                            | null                              |
| SearchClass                | Defines class for search field.                                                                                                                                                                                                                                                                                                                                                      | string                                                |                                   |
| SearchStyle                | Defines style for search field.                                                                                                                                                                                                                                                                                                                                                      | string                                                |                                   |
| SearchTextColor            | Defines the text color of the search field.                                                                                                                                                                                                                                                                                                                                          | TextColor                                             | null                              |
| SelectedText               | Gets or sets the currently selected item text.                                                                                                                                                                                                                                                                                                                                       | string                                                |                                   |
| SelectedTexts              | Currently selected items texts.     Used when multiple selection is set.                                                                                                                                                                                                                                                                                                             | List<string>                                          | null                              |
| SelectedValue              | Currently selected item value.                                                                                                                                                                                                                                                                                                                                                       | TValue                                                | null                              |
| SelectedValues             | Currently selected items values.     Used when multiple selection is set.                                                                                                                                                                                                                                                                                                            | List<TValue>                                          | null                              |
| SelectionMode              | Gets or sets the Components.Autocomplete Selection Mode.Possible values:Default, Multiple, Checkbox                                                                                                                                                                                                                                                                                  | AutocompleteSelectionMode                             | AutocompleteSelectionMode.Default |
| Size                       | Size of a search field.                                                                                                                                                                                                                                                                                                                                                              | Size?                                                 | null                              |
| Style                      | Custom styles for dropdown element.                                                                                                                                                                                                                                                                                                                                                  | string                                                |                                   |
| SuggestSelectedItems       | Suggests already selected option(s) when presenting the options.                                                                                                                                                                                                                                                                                                                     | bool                                                  | false                             |
| TabIndex                   | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation.                                                                                                                                                                                                                                                                        | int?                                                  | null                              |
| TagTemplate                | Specifies the content to be rendered for each tag (multiple selected item).                                                                                                                                                                                                                                                                                                          | RenderFragment<AutocompleteTagContext<TItem, TValue>> | null                              |
| TotalItems                 | Gets or sets the total number of items. Used only when Components.Autocomplete.ReadData and Components.Autocomplete.Virtualize is used to load the data.Remarks This field must be set only when Components.Autocomplete.ReadData and Components.Autocomplete.Virtualize is used to load the data.                                                                                   | int?                                                  | null                              |
| Virtualize                 | Gets or sets whether the Autocomplete will use the Virtualize functionality.                                                                                                                                                                                                                                                                                                         | bool                                                  | false                             |

### Events

| Event                 | Description                                                                                 | Type                                              |
|-----------------------|---------------------------------------------------------------------------------------------|---------------------------------------------------|
| AsyncValidator        | Asynchronously validates the selected value.                                                | Func<ValidatorEventArgs, CancellationToken, Task> |
| Closed                | Event handler used to detect when the autocomplete is closed.                               | EventCallback<AutocompleteClosedEventArgs>        |
| CurrentSearchChanged  | Occurs on every search text change.                                                         | EventCallback<string>                             |
| CustomFilter          | Handler for custom filtering on Autocomplete's data source.                                 | Func<TItem, string, bool>                         |
| NotFound              | Occurs on every search text change where the data does not contain the text being searched. | EventCallback<string>                             |
| Opened                | Event handler used to detect when the autocomplete is opened.                               | EventCallback                                     |
| ReadData              | Event handler used to load data manually based on the current search value.                 | EventCallback<AutocompleteReadDataEventArgs>      |
| SearchBlur            | The blur event fires when the search box has lost focus.                                    | EventCallback<FocusEventArgs>                     |
| SearchChanged         | Occurs on every search text change.                                                         | EventCallback<string>                             |
| SearchFocus           | Occurs when the search box gains or loses focus.                                            | EventCallback<FocusEventArgs>                     |
| SearchKeyDown         | Occurs when a key is pressed down while the search box has focus.                           | EventCallback<KeyboardEventArgs>                  |
| SearchTextChanged     | Occurs after the search box text has changed.                                               | EventCallback<string>                             |
| SelectedTextChanged   | Gets or sets the currently selected item text.                                              | EventCallback<string>                             |
| SelectedTextsChanged  | Occurs after the selected texts have changed.     Used when multiple selection is set.      | EventCallback<List<string>>                       |
| SelectedValueChanged  | Occurs after the selected value has changed.                                                | EventCallback<TValue>                             |
| SelectedValuesChanged | Occurs after the selected values have changed.     Used when multiple selection is set.     | EventCallback<List<TValue>>                       |
| TextField             | Method used to get the display field from the supplied data source.                         | Func<TItem, string>                               |
| Validator             | Validation handler used to validate selected value.                                         | Action<ValidatorEventArgs>                        |
| ValueField            | Method used to get the value field from the supplied data source.                           | Func<TItem, TValue>                               |

### Methods

| Method                     | Description                                                                                                                                 | Return             | Parameters                                              |
|----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|--------------------|---------------------------------------------------------|
| ScrollItemIntoView         | Scrolls an item into view.                                                                                                                  | Task               | int index                                               |
| Reload                     | Triggers the reload of the Components.Autocomplete data.     Makes sure not to reload if the Components.Autocomplete is in a loading state. | Task               | CancellationToken cancellationToken                     |
| AddMultipleTextAndValue    | Adds a Multiple Selection.                                                                                                                  | Task               | TValue value                                            |
| RemoveMultipleTextAndValue | Removes a Multiple Selection.                                                                                                               | Task               | string text                                             |
| RemoveMultipleTextAndValue | Removes a Multiple Selection.                                                                                                               | Task               | TValue value                                            |
| ResetSelected              | Clears the current selection.                                                                                                               | Task               |                                                         |
| Clear                      | Clears the selected value and the search field.                                                                                             | Task               |                                                         |
| Focus                      | Sets focus on the input element, if it can be focused.                                                                                      | Task               | bool scrollToElement                                    |
| Close                      | Closes the Components.Autocomplete Dropdown.                                                                                                | Task               |                                                         |
| Close                      | Closes the Components.Autocomplete Dropdown.                                                                                                | Task               | CloseReason closeReason                                 |
| IsSafeToClose              | Determines if Autocomplete can be closed                                                                                                    | Task<bool>         | string elementId, CloseReason closeReason, bool isChild |
| OpenDropdown               | Opens the Components.Autocomplete Dropdown.                                                                                                 | Task               |                                                         |
| IsSelectedvalue            | Gets whether the  is selected.                                                                                                              | bool               | TValue value                                            |
| IsSelectedItem             | Gets whether the  is selected.                                                                                                              | bool               | TItem item                                              |
| GetItemByValue             | Gets a  from Components.Autocomplete.Data by using the provided Components.Autocomplete.ValueField.                                         | TItem              | TValue value                                            |
| GetItemByText              | Gets a  from Components.Autocomplete.Data by using the provided Components.Autocomplete.TextField.                                          | TItem              | string text                                             |
| GetItemsByText             | Gets multiple items from Components.Autocomplete.Data by using the provided Components.Autocomplete.TextField.                              | IEnumerable<TItem> | string text                                             |

###### On this page

#### 

## 