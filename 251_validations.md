# Blazorise DataGrid: Validations

Easily validate the edited or added row data.

## Overview

The DataGrid provides validations of column values at editing or creating items. For using validation of DataGrid you have to use these properties:

UseValidation must be set to true to enable validation.
ShowValidationFeedback of DataGrid to hide or show feedback for validation.
ShowValidationsSummary of DataGrid to hide or show validations summary.
ValidationsSummaryLabel of DataGrid to set label of validations summary.
Validator of DataGridColumn validates the input value after trying to save.
ValidationPattern of DataGridColumn forces validation to use regex pattern matching instead of default validator handler.

## Examples

### Validations

By default,  will use data-annotation to validate editing fields. You only need to define them on your model and they will automatically be picked up by the grid.

```
public class Employee
{
	[Required]
	public string FirstName { get; set; }

	[Required]
	public string LastName { get; set; }
}
```

Don’t forget to enable validation by setting .

| Name    | New        |
|---------|------------|
| David   | EditDelete |
| Mladen  | EditDelete |
| John    | EditDelete |
| Ana     | EditDelete |
| Jessica | EditDelete |

To override data-annotation you only need to define a  attribute and assign it to your validation method.

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          Responsive
          Editable
          UseValidation>
    <DataGridColumn Field="@nameof( Employee.FirstName )" Caption="Name" Validator="@CheckName" Editable />
    <DataGridCommandColumn />
</DataGrid>
```

```
@code{
    private List<Employee> employeeList = new() { new() { FirstName = "David" }, new() { FirstName = "Mladen" }, new() { FirstName = "John" }, new() { FirstName = "Ana" }, new() { FirstName = "Jessica" } };

    public void CheckName( ValidatorEventArgs validationArgs )
    {
        ValidationRule.IsNotEmpty( validationArgs );

        if ( validationArgs.Status == ValidationStatus.Error )
        {
            validationArgs.ErrorText = "Name can't be empty.";
        }
    }
}
```

| Name    | New        |
|---------|------------|
| David   | EditDelete |
| Mladen  | EditDelete |
| John    | EditDelete |
| Ana     | EditDelete |
| Jessica | EditDelete |

If you use  to customize editing of columns, then using  or  will not work and you have to use  like in the following example:

```
<DataGrid TItem="Employee"
          Data="@employeeList"
          Responsive
          Editable
          UseValidation
          ShowValidationsSummary="false">
    <DataGridColumn Field="@nameof( Employee.FirstName )" Caption="Name" Editable>
        <EditTemplate>
            <Validation Validator="@CheckName">
                <TextEdit Text="@((string)context.CellValue)" TextChanged="(value => context.CellValue = value)">
                    <Feedback>
                        <ValidationError />
                    </Feedback>
                </TextEdit>
            </Validation>
        </EditTemplate>
    </DataGridColumn>
    <DataGridCommandColumn />
</DataGrid>
```

```
@code{
    private List<Employee> employeeList = new() { new() { FirstName = "David" }, new() { FirstName = "Mladen" }, new() { FirstName = "John" }, new() { FirstName = "Ana" }, new() { FirstName = "Jessica" } };

    public void CheckName( ValidatorEventArgs validationArgs )
    {
        ValidationRule.IsNotEmpty( validationArgs );

        if ( validationArgs.Status == ValidationStatus.Error )
        {
            validationArgs.ErrorText = "Name can't be empty.";
        }
    }
}
```

## API

See the documentation below for a complete reference to all of the props and classes available to the components mentioned here.

&lt;DataGrid /&gt;

###### On this page

#### 

## 