# Blazorise DataGrid: Editing

The DataGrid component allows you to dynamically insert, delete, and update records.

## Overview

The grid can perform some basic CRUD operations on the supplied Data collection. To enable editing on data-grid, set the Editable attribute to true on the DataGrid, and then set Editable to true on each column you wish to be editable.

By default every time the Item is saved it will be automatically handled by the data-grid itself. That means that all its fields will be populated after the user clicks on Save button. If you want to change that, you can just disable it by setting the UseInternalEditing to false.

### Edit Modes

The grid can work in several different editing modes that can provide different user experiences.

EditMode:

Form editing is done in the internal DataGrid form
Inline editing is done in the current row
Popup editing is done in the the modal dialog
Cell any cell value can be edited directly allowing for rapid editing of data.

|   # | First Name   | Last Name   | Email                       | Salary      |
|-----|--------------|-------------|-----------------------------|-------------|
|   1 | Samuel       | Collier     | Samuel.Collier62@gmail.com  | 86 030,41 € |
|   2 | Irvin        | Ziemann     | Irvin.Ziemann@gmail.com     | 61 781,31 € |
|   3 | Gerald       | Pollich     | Gerald82@yahoo.com          | 58 810,75 € |
|   4 | Cora         | Conn        | Cora27@yahoo.com            | 84 414,66 € |
|   5 | Alfonso      | D'Amore     | Alfonso.DAmore@hotmail.com  | 69 318,29 € |
|   6 | Jessie       | Wilkinson   | Jessie_Wilkinson@gmail.com  | 78 566,12 € |
|   7 | Gregory      | Renner      | Gregory63@hotmail.com       | 57 456,82 € |
|   8 | Maryann      | Hilpert     | Maryann.Hilpert12@gmail.com | 89 153,38 € |
|   9 | Merle        | Pacocha     | Merle3@gmail.com            | 55 349,94 € |
|  10 | Angelina     | Ward        | Angelina42@gmail.com        | 73 625,86 € |

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

1 - 10 of 499 items

499 items

```
<Field>
    <FieldLabel>
        Edit Mode
    </FieldLabel>
    <FieldBody>
        <Select @bind-SelectedValue="@editMode">
            <SelectItem Value="DataGridEditMode.Form">Form</SelectItem>
            <SelectItem Value="DataGridEditMode.Inline">Inline</SelectItem>
            <SelectItem Value="DataGridEditMode.Popup">Popup</SelectItem>
            <SelectItem Value="DataGridEditMode.Cell">Cell ("Rapid Editing")</SelectItem>
        </Select>
    </FieldBody>
</Field>

<DataGrid TItem="Employee"
          Data="@employeeList"
          @bind-SelectedRow="@selectedEmployee"
          Editable
          Responsive
          ShowPager
          CommandMode="DataGridCommandMode.ButtonRow"
          EditMode="editMode">
    <DataGridColumns>
        <DataGridCommandColumn  NewCommandAllowed="false" EditCommandAllowed="false" DeleteCommandAllowed="false"  CancelCommandAllowed >
            <SaveCommandTemplate>
                <Button ElementId="btnSave" Type="ButtonType.Submit" PreventDefaultOnSubmit Color="Color.Primary" Clicked="@context.Clicked">@context.LocalizationString</Button>
            </SaveCommandTemplate>
            <CancelCommandTemplate>
                <Button ElementId="btnCancel" Color="Color.Secondary" Clicked="@context.Clicked">@context.LocalizationString</Button>
            </CancelCommandTemplate>
        </DataGridCommandColumn>
        <DataGridColumn Field="@nameof(Employee.Id)" Caption="#" Sortable="false" />
        <DataGridColumn Field="@nameof(Employee.FirstName)" Caption="First Name" Editable />
        <DataGridColumn Field="@nameof(Employee.LastName)" Caption="Last Name" Editable />
        <DataGridColumn Field="@nameof(Employee.Email)" Caption="Email" Editable />
        <DataGridNumericColumn Field="@nameof(Employee.Salary)" Caption="Salary" DisplayFormat="{0:C}" DisplayFormatProvider="@System.Globalization.CultureInfo.GetCultureInfo("fr-FR")" Editable />
    </DataGridColumns>
    <ButtonRowTemplate>
        <Button Color="Color.Success" Clicked="context.NewCommand.Clicked">New</Button>
        <Button Color="Color.Primary" Disabled="(selectedEmployee is null)" Clicked="context.EditCommand.Clicked">Edit</Button>
        <Button Color="Color.Danger" Disabled="(selectedEmployee is null)" Clicked="context.DeleteCommand.Clicked">Delete</Button>
        <Button Color="Color.Link" Clicked="context.ClearFilterCommand.Clicked">Clear Filter</Button>
    </ButtonRowTemplate>
</DataGrid>
```

```
@code{
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;
    private Employee selectedEmployee;
    private DataGridEditMode editMode = DataGridEditMode.Form;

    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
        await base.OnInitializedAsync();
    }
}
```

### Rapid Editing

For a rapid editing experience, similar to how an excel document works, we recommend enabling the following options:

- CellNavigable - This allows to use the arrow keys to navigate between cells
- DataGridEditMode.Cell - This allows to edit the cells directly by pressing the Enter key or any text key.
- DataGridEditModeOptions.CellEditSelectTextOnEdit - When a cell enters edit mode the text will be selected allowing the user to quickly copy or replace it.

It is also of note that you can use the DataGridEditModeOptions to further configure how the feature will work.
            For instance, in the following example we're using the recommended options to enable rapid editing, and we’re using the CellEditOnSingleClick and CellEditOnDoubleClick edit options to disable the cell editing on single click and double click.

|   # | First Name   | Last Name   | Email                       | Salary      |
|-----|--------------|-------------|-----------------------------|-------------|
|   1 | Samuel       | Collier     | Samuel.Collier62@gmail.com  | 86 030,41 € |
|   2 | Irvin        | Ziemann     | Irvin.Ziemann@gmail.com     | 61 781,31 € |
|   3 | Gerald       | Pollich     | Gerald82@yahoo.com          | 58 810,75 € |
|   4 | Cora         | Conn        | Cora27@yahoo.com            | 84 414,66 € |
|   5 | Alfonso      | D'Amore     | Alfonso.DAmore@hotmail.com  | 69 318,29 € |
|   6 | Jessie       | Wilkinson   | Jessie_Wilkinson@gmail.com  | 78 566,12 € |
|   7 | Gregory      | Renner      | Gregory63@hotmail.com       | 57 456,82 € |
|   8 | Maryann      | Hilpert     | Maryann.Hilpert12@gmail.com | 89 153,38 € |
|   9 | Merle        | Pacocha     | Merle3@gmail.com            | 55 349,94 € |
|  10 | Angelina     | Ward        | Angelina42@gmail.com        | 73 625,86 € |

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

1 - 10 of 499 items

499 items

```
<Field>
    <FieldBody>
        <Switch @bind-Checked="@showCommandColumn" Size="Size.Medium">Show Command Column</Switch>
    </FieldBody>
</Field>

<DataGrid TItem="Employee"
          Data="@employeeList"
          @bind-SelectedRow="@selectedEmployee"
          Editable
          Responsive
          ShowPager
          CommandMode="DataGridCommandMode.ButtonRow"
          EditMode="DataGridEditMode.Cell"
          NavigationMode="DataGridNavigationMode.Cell"
          EditModeOptions="new() { CellEditOnSingleClick = false, CellEditOnDoubleClick = false, CellEditSelectTextOnEdit = true }">
    <DataGridColumns>
        @if ( showCommandColumn )
        {
            <DataGridCommandColumn NewCommandAllowed="false" EditCommandAllowed="false" DeleteCommandAllowed="false" CancelCommandAllowed>
                <SaveCommandTemplate>
                    <Button ElementId="btnSave" Type="ButtonType.Submit" PreventDefaultOnSubmit Color="Color.Primary" Clicked="@context.Clicked">@context.LocalizationString</Button>
                </SaveCommandTemplate>
                <CancelCommandTemplate>
                    <Button ElementId="btnCancel" Color="Color.Secondary" Clicked="@context.Clicked">@context.LocalizationString</Button>
                </CancelCommandTemplate>
            </DataGridCommandColumn>
        }
        <DataGridColumn Field="@nameof(Employee.Id)" Caption="#" Sortable="false" />
        <DataGridColumn Field="@nameof(Employee.FirstName)" Caption="First Name" Editable />
        <DataGridColumn Field="@nameof(Employee.LastName)" Caption="Last Name" Editable />
        <DataGridColumn Field="@nameof(Employee.Email)" Caption="Email" Editable />
        <DataGridNumericColumn Field="@nameof(Employee.Salary)" Caption="Salary" DisplayFormat="{0:C}" DisplayFormatProvider="@System.Globalization.CultureInfo.GetCultureInfo("fr-FR")" Editable />
    </DataGridColumns>
</DataGrid>
```

```
@code {
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;
    private Employee selectedEmployee;
    private bool showCommandColumn;

    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
        await base.OnInitializedAsync();
    }
}
```

### Batch Edit

The grid can be set to batch edit mode by setting BatchEdit to true. This allows the user to edit multiple rows and then save all the changes at once.

|   # | First Name   | Last Name   | Email                       | Salary      |
|-----|--------------|-------------|-----------------------------|-------------|
|   1 | Samuel       | Collier     | Samuel.Collier62@gmail.com  | 86 030,41 € |
|   2 | Irvin        | Ziemann     | Irvin.Ziemann@gmail.com     | 61 781,31 € |
|   3 | Gerald       | Pollich     | Gerald82@yahoo.com          | 58 810,75 € |
|   4 | Cora         | Conn        | Cora27@yahoo.com            | 84 414,66 € |
|   5 | Alfonso      | D'Amore     | Alfonso.DAmore@hotmail.com  | 69 318,29 € |
|   6 | Jessie       | Wilkinson   | Jessie_Wilkinson@gmail.com  | 78 566,12 € |
|   7 | Gregory      | Renner      | Gregory63@hotmail.com       | 57 456,82 € |
|   8 | Maryann      | Hilpert     | Maryann.Hilpert12@gmail.com | 89 153,38 € |
|   9 | Merle        | Pacocha     | Merle3@gmail.com            | 55 349,94 € |
|  10 | Angelina     | Ward        | Angelina42@gmail.com        | 73 625,86 € |

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
<Field>
    <FieldLabel>
        Edit Mode
    </FieldLabel>
    <FieldBody>
        <Select @bind-SelectedValue="@editMode">
            <SelectItem Value="DataGridEditMode.Form">Form</SelectItem>
            <SelectItem Value="DataGridEditMode.Inline">Inline</SelectItem>
            <SelectItem Value="DataGridEditMode.Popup">Popup</SelectItem>
            <SelectItem Value="DataGridEditMode.Cell">Cell ("Rapid Editing")</SelectItem>
        </Select>
    </FieldBody>
</Field>

<DataGrid @ref=dataGridRef
            TItem="Employee"
            Data="inMemoryData"
            Responsive
            ShowPager
            ShowPageSizes
            @bind-SelectedRow="@selectedEmployee"
            Editable
            EditMode="@editMode"
            BatchEdit
            BatchChange="OnBatchChange"
            BatchSaving="OnBatchSaving"
            BatchSaved="OnBatchSaved"
            UseValidation
            ValidationsSummaryLabel="The following validation errors have occurred..."
            CommandMode="DataGridCommandMode.ButtonRow"
            ShowValidationsSummary>
    <DataGridColumns>
        <DataGridCommandColumn SaveBatchCommandAllowed=false CancelBatchCommandAllowed=false />
        <DataGridColumn TextAlignment="TextAlignment.Center" TItem="Employee" Field="@nameof( Employee.Id )" Caption="#" Width="60px" />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.FirstName )" Caption="First Name" Editable />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.LastName )" Caption="Last Name" Editable />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.Email )" Caption="Email" Editable />
        <DataGridColumn TItem="Employee" Field="@nameof( Employee.Salary )" Caption="Salary" Editable Width="140px" DisplayFormat="{0:C}" DisplayFormatProvider="@System.Globalization.CultureInfo.GetCultureInfo("fr-FR")" TextAlignment="TextAlignment.End" />
     </DataGridColumns>
     <ButtonRowTemplate>
         <Button Color="Color.Success" Clicked="context.NewCommand.Clicked">New</Button>
         <Button Color="Color.Primary" Disabled="(selectedEmployee is null)" Clicked="context.EditCommand.Clicked">Edit</Button>
         <Button Color="Color.Danger" Disabled="(selectedEmployee is null)" Clicked="context.DeleteCommand.Clicked">Delete</Button>
         <Button Color="Color.Link" Clicked="context.ClearFilterCommand.Clicked">Clear Filter</Button>

         <Button Color="Color.Success" Disabled="(batchQuantity == 0)" Clicked="@(context.SaveBatchCommand.Clicked)">@context.SaveBatchCommand.LocalizationString</Button>
         <Button Color="Color.Default" Clicked="@(context.CancelBatchCommand.Clicked)">@context.CancelBatchCommand.LocalizationString</Button>
    </ButtonRowTemplate>
</DataGrid>
```

```
@code {
    [Inject] EmployeeData EmployeeData { get; set; }

    private int batchQuantity = 0;
    private DataGrid<Employee> dataGridRef;
    private List<Employee> inMemoryData;
    private Employee selectedEmployee;
    private DataGridEditMode editMode = DataGridEditMode.Form;

    protected override async Task OnInitializedAsync()
    {
        inMemoryData = ( await EmployeeData.GetDataAsync().ConfigureAwait( false ) ).Take( 25 ).ToList();
        await base.OnInitializedAsync();
    }

    private Task OnBatchChange( DataGridBatchChangeEventArgs<Employee> args )
    {
        Console.WriteLine( "Batch Change" );
        batchQuantity = dataGridRef.BatchChanges.Count;
        return Task.CompletedTask;
    }

    private Task OnBatchSaving( DataGridBatchSavingEventArgs<Employee> args )
    {
        Console.WriteLine( "Batch Saving" );
        return Task.CompletedTask;
    }

    private Task OnBatchSaved( DataGridBatchSavedEventArgs<Employee> args )
    {
        Console.WriteLine( "Batch Saved" );
        batchQuantity = 0;
        return Task.CompletedTask;
    }
}
```

### NewItemDefaultSetter

function is used to set default values when new item is created and before the edit form is shown. It will only be evaluate, if  is editable.

| New        |   # | First Name   | Last Name   | Email                       | Salary      |
|------------|-----|--------------|-------------|-----------------------------|-------------|
| EditDelete |   1 | Samuel       | Collier     | Samuel.Collier62@gmail.com  | 86 030,41 € |
| EditDelete |   2 | Irvin        | Ziemann     | Irvin.Ziemann@gmail.com     | 61 781,31 € |
| EditDelete |   3 | Gerald       | Pollich     | Gerald82@yahoo.com          | 58 810,75 € |
| EditDelete |   4 | Cora         | Conn        | Cora27@yahoo.com            | 84 414,66 € |
| EditDelete |   5 | Alfonso      | D'Amore     | Alfonso.DAmore@hotmail.com  | 69 318,29 € |
| EditDelete |   6 | Jessie       | Wilkinson   | Jessie_Wilkinson@gmail.com  | 78 566,12 € |
| EditDelete |   7 | Gregory      | Renner      | Gregory63@hotmail.com       | 57 456,82 € |
| EditDelete |   8 | Maryann      | Hilpert     | Maryann.Hilpert12@gmail.com | 89 153,38 € |
| EditDelete |   9 | Merle        | Pacocha     | Merle3@gmail.com            | 55 349,94 € |
| EditDelete |  10 | Angelina     | Ward        | Angelina42@gmail.com        | 73 625,86 € |

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

1 - 10 of 499 items

499 items

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          @bind-SelectedRow="@selectedEmployee"
          NewItemDefaultSetter="@OnEmployeeNewItemDefaultSetter"
          Editable
          Responsive
          ShowPager>
    <DataGridCommandColumn />
    <DataGridColumn Field="@nameof(Employee.Id)" Caption="#" Sortable="false" />
    <DataGridColumn Field="@nameof(Employee.FirstName)" Caption="First Name" Editable />
    <DataGridColumn Field="@nameof(Employee.LastName)" Caption="Last Name" Editable />
    <DataGridColumn Field="@nameof(Employee.Email)" Caption="Email" Editable />
    <DataGridColumn Field="@nameof(Employee.Salary)" Caption="Salary" DisplayFormat="{0:C}" DisplayFormatProvider="@System.Globalization.CultureInfo.GetCultureInfo("fr-FR")" Editable>
        <EditTemplate>
            <NumericEdit TValue="decimal" Value="@((decimal)context.CellValue)" ValueChanged="@( v => context.CellValue = v)" />
        </EditTemplate>
    </DataGridColumn>
</DataGrid>
```

```
@code{
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;
    private Employee selectedEmployee;

    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
        await base.OnInitializedAsync();
    }

    void OnEmployeeNewItemDefaultSetter( Employee employee )
    {
        employee.Salary = 100.0M;
        employee.IsActive = true;
    }
}
```

### Cascading values

In some case you want to update a different cell in a DataGrid when you update a value. This can be achieved with an UpdateCell method. You have two ways of updating a cell:

- by calling UpdateCell on the context inside of EditTemplate, or
- by calling UpdateCellEditValue on the DataGrid instance

In the following example we’re simply calling context.UpdateCell with a field-name to change and a new value that we want it to assign:

| New        | Salary      | Tax         |
|------------|-------------|-------------|
| EditDelete | 86 030,41 € | 21 507,60 € |
| EditDelete | 61 781,31 € | 15 445,33 € |
| EditDelete | 58 810,75 € | 14 702,69 € |
| EditDelete | 84 414,66 € | 21 103,67 € |
| EditDelete | 69 318,29 € | 17 329,57 € |
| EditDelete | 78 566,12 € | 19 641,53 € |
| EditDelete | 57 456,82 € | 14 364,21 € |
| EditDelete | 89 153,38 € | 22 288,35 € |
| EditDelete | 55 349,94 € | 13 837,49 € |
| EditDelete | 73 625,86 € | 18 406,47 € |

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

1 - 10 of 499 items

499 items

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          Editable
          EditMode="DataGridEditMode.Inline"
          Responsive
          ShowPager>
    <DataGridCommandColumn />
    <DataGridColumn Field="@nameof( Employee.Salary )" Caption="Salary" Editable DisplayFormat="{0:C}" DisplayFormatProvider="@System.Globalization.CultureInfo.GetCultureInfo("fr-FR")">
        <EditTemplate>
            <NumericEdit TValue="decimal"
                         Value="@((decimal)context.CellValue)"
                         ValueChanged="@( v => {
                            context.CellValue = v;
                            context.UpdateCell( nameof( Employee.Tax ), v * context.Item.TaxPercentage );
                         })" />
        </EditTemplate>
    </DataGridColumn>
    <DataGridColumn Field="@nameof( Employee.Tax )" Caption="Tax" Editable DisplayFormat="{0:C}" DisplayFormatProvider="@System.Globalization.CultureInfo.GetCultureInfo("fr-FR")">
        <EditTemplate>
            <NumericEdit TValue="decimal"
                         Value="@((decimal)context.CellValue)"
                         Disabled />
        </EditTemplate>
    </DataGridColumn>
</DataGrid>
```

```
@code {
    [Inject]
    public EmployeeData EmployeeData { get; set; }
    private List<Employee> employeeList;

    protected override async Task OnInitializedAsync()
    {
        employeeList = await EmployeeData.GetDataAsync();
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