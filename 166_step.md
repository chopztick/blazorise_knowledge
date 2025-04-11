# Blazorise Step component

The Step component displays progress through numbered steps.

Similar to Tabs component, the step component have the same structure and usage.

- &lt; Steps&gt; container for Step items.
- &lt;Steps&gt; container for Step items.
    - &lt; Items&gt; collection of step items.
    - &lt;Items&gt; collection of step items.
        - &lt;Step&gt; individual step item, which can be clicked to navigate to the step content.
    - &lt; Content&gt; container for step content.
    - &lt;Content&gt; container for step content.
        - &lt;StepPanel&gt; individual step content, which is displayed when the step item is clicked.

The Steps component is container for Step items. The Name of each step
    item should match the Name of a step panel(if panels are used).

- &lt; StepsContent&gt; container for step panels
    - &lt;StepPanel&gt; container for step content

The step content container is used to hold step panels. Each content pane also has a unique Name,
    which is targeted by a link in the step-strip.

Most of the time you will only need to use Steps component as it is crafted to hold both clickable
    step items and step content. Only in the advanced scenario where the content will be separated from the step items
    you will need to use StepsContent component.

## Examples

### Basic

- 1
Create campaign settings
- 2
Create an ad group
- 3
Create an add
- Finish

Content for step 1.

Content for step 2.

Content for step 3.

Content for finish.

```
<Steps SelectedStep="@selectedStep" SelectedStepChanged="@OnSelectedStepChanged">
    <Items>
        <Step Name="step1">Create campaign settings</Step>
        <Step Name="step2">Create an ad group</Step>
        <Step Name="step3">Create an add</Step>
        <Step Name="step4">
            <Marker>
                <Icon Name="IconName.Flag" />
            </Marker>
            <Caption>
                Finish
            </Caption>
        </Step>
    </Items>
    <Content>
        <StepPanel Name="step1">
            Content for step 1.
        </StepPanel>
        <StepPanel Name="step2">
            Content for step 2.
        </StepPanel>
        <StepPanel Name="step3">
            Content for step 3.
        </StepPanel>
        <StepPanel Name="step4">
            Content for finish.
        </StepPanel>
    </Content>
</Steps>
```

```
@code{
    string selectedStep = "step1";

    private Task OnSelectedStepChanged( string name )
    {
        selectedStep = name;

        return Task.CompletedTask;
    }
}
```

### Navigation Control

Basic steps navigation has no constraints, so it is possible to jump to any steps by clicking on them. However, this is usually impossible in real-world scenarios as sometimes a user is required to enter valid data before proceeding to the next step.

To control the navigation between the steps, you need to use the NavigationAllowed parameter, which acts as a function that has all the information you need to validate the page switch.

- 1
Step 1
- 2
Step 2
- 3
Step 3
- 4
Step 4

Step 1

Step 3

Step 4

```
<Steps @ref="stepsRef" @bind-SelectedStep="selectedStep" NavigationAllowed="NavigationAllowed">
    <Items>
        <Step Name="1">Step 1</Step>
        <Step Name="2">Step 2</Step>
        <Step Name="3">Step 3</Step>
        <Step Name="4">Step 4</Step>
    </Items>
    <Content>
        <StepPanel Name="1">
            Step 1
        </StepPanel>
        <StepPanel Name="2">
            <Field>
                <FieldLabel>Email address</FieldLabel>
                <TextEdit @bind-Text="email" Placeholder="Enter email">
                    <FieldHelp>This field is required in order to procceed to the next step.</FieldHelp>
                </TextEdit>
            </Field>
        </StepPanel>
        <StepPanel Name="3">
            Step 3
        </StepPanel>
        <StepPanel Name="4">
            Step 4
        </StepPanel>
    </Content>
</Steps>
<Div Display="Display.Flex" Class="justify-content-center">
    <Button Color="Color.Secondary" Margin="Margin.Is2.FromEnd" Clicked="() => stepsRef.PreviousStep()">
        Previous
    </Button>
    <Button Color="Color.Primary" Clicked="() => stepsRef.NextStep()">
        Next
    </Button>
</Div>
```

```
@code {
    private Steps stepsRef;
    private string email;
    private string selectedStep = "2";

    private bool NavigationAllowed( StepNavigationContext context )
    {
        if ( context.CurrentStepIndex == 2 && context.NextStepIndex > 2 && !ValidationRule.IsEmail( email ) )
        {
            return false;
        }

        return true;
    }
}
```

## API

### Parameters

#### Steps

| Parameter    | Description                                             | Type           | Default   |
|--------------|---------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this Steps. | RenderFragment | null      |
| Content      | Template for placing the StepPanel items.               | RenderFragment | null      |
| Items        | Template for placing the Step items.                    | RenderFragment | null      |
| SelectedStep | Gets or sets currently selected step name.              | string         |           |

#### Step

| Parameter    | Description                                                          | Type           | Default       |
|--------------|----------------------------------------------------------------------|----------------|---------------|
| Caption      | Custom render template for the text part of the step item.           | RenderFragment | null          |
| ChildContent | Specifies the content to be rendered inside this Step.               | RenderFragment | null          |
| Color        | Overrides the step color.                                            | Color          | Color.Default |
| Completed    | Marks the step as completed.                                         | bool           | false         |
| Index        | Overrides the index of the step item.                                | int?           | null          |
| Marker       | Custom render template for the marker(circle) part of the step item. | RenderFragment | null          |
| Name         | Defines the step name.                                               | string         |               |

#### StepsContent

| Parameter     | Description                                                    | Type           | Default   |
|---------------|----------------------------------------------------------------|----------------|-----------|
| ChildContent  | Specifies the content to be rendered inside this StepsContent. | RenderFragment | null      |
| SelectedPanel | Gets or sets currently selected panel name.                    | string         |           |

#### StepPanel

| Parameter    | Description                                                     | Type           | Default   |
|--------------|-----------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this StepPanel.     | RenderFragment | null      |
| Name         | Defines the panel name. Must match the corresponding step name. | string         |           |

### Events

#### Steps

| Event               | Description                                 | Type                              |
|---------------------|---------------------------------------------|-----------------------------------|
| NavigationAllowed   | Disables navigation by clicking on step.    | Func<StepNavigationContext, bool> |
| SelectedStepChanged | Occurs after the selected step has changed. | EventCallback<string>             |

#### Step

| Event   | Description                      | Type                          |
|---------|----------------------------------|-------------------------------|
| Clicked | Occurs when the item is clicked. | EventCallback<MouseEventArgs> |

#### StepsContent

| Event                | Description                                  | Type                  |
|----------------------|----------------------------------------------|-----------------------|
| SelectedPanelChanged | Occurs after the selected panel has changed. | EventCallback<string> |

### Methods

#### Steps

| Method       | Description                       | Return   | Parameters      |
|--------------|-----------------------------------|----------|-----------------|
| SelectStep   | Sets the active step by the name. | Task     | string stepName |
| NextStep     | Goes to the next step.            | Task     |                 |
| PreviousStep | Goes to the previous step.        | Task     |                 |

#### StepsContent

| Method      | Description               | Return   | Parameters   |
|-------------|---------------------------|----------|--------------|
| SelectPanel | Select the panel by name. | Task     | string name  |

###### On this page

#### 

## 