# Blazorise Validation component

The Validation component allows you to verify your data, helping you find and correct errors.

Validation components are used to provide simple form validation for Blazorise input components.

The basic structure for validation component is:

- &lt; Validations&gt; container for all validations, it can contain multiple Validation components.
- &lt;Validations&gt; container for all validations, it can contain multiple Validation components.
    - &lt; Validation&gt; component that contains the validation logic.
    - &lt;Validation&gt; component that contains the validation logic.
        - &lt; Feedback&gt; component that displays the validation message.
        - &lt;Feedback&gt; component that displays the validation message.
            - &lt;ValidationSuccess&gt; success message.
            - &lt;ValidationError&gt; error message.
            - &lt;ValidationNone&gt; message when nothing has happened.
    - &lt;ValidationSummary&gt; lists all error messages

For the most part you will need to use just the &lt;Validation&gt; component along
    with &lt;ValidationSuccess&gt; and &lt;ValidationError&gt;. By default every validation
    will run automatically when input value changes. You must set the Validator event handler where you can
    define the validation rules and return the validation result.

## Examples

### Validating using Methods handlers

Method handlers are the easiest and quickest way to validate fields. Therefore, we give you a set of predefined validation handlers that can be accessed through the  ValidationRule helpers class and assigned to the Validator parameter.

Apart from using the pre-built handler methods, you can also create your own. For example, you can see the custom ValidateEmail handler in the following code-snippet.

Enter valid name!

```
<Validation Validator="ValidationRule.IsNotEmpty">
    <TextEdit Placeholder="Enter name">
        <Feedback>
            <ValidationNone>Please enter the name.</ValidationNone>
            <ValidationSuccess>Name is good.</ValidationSuccess>
            <ValidationError>Enter valid name!</ValidationError>
        </Feedback>
    </TextEdit>
</Validation>

<Validation Validator="ValidateEmail">
    <TextEdit Placeholder="Enter email">
        <Feedback>
            <ValidationNone>Please enter the email.</ValidationNone>
            <ValidationSuccess>Email is good.</ValidationSuccess>
            <ValidationError>Enter valid email!</ValidationError>
        </Feedback>
    </TextEdit>
</Validation>
```

```
@code{
    void ValidateEmail( ValidatorEventArgs e )
    {
        var email = Convert.ToString( e.Value );

        e.Status = string.IsNullOrEmpty( email ) ? ValidationStatus.None :
            email.Contains( "@" ) ? ValidationStatus.Success : ValidationStatus.Error;
    }
}
```

The same structure is for all  components(check, radio, select, etc). Note that for some components
        there are some special rules when defining the validation structure. For example for  you must use
         tag along with the  tag. This is a limitation in Blazor, hopefully it
        will be fixed in the future.

```
<Validation Validator="@ValidateCheck">
    <Check TValue="bool">
        <ChildContent>
            Check me out
        </ChildContent>
        <Feedback>
            <ValidationError>You must check me out!</ValidationError>
        </Feedback>
    </Check>
</Validation>
```

```
@code{
    void ValidateCheck( ValidatorEventArgs e )
    {
        // ...
    }
}
```

### Validating using Data Annotations

To use data annotations with Blazorise you must combine both

and the

components. The

component will act as a group for a fields used inside of

component. To make it all work you must meet two requirements:

1. Validations component must contain reference to the validated POCO through the Model parameter.
2. Input component must bind to the model field through the @bind-{Value}(i.e. @bind-Text)

After those two requirements are met the Blazorise will have enough information to know how to use data annotations.

The Name field is required.

The Email field is required.

Password is required

Confirm Password is required

```
@using System.ComponentModel.DataAnnotations

<Validations Mode="ValidationMode.Auto" Model="@user">
    <Validation>
        <Field Horizontal>
            <FieldLabel ColumnSize="ColumnSize.Is2">Full Name</FieldLabel>
            <FieldBody ColumnSize="ColumnSize.Is10">
                <TextEdit Placeholder="First and last name" @bind-Text="@user.Name">
                    <Feedback>
                        <ValidationError />
                    </Feedback>
                </TextEdit>
            </FieldBody>
        </Field>
    </Validation>
    <Validation>
        <Field Horizontal>
            <FieldLabel ColumnSize="ColumnSize.Is2">Email</FieldLabel>
            <FieldBody ColumnSize="ColumnSize.Is10">
                <TextEdit Placeholder="Enter email" @bind-Text="@user.Email">
                    <Feedback>
                        <ValidationError />
                    </Feedback>
                </TextEdit>
            </FieldBody>
        </Field>
    </Validation>
    <Validation>
        <Field Horizontal>
            <FieldLabel ColumnSize="ColumnSize.Is2">Password</FieldLabel>
            <FieldBody ColumnSize="ColumnSize.Is10">
                <TextEdit Role="TextRole.Password" Placeholder="Password" @bind-Text="@user.Password">
                    <Feedback>
                        <ValidationError />
                    </Feedback>
                </TextEdit>
            </FieldBody>
        </Field>
    </Validation>
    <Validation>
        <Field Horizontal>
            <FieldLabel ColumnSize="ColumnSize.Is2">Re Password</FieldLabel>
            <FieldBody ColumnSize="ColumnSize.Is10">
                <TextEdit Role="TextRole.Password" Placeholder="Retype password" @bind-Text="@user.ConfirmPassword">
                    <Feedback>
                        <ValidationError />
                    </Feedback>
                </TextEdit>
            </FieldBody>
        </Field>
    </Validation>
</Validations>
```

```
@code{
    User user = new User();

    public class User
    {
        [Required]
        [StringLength( 10, ErrorMessage = "Name is too long." )]
        public string Name { get; set; }

        [Required]
        [EmailAddress( ErrorMessage = "Invalid email." )]
        public string Email { get; set; }

        [Required( ErrorMessage = "Password is required" )]
        [StringLength( 8, ErrorMessage = "Must be between 5 and 8 characters", MinimumLength = 5 )]
        [DataType( DataType.Password )]
        public string Password { get; set; }

        [Required( ErrorMessage = "Confirm Password is required" )]
        [StringLength( 8, ErrorMessage = "Must be between 5 and 8 characters", MinimumLength = 5 )]
        [DataType( DataType.Password )]
        [Compare( "Password" )]
        public string ConfirmPassword { get; set; }

        [Required]
        public string Title { get; set; }

        [Range( typeof( bool ), "true", "true", ErrorMessage = "You gotta tick the box!" )]
        public bool TermsAndConditions { get; set; }
    }
}
```

### Validating using Pattern

If you want to validate input by using regular expression instead of  handlers you can
        use  patameter. Components that supports pattern attribute are
        ,  and .

Pattern does not match!

```
<Validation UsePattern>
    <TextEdit Pattern="[A-Za-z]{3}">
        <Feedback>
            <ValidationError>Pattern does not match!</ValidationError>
        </Feedback>
    </TextEdit>
</Validation>
```

### Async validation

In case you need to run validation using the external source or rest API, we also support async validation.
        The process is similar to regular validator. You just need to define awaitable handler using
        the  parameter.

Enter valid name!

```
@using System.Threading

<Validation AsyncValidator="@ValidateNameAsync">
    <TextEdit Placeholder="Enter name">
        <Feedback>
            <ValidationError>Enter valid name!</ValidationError>
        </Feedback>
    </TextEdit>
</Validation>
```

```
@code{
    Random random = new Random();

    async Task ValidateNameAsync( ValidatorEventArgs e, CancellationToken cancellationToken )
    {
        cancellationToken.ThrowIfCancellationRequested();

        // some long running task or call to the rest API
        await Task.Delay( random.Next( 1500 ) );

        e.Status = string.IsNullOrEmpty( Convert.ToString( e.Value ) )
            ? ValidationStatus.Error
            : ValidationStatus.Success;
    }
}
```

### Manual validation

Sometimes you don’t want to do validation on every input change. In that case you use  component
        to group multiple validations and then run the validation manually.
        



        In this example you can see how the component is used to enclose multiple validation
        components and the  attribute is set to . Validation is executed only when
        clicked on submit button.

```
<Validations @ref="validations" Mode="ValidationMode.Manual">
    <Validation Validator="@ValidationRule.IsNotEmpty">
        <Field>
            <TextEdit Placeholder="Enter first name" />
        </Field>
    </Validation>
    <Validation Validator="@ValidationRule.IsNotEmpty">
        <Field>
            <TextEdit Placeholder="Enter last name" />
        </Field>
    </Validation>
    <Button Color="Color.Primary" Clicked="@Submit">Submit</Button>
</Validations>
```

```
@code{
    Validations validations;

    async Task Submit()
    {
        if ( await validations.ValidateAll() )
        {
            // do something
        }
    }
}
```

## Localization

If you want to localize your validation messages, we got you covered. Blazorise will provide you with an API
    and all the required information needed for you to make localization. This is done through the MessageLocalizer API.
    But before you use it we need to break it down a little so you can understand it better how it works.

A MessageLocalizer is fairly straight forward. It accepts two parameters and returns a string. It’s
    signature is as following string Localize(string message, IEnumerable&lt;string&gt; arguments).

Where:

- format raw validation message
- arguments list of arguments or values for populating the message

So now that you know what the API consist of, we need to talk what is the content of the API. And the most important
    is the message parameter. Each message value will be represented as a raw message in the form before
    the actual message was formatted.

For example if you have a [Required] attribute set on your model field, this message will be
    "The {0} field is required.". And the arguments will contain all the
    values needed to populate the placeholders inside of the message.

### Example

For the basic example we’re going to use  directly on a  component.

```
@using Blazorise.Localization

<Validation MessageLocalizer="@Localize">
</Validation>
```

```
@code{
    [Inject] ITextLocalizer<LocalizationValidationExample> L { get; set; }

    string Localize( string message, IEnumerable<string> arguments )
    {
        // You should probably do null checks here!
        return string.Format( L[message], arguments.ToArray() );
    }
}
```

### Global Options

Setting the  on each  is a good for approach if you want
        to control every part of your application. But a more practical way is to define it globally. If you remember
        from the Start Guide, we already have  defined in our application startup so we just need
        to modify it a little.

### Validation summary

Sometimes you don’t want to show error messages under each field. In those situations you can
        use  component. Once placed inside of Validations it will show
        all error messages as a bullet list.

```
<Validations Mode="ValidationMode.Manual">
    <ValidationSummary Label="Following error occurs..." />

    @*other validation fields*@
</Validations>
```

### Auto Validation

By default form is auto-validated on page load. In case you want to disable it and validate
        only when user starts entering fields, now you can. Just set  to false.

...

```
<Validations Mode="ValidationMode.Auto" ValidateOnLoad>
    ...
</Validations>
```

### Validation rules

In Blazorise you can use some of the predefined validation rules. eg

...

```
<Validation Validator="@ValidationRule.IsNotEmpty">
    ...
</Validation>
```

### IValidatableObject

This example demonstrates how to implement validation in a Blazor component using the  interface for custom logic. The form contains several fields bound to a CompanyInfo model, which is validated automatically using data annotations and custom validation logic.

Name is required

Description is required

AlphaCode is required

```
@using System.ComponentModel.DataAnnotations

<Validations Model="@Company" Mode="ValidationMode.Auto">
    <Validation>
        <Field>
            <FieldLabel>Name</FieldLabel>
            <FieldBody>
                <TextEdit @bind-Text="@Company.Name">
                    <Feedback>
                        <ValidationError />
                    </Feedback>
                </TextEdit>
            </FieldBody>
        </Field>
    </Validation>
    <Validation>
        <Field>
            <FieldLabel>Description</FieldLabel>
            <FieldBody>
                <TextEdit @bind-Text="@Company.Description">
                    <Feedback>
                        <ValidationError />
                    </Feedback>
                </TextEdit>
            </FieldBody>
        </Field>
    </Validation>
    <Field>
        <Switch @bind-Checked="@Company.UseAlphaCode">Use AlphaCode</Switch>
    </Field>
    <Fields>
        <Validation>
            <Field>
                <FieldLabel>AlphaCode</FieldLabel>
                <FieldBody>
                    <TextEdit @bind-Text="@Company.AlphaCode">
                        <Feedback>
                            <ValidationError />
                        </Feedback>
                    </TextEdit>
                </FieldBody>
            </Field>
        </Validation>
        <Validation>
            <Field>
                <FieldLabel>BetaCode</FieldLabel>
                <FieldBody>
                    <TextEdit @bind-Text="@Company.BetaCode">
                        <Feedback>
                            <ValidationError />
                        </Feedback>
                    </TextEdit>
                </FieldBody>
            </Field>
        </Validation>
    </Fields>
</Validations>
```

```
@code {
    CompanyInfo Company = new CompanyInfo()
    {
        UseAlphaCode = true,
    };

    public class CompanyInfo : IValidatableObject
    {
        [Required( ErrorMessage = "Name is required" )]
        public string Name { get; set; }

        [Required( ErrorMessage = "Description is required" )]
        public string Description { get; set; }

        public bool UseAlphaCode { get; set; }

        public string AlphaCode { get; set; }

        public string BetaCode { get; set; }

        [Range( 0, 999.99 )]
        public decimal Price { get; set; }

        public IEnumerable<ValidationResult> Validate( ValidationContext validationContext )
        {
            if ( UseAlphaCode )
            {
                if ( String.IsNullOrWhiteSpace( AlphaCode ) )
                {
                    yield return new ValidationResult( "AlphaCode is required", new[] { "AlphaCode" } );
                }
            }
            else
            {
                if ( String.IsNullOrWhiteSpace( BetaCode ) )
                {
                    yield return new ValidationResult( "BetaCode is required", new[] { "BetaCode" } );
                }
            }
        }
    }
}
```

List of the currently available validators.

| Name                         | Description                                                                                                                    |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| IsEmpty                      | Check if the string is null or empty.                                                                                          |
| IsNotEmpty                   | Check if the string is not null or empty.                                                                                      |
| IsEmail                      | Check if the string is an email.                                                                                               |
| IsAlpha                      | Check if the string contains only letters (a-zA-Z).                                                                            |
| IsAlphanumeric               | Check if the string contains only letters and numbers.                                                                         |
| IsAlphanumericWithUnderscore | Check if the string contains only letters, numbers and underscore.                                                             |
| IsUppercase                  | Check if the string is uppercase.                                                                                              |
| IsLowercase                  | Check if the string is lowercase.                                                                                              |
| IsChecked                    | Checks if the boolean based input is checked.                                                                                  |
| IsSelected                   | Checks if the selection based input has a valid value selected. Valid values are anything except for null, string.Empty, or 0. |
| IsFileSelected               | Checks if the file is selected.                                                                                                |

## API

### Parameters

#### Validations

| Parameter                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Type           | Default             |
|---------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|---------------------|
| ChildContent              | Specifies the content to be rendered inside this Validations.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | RenderFragment | null                |
| EditContext               | Supplies the edit context explicitly. If using this parameter, do not     also supply Validations.Model, since the model value will be taken     from the EditContext.Model property.                                                                                                                                                                                                                                                                                                                                                                                          | EditContext    | null                |
| HandlerType               | Defines the default handler type that will be used by the validation, unless it is overriden by Validation.HandlerType property.                                                                                                                                                                                                                                                                                                                                                                                                                                               | Type           | null                |
| MissingFieldsErrorMessage | Message that will be displayed if any of the validations does not have defined error message.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | string         |                     |
| Mode                      | Defines the validation mode for validations inside of this container.Possible values:Auto, Manual                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | ValidationMode | ValidationMode.Auto |
| Model                     | Specifies the top-level model object for the form. An edit context will be constructed for this model.     If using this parameter, do not also supply a value for Validations.EditContext.                                                                                                                                                                                                                                                                                                                                                                                    | object         | null                |
| ValidateOnLoad            | If set to true, and Validations.Mode is set to ValidationMode.Auto, validation will run automatically on page load.Remarks When validation is placed inside of modal dialog, the behavior is a little different.      Modals are by definition always loaded and are always present in the DOM so no loading is ever happening again     after the page that contains the modal is first initialized.  Their visibility is controlled by display: none;     To workaround this, the actual "first load" for modals can be done by re-initializing Validations.Model parameter. | bool           | true                |

#### Validation

| Parameter    | Description                                                                           | Type             | Default               |
|--------------|---------------------------------------------------------------------------------------|------------------|-----------------------|
| ChildContent | Specifies the content to be rendered inside this Validation.                          | RenderFragment   | null                  |
| HandlerType  | Forces the custom validation handler to be used while validating the values.          | Type             | null                  |
| Status       | Gets the last received validation status.Possible values:None, Success, Error         | ValidationStatus | ValidationStatus.None |
| UsePattern   | Forces validation to use regex pattern matching instead of default validator handler. | bool             | false                 |

#### ValidationError

| Parameter    | Description                                                       | Type           | Default   |
|--------------|-------------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this ValidationError. | RenderFragment | null      |
| Multiline    | If true, shows the multiline error messages.                      | bool           | false     |
| Tooltip      | If true, shows the tooltip instead of label.                      | bool           | false     |

### Events

#### Validations

| Event         | Description                                                     | Type                                             |
|---------------|-----------------------------------------------------------------|--------------------------------------------------|
| StatusChanged | Event is fired whenever there is a change in validation status. | EventCallback<ValidationsStatusChangedEventArgs> |
| ValidatedAll  | Event is fired only after all of the validation are successful. | EventCallback                                    |

#### Validation

| Event            | Description                                                                                  | Type                                              |
|------------------|----------------------------------------------------------------------------------------------|---------------------------------------------------|
| AsyncValidator   | Gets the asynchronous validator handler attached to this validation.                         | Func<ValidatorEventArgs, CancellationToken, Task> |
| MessageLocalizer | Overrides the message that is going to be shown on the ValidationError or ValidationSuccess. | Func<string, IEnumerable<string>, string>         |
| StatusChanged    | Occurs each time that validation status changed.                                             | EventCallback<ValidationStatus>                   |
| Validator        | Gets the validator handler attached to this validation.                                      | Action<ValidatorEventArgs>                        |

### Methods

#### Validations

| Method                        | Description                                                                                                                                        | Return     | Parameters             |
|-------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|------------|------------------------|
| ValidateAll                   | Asynchronously runs the validation process for all validations and returns false if any is failed.                                                 | Task<bool> |                        |
| ClearAll                      | Clears all validation statuses.                                                                                                                    | Task       |                        |
| NotifyValidationInitialized   | Notifies the validation system that a new validation component has been initialized and adds it to the list of validations if not already present. | void       | IValidation validation |
| NotifyValidationRemoved       | Notifies the validation system that a validation component is being removed and removes it from the list of validations if present.                | void       | IValidation validation |
| NotifyValidationStatusChanged | Notifies the validation system that the status of a validation component has changed. This method handles the logic for updating the overall validation status based on the mode (Auto or Manual) and the current validation results.                     Remarks In Auto mode, this method triggers the aggregation of validation results and potentially raises a status changed event.     It is designed to minimize the number of status changed events by aggregating validation results.     Special consideration is needed to ensure that the status changed event is raised only once per validation cycle,     even if multiple validations fail.                                                                                                                                                    | void       | IValidation validation |

#### Validation

| Method                        | Description                                                                 | Return                 | Parameters                                            |
|-------------------------------|-----------------------------------------------------------------------------|------------------------|-------------------------------------------------------|
| InitializeInput               | Initializes the input component with the specified validation input. It performs an initial validation     if the mode is set to auto validation and validation on load is enabled.                     Remarks This method sets the input component and, based on the configuration, may asynchronously validate     the component's validation value. It also marks the component as initialized.                                                                             | Task                   | IValidationInput inputComponent                       |
| InitializeInputPattern        | Initializes or updates the input validation pattern. If the pattern string changes,     a new regex pattern is created, and the input is re-validated if applicable.                     Remarks This method optimizes performance by avoiding re-instantiation of the regex pattern if it has not changed.     It ensures that validation is only re-triggered if the component has been initialized and validation conditions are met.                                                                             | Task                   | string patternString, T value                         |
| InitializeInputExpression     | Initializes or updates the input based on a specified expression. This is primarily used for data-annotation validation.                     Remarks This method is designed to work with models and edit contexts, allowing for dynamic validation based on expressions.     It ensures that validation is only re-triggered if the component has been initialized and validation conditions are met.                                                                             | Task                   | Expression<Func<T>> expression                        |
| NotifyInputChanged            | Notifies that an input's value has changed and optionally re-validates the input.                     Remarks If the edit context is set and a field identifier has been established, this method notifies the edit context     of the field change. It then conditionally triggers validation based on the component's mode.                                                                             | Task                   | T newExpressionValue, bool overrideNewValue           |
| Validate                      | Runs the validation process.                                                | ValidationStatus       |                                                       |
| Validate                      | Runs the validation process.                                                | ValidationStatus       | object newValidationValue                             |
| ValidateAsync                 | Runs the asynchronous validation process based on the last available value. | Task<ValidationStatus> |                                                       |
| ValidateAsync                 | Runs the asynchronous validation process.                                   | Task<ValidationStatus> | object newValidationValue                             |
| Clear                         | Clears the validation status.                                               | void                   |                                                       |
| NotifyValidationStarted       | Notifies the validation that validation process has being activated.        | void                   |                                                       |
| NotifyValidationStatusChanged | Notifies the validation with the new status and messages.                   | void                   | ValidationStatus status, IEnumerable<string> messages |

###### On this page

#### 

## 