# Blazorise DataGrid: State Management

You are able to manage the state of the DataGrid by using the provided GetState and LoadState methods.

## Example

### Get And Load State

In the following example,

- we are using the LoadState method to load the DataGrid state from the LocalStorage if available.
- We are using the GetState method to save the DataGrid state to the LocalStorage in order to load at a later date.
- The page checks the LocalStorage on first render and loads the saved state if available.

Load State
Save State
Reset State

- First
- Prev
- 1
- 2
- 3
- 123
- Next
- Last
- 5102550100250
- items per page

1 - 10 of 25 items

25 items

| #   | First Name   | Last Name   | Email                       |  City             | Zip        | Date Of Birth   | Childrens   | Gender            | Salary      | Active   |
|-----|--------------|-------------|-----------------------------|-------------------|------------|-----------------|-------------|-------------------|-------------|----------|
|     |              |             |                             |                   |            |                 |             | MaleFemaleDiverse |             |          |
| 1   | Samuel       | Collier     | Samuel.Collier62@gmail.com  | New Lura          | 91848-4714 | 26.08.1970      | 3           | M                 | 86 030,41 € |          |
| 2   | Irvin        | Ziemann     | Irvin.Ziemann@gmail.com     | Modestomouth      | 16505-8405 | 25.05.1974      | 3           | M                 | 61 781,31 € |          |
| 3   | Gerald       | Pollich     | Gerald82@yahoo.com          | Theresashire      | 28612      | 29.04.1969      | 1           | M                 | 58 810,75 € |          |
| 4   | Cora         | Conn        | Cora27@yahoo.com            | North Art         | 10437-2253 | 12.02.1984      | 5           | D                 | 84 414,66 € |          |
| 5   | Alfonso      | D'Amore     | Alfonso.DAmore@hotmail.com  | East Carolefort   | 87912-3933 | 06.11.1983      | 5           | F                 | 69 318,29 € |          |
| 6   | Jessie       | Wilkinson   | Jessie_Wilkinson@gmail.com  | Mayrafurt         | 34306      | 02.10.1995      | 4           | M                 | 78 566,12 € |          |
| 7   | Gregory      | Renner      | Gregory63@hotmail.com       | West Marcelleside | 57895      | 15.03.1978      | 1           | F                 | 57 456,82 € |          |
| 8   | Maryann      | Hilpert     | Maryann.Hilpert12@gmail.com | Boehmview         | 38859-0368 | 01.07.1970      | 5           | D                 | 89 153,38 € |          |
| 9   | Merle        | Pacocha     | Merle3@gmail.com            | North Erlingport  | 48154-3034 | 24.06.1993      | 5           | F                 | 55 349,94 € |          |
| 10  | Angelina     | Ward        | Angelina42@gmail.com        | Melyssaview       | 72291-1146 | 18.09.1992      | 3           | D                 | 73 625,86 € |          |

```
<Paragraph>
    <Button Color="Color.Primary" Clicked="LoadState">Load State</Button>
    <Button Color="Color.Success" Clicked="SaveState">Save State</Button>
    <Button Color="Color.Light" Clicked="ResetState">Reset State</Button>
</Paragraph>

<DataGrid @ref="dataGridRef"
          TItem="Employee"
          Data="inMemoryData"
          Responsive
          Editable
          Filterable
          ShowPager
          ShowPageSizes
          ShowColumnChooser
          PagerPosition="DataGridPagerPosition.Top">
    <DataGridColumns>
        <DataGridColumn TextAlignment="TextAlignment.Center" TItem="Employee" Field="@nameof( Employee.Id )" Caption="#" Width="60px" />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.FirstName )" Caption="First Name">
        </DataGridColumn>
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.LastName )" Caption="Last Name" />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.Email )" Caption="Email" />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.City )" Caption="City">
            <CaptionTemplate>
                <Icon Name="IconName.City" /> @context.Caption
            </CaptionTemplate>
        </DataGridColumn>
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.Zip )" Caption="Zip">
        </DataGridColumn>
        <DataGridDateColumn TItem="Employee" Field="@nameof( Employee.DateOfBirth )" DisplayFormat="{0:dd.MM.yyyy}" Caption="Date Of Birth" Editable />
        <DataGridNumericColumn TItem="Employee" Field="@nameof( Employee.Childrens )" Caption="Childrens" ReverseSorting="true" Editable Filterable="false" />
        <DataGridSelectColumn TItem="Employee" Field="@nameof( Employee.Gender )" Caption="Gender" Editable Data="EmployeeData.Genders" ValueField="(x) => ((Gender)x).Code" TextField="(x) => ((Gender)x).Description" />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.Salary )" Caption="Salary" Editable Width="140px" DisplayFormat="{0:C}" DisplayFormatProvider="@System.Globalization.CultureInfo.GetCultureInfo("fr-FR")" TextAlignment="TextAlignment.End">
        </DataGridColumn>
        <DataGridCheckColumn TItem="Employee" Field="@nameof(Employee.IsActive)" Caption="Active" Editable Filterable="false">
            <DisplayTemplate>
                <Check TValue="bool" Checked="context.IsActive" Disabled ReadOnly />
            </DisplayTemplate>
        </DataGridCheckColumn>
    </DataGridColumns>
</DataGrid>
```

```
@code {
    [Inject] Blazored.LocalStorage.ILocalStorageService LocalStorage { get; set; }
    [Inject] EmployeeData EmployeeData { get; set; }

    private const string STORAGE_KEY = "__DATAGRID_STATE__";
    private DataGrid<Employee> dataGridRef;
    private IEnumerable<Employee> inMemoryData;

    protected override async Task OnInitializedAsync()
    {
        inMemoryData = ( await EmployeeData.GetDataAsync().ConfigureAwait( false ) ).Take( 25 );
        await base.OnInitializedAsync();
    }

    protected async override Task OnAfterRenderAsync( bool firstRender )
    {
        if ( firstRender )
        {
            await LoadState();
        }

        await base.OnAfterRenderAsync( firstRender );
    }

    private async Task ResetState()
    {
        await LocalStorage.RemoveItemAsync( STORAGE_KEY );

        var state = new DataGridState<Employee>()
        {
            CurrentPage = 1,
            PageSize = 10,
        };

        await dataGridRef.LoadState( state );
    }

    private async Task LoadState()
    {
        var stateFromLocalStorage = await LocalStorage.GetItemAsync<DataGridState<Employee>>( STORAGE_KEY );

        if ( stateFromLocalStorage is not null )
        {
            //It is of note that we must make sure the reference is contained in the DataGrid Data collection.
            if ( stateFromLocalStorage.SelectedRow is not null )
            {
                stateFromLocalStorage.SelectedRow = inMemoryData.FirstOrDefault( x => x.Id == stateFromLocalStorage.SelectedRow.Id );
            }
            if ( stateFromLocalStorage.EditItem is not null )
            {
                stateFromLocalStorage.EditItem = inMemoryData.FirstOrDefault( x => x.Id == stateFromLocalStorage.EditItem.Id );
            }
            await dataGridRef.LoadState( stateFromLocalStorage );
            return;
        }
    }

    private async Task SaveState()
    {
        var state = await dataGridRef.GetState();
        await LocalStorage.SetItemAsync( STORAGE_KEY, state );
    }
}
```

## API

See the documentation below for a complete reference to all of the props and classes available to the components mentioned here.

&lt;DataGrid /&gt;

###### On this page

#### 

## 