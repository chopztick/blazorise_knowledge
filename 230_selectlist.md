# Blazorise SelectList component

The SelectList component allows you to select a value from a list of predefined items.

To be able to use SelectList component you first need to install it.

## Installation

The SelectList extension is part of the  NuGet package.

### NuGet

Install extension from NuGet.

```
Install-Package Blazorise.Components
```

## Examples

### Basic Example

```
<SelectList TItem="MyCountryModel"
            TValue="int"
            Data="@IndexedCountries"
            TextField="@((item)=>item.Name)"
            ValueField="@((item)=>item.Id)"
            @bind-SelectedValue="@selectedListValue"
            DefaultItemText="Choose your country" />
```

```
@code {
    public class MyCountryModel
    {
        public int Id { get; set; }
        public string Name { get; set; }
    }

    static string[] Countries = { "Albania", "Andorra", "Armenia", "Austria", "Azerbaijan", "Belarus", "Belgium", "Bosnia & Herzegovina", "Bulgaria", "Croatia", "Cyprus", "Czech Republic", "Denmark", "Estonia", "Finland", "France", "Georgia", "Germany", "Greece", "Hungary", "Iceland", "Ireland", "Italy", "Kosovo", "Latvia", "Liechtenstein", "Lithuania", "Luxembourg", "Macedonia", "Malta", "Moldova", "Monaco", "Montenegro", "Netherlands", "Norway", "Poland", "Portugal", "Romania", "Russia", "San Marino", "Serbia", "Slovakia", "Slovenia", "Spain", "Sweden", "Switzerland", "Turkey", "Ukraine", "United Kingdom", "Vatican City" };
    static IEnumerable<MyCountryModel> IndexedCountries = Enumerable.Range( 1, Countries.Length ).Select( x => new MyCountryModel { Name = Countries[x - 1], Id = x } );

    int selectedListValue { get; set; } = 3;
}
```

### With Multiple Selections

Just like with a regular  component, add the  parameter to allow more than one option to be selected. Also, bind the  parameter.

```
<SelectList TItem="MyFruitModel"
            TValue="int"
            Data="@IndexedFruits"
            TextField="@((item)=>item.Name)"
            ValueField="@((item)=>item.Id)"
            Multiple
            @bind-SelectedValues="@selectedListValues"
            DefaultItemText="Choose your fruit" />
```

```
@code {
    public class MyFruitModel
    {
        public int Id { get; set; }
        public string Name { get; set; }
    }

    static string[] Fruits = { "Avocado", "Banana", "Blackberries", "Blueberries", "Cherries", "Cranberries", "Lemon", "Mango", "Orange", "Pineapple", "Watermelon" };
    static IEnumerable<MyFruitModel> IndexedFruits = Enumerable.Range( 1, Fruits.Length ).Select( x => new MyFruitModel { Name = Fruits[x - 1], Id = x } );

    IReadOnlyList<int> selectedListValues { get; set; }
}
```

## API

### Parameters

| Parameter                | Description                                                                                                   | Type                                    | Default   |
|--------------------------|---------------------------------------------------------------------------------------------------------------|-----------------------------------------|-----------|
| Attributes               | Captures all the custom attribute that are not part of Blazorise component.                                   | Dictionary<string, object>              | null      |
| ChildContent             | Specifies the content to be rendered inside this Components.SelectList.                                       | RenderFragment                          | null      |
| Class                    | Custom css class-names.                                                                                       | string                                  |           |
| Data                     | Gets or sets the select data-source.                                                                          | IEnumerable<TItem>                      | null      |
| DefaultItemDisabled      | If true, disables the default item.                                                                           | bool                                    | false     |
| DefaultItemHidden        | If true, disables the default item.                                                                           | bool                                    | false     |
| DefaultItemText          | Display text of the default select item.                                                                      | string                                  |           |
| DefaultItemValue         | Value of the default select item.                                                                             | TValue                                  | null      |
| Disabled                 | Add the disabled boolean attribute on an select to prevent user interactions and make it appear lighter.      | bool                                    | false     |
| ElementId                | Gets or sets the select element id.                                                                           | string                                  |           |
| Feedback                 | Placeholder for validation messages.                                                                          | RenderFragment                          | null      |
| MaxVisibleItems          | Specifies how many options should be shown at once.                                                           | int?                                    | null      |
| Multiple                 | Specifies that multiple items can be selected.                                                                | bool                                    | false     |
| SelectedValue            | Currently selected item value.                                                                                | TValue                                  | null      |
| SelectedValueExpression  | Gets or sets an expression that identifies the selected value.                                                | Expression<Func<TValue>>                | null      |
| SelectedValues           | Gets or sets the multiple selected item values.                                                               | IReadOnlyList<TValue>                   | null      |
| SelectedValuesExpression | Gets or sets an expression that identifies the selected value.                                                | Expression<Func<IReadOnlyList<TValue>>> | null      |
| Size                     | Size of a select field.                                                                                       | Size?                                   | null      |
| Style                    | Custom styles.                                                                                                | string                                  |           |
| TabIndex                 | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation. | int?                                    | null      |

### Events

| Event                 | Description                                                                                        | Type                                 |
|-----------------------|----------------------------------------------------------------------------------------------------|--------------------------------------|
| ItemDisabled          | Method used to determine if an item should be disabled.                                            | Func<TItem, bool>                    |
| SelectedValueChanged  | Occurs after the selected value has changed.                                                       | EventCallback<TValue>                |
| SelectedValuesChanged | Occurs when the selected items value has changed (only when Components.SelectList.Multiple==true). | EventCallback<IReadOnlyList<TValue>> |
| TextField             | Method used to get the display field from the supplied data source.                                | Func<TItem, string>                  |
| ValueField            | Method used to get the value field from the supplied data source.                                  | Func<TItem, TValue>                  |

### Methods

| Method   | Description                                            | Return   | Parameters           |
|----------|--------------------------------------------------------|----------|----------------------|
| Focus    | Sets focus on the input element, if it can be focused. | Task     | bool scrollToElement |

###### On this page

#### 

## 