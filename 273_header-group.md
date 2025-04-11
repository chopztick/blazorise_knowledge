# Blazorise DataGrid: Header Group

Header Group feature for Blazorise DataGrid allows you to easily group a set of defined columns by rendering a top row header which groups the columns by the defined Caption.

### Header Group

You can define columns that can be grouped by assigning the HeaderGroupCaption and enabling ShowHeaderGroupCaptions on the DataGrid.

|    | Personal Info   | Personal Info               | Personal Info   | Address    | Address           |
|----|-----------------|-----------------------------|-----------------|------------|-------------------|
| #  | First Name      | Email                       | Last Name       | Zip        | City              |
| 1  | Samuel          | Samuel.Collier62@gmail.com  | Collier         | 91848-4714 | New Lura          |
| 2  | Irvin           | Irvin.Ziemann@gmail.com     | Ziemann         | 16505-8405 | Modestomouth      |
| 3  | Gerald          | Gerald82@yahoo.com          | Pollich         | 28612      | Theresashire      |
| 4  | Cora            | Cora27@yahoo.com            | Conn            | 10437-2253 | North Art         |
| 5  | Alfonso         | Alfonso.DAmore@hotmail.com  | D'Amore         | 87912-3933 | East Carolefort   |
| 6  | Jessie          | Jessie_Wilkinson@gmail.com  | Wilkinson       | 34306      | Mayrafurt         |
| 7  | Gregory         | Gregory63@hotmail.com       | Renner          | 57895      | West Marcelleside |
| 8  | Maryann         | Maryann.Hilpert12@gmail.com | Hilpert         | 38859-0368 | Boehmview         |
| 9  | Merle           | Merle3@gmail.com            | Pacocha         | 48154-3034 | North Erlingport  |
| 10 | Angelina        | Angelina42@gmail.com        | Ward            | 72291-1146 | Melyssaview       |

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

```
<DataGrid TItem="Employee"
          Data="inMemoryData"
          ShowPager
          ShowPageSizes
          ShowHeaderGroupCaptions>
    <DataGridColumns>
        <DataGridColumn DisplayOrder=2 TItem="Employee" Field="@nameof( Employee.LastName )" HeaderGroupCaption="Personal Info" Caption="Last Name" />
        <DataGridColumn TextAlignment="TextAlignment.Center" TItem="Employee" Field="@nameof( Employee.Id )" Caption="#" Width="60px" />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.FirstName )" HeaderGroupCaption="Personal Info" Caption="First Name" />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.Zip )" HeaderGroupCaption="Address" Caption="Zip" />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.City )" HeaderGroupCaption="Address" Caption="City">
            <CaptionTemplate>
                <Icon Name="IconName.City" /> @context.Caption
            </CaptionTemplate>
        </DataGridColumn>
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.Email )" HeaderGroupCaption="Personal Info" Caption="Email" />
    </DataGridColumns>
</DataGrid>
```

```
@code {
    [Inject] EmployeeData EmployeeData { get; set; }

    private List<Employee> inMemoryData;

    protected override async Task OnInitializedAsync()
    {
        inMemoryData = ( await EmployeeData.GetDataAsync().ConfigureAwait( false ) ).Take( 25 ).ToList();
        await base.OnInitializedAsync();
    }
}
```

### Header Group Template

You can define also further customize the look of each header group by defining HeaderGroupCaptionTemplate.

|    | Personal Information   | Personal Information        | Personal Information   | Address    | Address           |
|----|------------------------|-----------------------------|------------------------|------------|-------------------|
| #  | First Name             | Email                       | Last Name              | Zip        | City              |
| 1  | Samuel                 | Samuel.Collier62@gmail.com  | Collier                | 91848-4714 | New Lura          |
| 2  | Irvin                  | Irvin.Ziemann@gmail.com     | Ziemann                | 16505-8405 | Modestomouth      |
| 3  | Gerald                 | Gerald82@yahoo.com          | Pollich                | 28612      | Theresashire      |
| 4  | Cora                   | Cora27@yahoo.com            | Conn                   | 10437-2253 | North Art         |
| 5  | Alfonso                | Alfonso.DAmore@hotmail.com  | D'Amore                | 87912-3933 | East Carolefort   |
| 6  | Jessie                 | Jessie_Wilkinson@gmail.com  | Wilkinson              | 34306      | Mayrafurt         |
| 7  | Gregory                | Gregory63@hotmail.com       | Renner                 | 57895      | West Marcelleside |
| 8  | Maryann                | Maryann.Hilpert12@gmail.com | Hilpert                | 38859-0368 | Boehmview         |
| 9  | Merle                  | Merle3@gmail.com            | Pacocha                | 48154-3034 | North Erlingport  |
| 10 | Angelina               | Angelina42@gmail.com        | Ward                   | 72291-1146 | Melyssaview       |

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

```
<DataGrid TItem="Employee"
          Data="inMemoryData"
          ShowPager
          ShowPageSizes
          ShowHeaderGroupCaptions>
    <DataGridColumns>
        <DataGridColumn DisplayOrder=2 TItem="Employee" Field="@nameof( Employee.LastName )" HeaderGroupCaption="PersonalInfo" Caption="Last Name" />
        <DataGridColumn TextAlignment="TextAlignment.Center" TItem="Employee" Field="@nameof( Employee.Id )" Caption="#" Width="60px" />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.FirstName )" HeaderGroupCaption="PersonalInfo" Caption="First Name" />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.Zip )" HeaderGroupCaption="Address" Caption="Zip" />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.City )" HeaderGroupCaption="Address" Caption="City">
            <CaptionTemplate>
                <Icon Name="IconName.City" /> @context.Caption
            </CaptionTemplate>
        </DataGridColumn>
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.Email )" HeaderGroupCaption="PersonalInfo" Caption="Email" />
    </DataGridColumns>
    <HeaderGroupCaptionTemplate>
        @if ( context.HeaderGroupCaption == "PersonalInfo" )
        {
            <Strong TextColor="TextColor.Primary">Personal Information</Strong>
        }
        else if ( context.HeaderGroupCaption == "Address" )
        {
            <Strong TextColor="TextColor.Success">Address</Strong>
        }
    </HeaderGroupCaptionTemplate>
</DataGrid>
```

```
@code {
    [Inject] EmployeeData EmployeeData { get; set; }

    private List<Employee> inMemoryData;

    protected override async Task OnInitializedAsync()
    {
        inMemoryData = ( await EmployeeData.GetDataAsync().ConfigureAwait( false ) ).Take( 25 ).ToList();
        await base.OnInitializedAsync();
    }
}
```

## API

See the documentation below for a complete reference to all of the props and classes available to the components mentioned here.

&lt;DataGrid /&gt;

###### On this page

#### 

## 