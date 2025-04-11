# Blazorise DataGrid: Paging

Paging provides an option to display DataGrid data in pages.

## Overview

With the paging enabled, users can easily navigate the DataGrid by clicking on a page button. This can be particularly useful when working with large sets of data.

## Examples

### Paging

Paging is handled automatically by the DataGrid. To show the pager you need to enable the ShowPager parameter.

To show the pager you need to enable the ShowPager parameter.

PageSize the maximum number of items for each page.
CurrentPage current page number.
PreviousPageButtonTemplate template for previous page button
NextPageButtonTemplate template for next page button
FirstPageButtonTemplate template for first page button
LastPageButtonTemplate template for last page button
PageButtonTemplate template for explicated page button with PageButtonContext as parameter
PagerOptions will provide you with additional settings to customize your pager.

### Pager Customization Example

Below you will find a fully customized pager.

- 1
- 2
- 3
- 4
- 5
- 12345
- 5102550100250

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

- 1
- 2
- 3
- 4
- 5
- 12345
- 5102550100250

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          @bind-SelectedRow="@selectedEmployee"
          Responsive
          ShowPager
          ShowPageSizes
          PagerPosition="DataGridPagerPosition.TopAndBottom"
          PagerOptions="new(){ ButtonSize=Size.Small }">
    <DataGridColumns>
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
    </DataGridColumns>
    <PageButtonTemplate>
        <Span TextColor="TextColor.Success">
            @context.PageNumber
        </Span>
    </PageButtonTemplate>
    <NextPageButtonTemplate><Icon Name="IconName.StepForward" TextColor="TextColor.Success" /></NextPageButtonTemplate>
    <PreviousPageButtonTemplate><Icon Name="IconName.StepBackward" TextColor="TextColor.Success" /></PreviousPageButtonTemplate>
    <LastPageButtonTemplate><Icon Name="IconName.Forward" TextColor="TextColor.Success" /></LastPageButtonTemplate>
    <FirstPageButtonTemplate><Icon Name="IconName.Backward" TextColor="TextColor.Success" /></FirstPageButtonTemplate>
    <TotalItemsTemplate><Badge Color="Color.Success">@context.TotalItems total items</Badge></TotalItemsTemplate>
    <TotalItemsShortTemplate><Badge Color="Color.Success">@context.TotalItems</Badge></TotalItemsShortTemplate>
    <ItemsPerPageTemplate></ItemsPerPageTemplate>
    <PageSelectorTemplate>
        <Select TextColor="TextColor.Success" @bind-SelectedValue="@context.CurrentPage" Size="Size.Small">
            @for ( int i = context.FirstVisiblePage; i <= context.LastVisiblePage; ++i )
            {
                var pageNumber = i;
                <SelectItem Value="@pageNumber">@pageNumber</SelectItem>
            }
        </Select>
    </PageSelectorTemplate>
    <PageSizesTemplate>
        <Select TextColor="TextColor.Success" @bind-SelectedValue="@context.CurrentPageSize" Size="Size.Small">
            @foreach ( var curPageSize in context.PageSizes )
            {
                <SelectItem Value="@curPageSize">@curPageSize</SelectItem>
            }
        </Select>
    </PageSizesTemplate>
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
}
```

## API

See the documentation below for a complete reference to all of the props and classes available to the components mentioned here.

&lt;DataGrid /&gt;

###### On this page

#### 

## 