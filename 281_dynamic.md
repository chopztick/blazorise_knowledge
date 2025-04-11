# Blazorise DataGrid: Dynamic Data Binding

The Blazorise DataGrid component offers the ability to bind to dynamic data, providing enhanced flexibility for various applications.

### Basic Example

To ensure the  correctly interprets the structure and type of your dynamic data during specific operations, such as creating new items or aggregating data, you need to define a representation within the  function. Below is an illustrative example.

| New        | #   | First Name   | Last Name   | Email                      |  City           | Zip        | Date Of Birth   |   Childrens | Gender   | Salary         | Active   |
|------------|-----|--------------|-------------|----------------------------|-----------------|------------|-----------------|-------------|----------|----------------|----------|
| EditDelete | 1   | Samuel       | Collier     | Samuel.Collier62@gmail.com | New Lura        | 91848-4714 | 26.08.1970      |           3 | M        | 86 030,41 €    |          |
| EditDelete | 2   | Irvin        | Ziemann     | Irvin.Ziemann@gmail.com    | Modestomouth    | 16505-8405 | 25.05.1974      |           3 | M        | 61 781,31 €    |          |
| EditDelete | 3   | Gerald       | Pollich     | Gerald82@yahoo.com         | Theresashire    | 28612      | 29.04.1969      |           1 | M        | 58 810,75 €    |          |
| EditDelete | 4   | Cora         | Conn        | Cora27@yahoo.com           | North Art       | 10437-2253 | 12.02.1984      |           5 | D        | 84 414,66 €    |          |
| EditDelete | 5   | Alfonso      | D'Amore     | Alfonso.DAmore@hotmail.com | East Carolefort | 87912-3933 | 06.11.1983      |           5 | F        | 69 318,29 €    |          |
|            |     |              |             | Total emails: 25           |                 |            |                 |          78 |          | 1 793 183,29 € | 14       |

- First
- Prev
- 1
- 2
- 3
- 4
- 5
- 12345
- Next
- Last
- 5102550100250
- items per page

1 - 5 of 25 items

25 items

```
@using System.Dynamic

<DataGrid TItem="ExpandoObject"
          Data="inMemoryData"
          Responsive
          ShowPager
          ShowPageSizes
          PageSize="5"
          Editable
          EditMode="DataGridEditMode.Inline"
          NewItemCreator="NewItemCreator">
    <DataGridAggregates>
        <DataGridAggregate Field="Email" Aggregate="DataGridAggregateType.Count">
            <DisplayTemplate>
                @($"Total emails: {context.Value}")
            </DisplayTemplate>
        </DataGridAggregate>
        <DataGridAggregate Field="Salary" Aggregate="DataGridAggregateType.Sum" DisplayFormat="{0:C}" DisplayFormatProvider="@System.Globalization.CultureInfo.GetCultureInfo("fr-FR")" />
        <DataGridAggregate Field="IsActive" Aggregate="DataGridAggregateType.TrueCount" />
        <DataGridAggregate Field="Childrens" Aggregate="DataGridAggregateType.Sum" />
    </DataGridAggregates>
    <DataGridColumns>
        <DataGridCommandColumn></DataGridCommandColumn>
        <DataGridColumn Editable TextAlignment="TextAlignment.Center" Field="@nameof( Employee.Id )" Caption="#" Width="60px" />
        <DataGridColumn Editable Field="FirstName" Caption="First Name">
        </DataGridColumn>
        <DataGridColumn Editable Field="LastName" Caption="Last Name" />
        <DataGridColumn Editable Field="Email" Caption="Email" />
        <DataGridColumn Editable Field="City" Caption="City">
            <CaptionTemplate>
                <Icon Name="IconName.City" /> @context.Caption
            </CaptionTemplate>
        </DataGridColumn>
        <DataGridColumn Editable Field="Zip" Caption="Zip">
        </DataGridColumn>
        <DataGridDateColumn Field="DateOfBirth" DisplayFormat="{0:dd.MM.yyyy}" Caption="Date Of Birth" Editable />
        <DataGridNumericColumn Field="Childrens" Caption="Childrens" ReverseSorting="true" Editable Filterable="false" />
        <DataGridSelectColumn Field="Gender" Caption="Gender" Editable Data="EmployeeData.Genders" ValueField="(x) => ((Gender)x).Code" TextField="(x) => ((Gender)x).Description" />
        <DataGridColumn Field="Salary" Caption="Salary" Editable Width="140px" DisplayFormat="{0:C}" DisplayFormatProvider="@System.Globalization.CultureInfo.GetCultureInfo("fr-FR")" TextAlignment="TextAlignment.End">
        </DataGridColumn>
        <DataGridCheckColumn Field="IsActive" Caption="Active" Editable Filterable="false">
            <DisplayTemplate>
                <Check TValue="bool" Checked='(context as dynamic).IsActive' Disabled ReadOnly />
            </DisplayTemplate>
        </DataGridCheckColumn>
    </DataGridColumns>
</DataGrid>
```

```
@code {

    [Inject] EmployeeData EmployeeData { get; set; }

    private List<ExpandoObject> inMemoryData;

    protected override async Task OnInitializedAsync()
    {
        inMemoryData = new();
        var data = ( await EmployeeData.GetDataAsync().ConfigureAwait( false ) ).Take( 25 );

        foreach ( var item in data )
        {

            IDictionary<string, object> expando = new ExpandoObject();

            foreach ( var property in typeof( Employee ).GetProperties() )
            {
                expando.Add( property.Name, property.GetValue( item ) );
            }
            inMemoryData.Add( (ExpandoObject)expando );
        }


        await base.OnInitializedAsync();
    }

    private ExpandoObject NewItemCreator()
    {
        IDictionary<string, object> expando = new ExpandoObject();

        foreach ( var property in typeof( Employee ).GetProperties() )
        {
            expando.Add( property.Name, property.PropertyType.IsValueType ? Activator.CreateInstance( property.PropertyType ) : null );
        }

        return (ExpandoObject)expando;
    }
}
```

### Auto Generate Columns Example

The Blazorise DataGrid also supports auto-generating columns based on the data structure. This feature simplifies the process of displaying data by automatically creating columns that match the properties of the bound data objects.

- First
- Prev
- 1
- 2
- 3
- 4
- 5
- 12345
- Next
- Last
- 5102550100250
- items per page

1 - 5 of 25 items

25 items

```
@using System.Dynamic

<DataGrid TItem="ExpandoObject"
          Data="inMemoryData"
          Responsive
          ShowPager
          ShowPageSizes
          PageSize="5"
          Editable
          EditMode="DataGridEditMode.Inline"
          NewItemCreator="NewItemCreator" />
```

```
@code {
    [Inject] EmployeeData EmployeeData { get; set; }

    private List<ExpandoObject> inMemoryData;

    protected override async Task OnInitializedAsync()
    {
        inMemoryData = new();
        var data = ( await EmployeeData.GetDataAsync().ConfigureAwait( false ) ).Take( 25 );

        foreach ( var item in data )
        {

            IDictionary<string, object> expando = new ExpandoObject();

            foreach ( var property in typeof( Employee ).GetProperties() )
            {
                expando.Add( property.Name, property.GetValue( item ) );
            }
            inMemoryData.Add( (ExpandoObject)expando );
        }


        await base.OnInitializedAsync();
    }

    private ExpandoObject NewItemCreator()
    {
        IDictionary<string, object> expando = new ExpandoObject();

        foreach ( var property in typeof( Employee ).GetProperties() )
        {
            expando.Add( property.Name, property.PropertyType.IsValueType ? Activator.CreateInstance( property.PropertyType ) : null );
        }

        return (ExpandoObject)expando;
    }
}
```

## API

See the documentation below for a complete reference to all of the props and classes available to the components mentioned here.

&lt;DataGrid /&gt;

###### On this page

#### 

## 