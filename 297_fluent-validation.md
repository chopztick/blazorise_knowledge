# Blazorise FluentValidation component

A validation component for building strongly-typed validation rules.

This extension component is based on FluentValidation, a validation library for .NET that uses a fluent interface and lambda expressions for building strongly-typed validation rules.

## Installation

### 1. NuGet

Install extension from NuGet.

```
Install-Package Blazorise.FluentValidation
Install-Package FluentValidation.DependencyInjectionExtensions
```

### 2. Imports

In your main  add:

```
@using Blazorise.FluentValidation
```

### 3. Register Blazorise Services

Add the following lines to the relevant sections of .

```
using Blazorise;
using Blazorise.Bootstrap;
using Blazorise.Icons.FontAwesome;
using Blazorise.FluentValidation;

builder.Services
    .AddBlazorise()
    .AddBootstrapProviders()
    .AddFontAwesomeIcons()
    .AddBlazoriseFluentValidation();

services.AddValidatorsFromAssembly( typeof( App ).Assembly );
```

## Examples

### Basic

The process of validating the model is similar to our data annotation on our Validation component. First, as usual, we define the Model parameter. After which, we need to determine the HandlerType. To make it easier, we have allowed the definition of HandlerType on the &lt;Validations&gt; level.

By defining the handler type on a &lt;Validations&gt; level, it will be shared and used by all the &lt;Validation&gt; components inside it. Thus, no need to specify the handler type on each &lt;Validation&gt; component.

```
@using Blazorise.FluentValidation

<Validations @ref="@fluentValidations" Mode="ValidationMode.Manual" Model="@person" HandlerType="typeof(FluentValidationHandler)">
    <Validation>
        <Field>
            <FieldLabel>First name</FieldLabel>
            <TextEdit Placeholder="Enter first name..." @bind-Text="@person.FirstName">
                <Feedback>
                    <ValidationError />
                </Feedback>
            </TextEdit>
        </Field>
    </Validation>
    <Validation>
        <Field>
            <FieldLabel>Last name</FieldLabel>
            <TextEdit Placeholder="Enter last name..." @bind-Text="@person.LastName">
                <Feedback>
                    <ValidationError />
                </Feedback>
            </TextEdit>
        </Field>
    </Validation>
    <Validation>
        <Field>
            <FieldLabel>Age</FieldLabel>
            <NumericEdit Placeholder="Enter age..." @bind-Value="@person.Age">
                <Feedback>
                    <ValidationError />
                </Feedback>
            </NumericEdit>
        </Field>
    </Validation>
</Validations>

<Button Color="Color.Primary" Clicked="@OnSavePerson">Save</Button>
```

```
@code {
    Validations fluentValidations;

    Person person = new();

    protected async Task OnSavePerson()
    {
        if ( await fluentValidations.ValidateAll() )
        {
            // the person is validated and we can proceed with the saving process
        }
    }
}
```

Don't forget to create the  for your .

```
public class PersonValidator : AbstractValidator<Person>
{
    public PersonValidator()
    {
        RuleFor( vm => vm.FirstName )
            .NotEmpty()
            .MaximumLength( 30 );

        RuleFor( vm => vm.LastName )
            .NotEmpty()
            .MaximumLength( 30 );

        RuleFor( vm => vm.Age )
            .GreaterThanOrEqualTo( 18 );
    }
}
```

###### On this page

#### 

## 