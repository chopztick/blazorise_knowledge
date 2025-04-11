# Blazorise ModalProvider component

Programatically instantiate modals with custom content.

The modal provider component provides an abstraction on top of Blazorize's Modal component, enabling you to programatically instantiate modals with custom content/components.

### Usage

You need to place &lt;ModalProvider&gt; somewhere in your application
            razor code. It can be placed anywhere, but a good approach is to place it in App.razor like in
            the following example.

A IModalService will be registered by Blazorise providing you with an API to programatically instantiate modals.
            Examples are provided further below.

```
<Router AppAssembly="typeof(App).Assembly">
    <Found>...</Found>
    <NotFound>...</NotFound>
</Router>

<ModalProvider />
```

### The IModalService

The  is an important feature that lets you control  instantiation.
        You are provided with various overloads of  to instantiate the  to your liking.
        This will return a  that represents the  you've instantiated with all of its configuration.
        You may also use the provided  method to close modals.

### Options

You may provide options to  globally by setting them on the  component itself.

```
<Router AppAssembly="typeof(App).Assembly">
    <Found>...</Found>
    <NotFound>...</NotFound>
</Router>

<ModalProvider UseModalStructure Animated Size="ModalSize.Fullscreen" />
```

Optionally you can override these when instantiating a modal through the  usage.

```
<Button Clicked="InstantiateModal"></Button>
```

```
@code {
    [Inject] public IModalService ModalService { get; set; }

    public Task InstantiateModal()
    {
        return ModalService.Show<ModalServiceOptionsExample>( "Override Options Example", new ModalInstanceOptions()
        {
            Animated = false,
            UseModalStructure = false,
            Size = ModalSize.Small
        } );
    }
}
```

### Closing the instantiated Modals

&lt;ModalProvider&gt; will only keep track of the modals that have been instantiated by itself.

To close a Modal:

You can use Blazorise's &lt;CloseButton&gt; component, which automatically knows how to close the currently opened &lt;Modal&gt;.
                

                    Use the provided IModalService and call IModelService.Hide(), this will close the last opened &lt;Modal&gt; tracked by the &lt;ModalProvider&gt;.
                

                    You may keep track of the ModalInstance and call IModalService.Hide(modalInstance), this will close the provided instance.
                

                    You may keep track of the ModalInstance and call modalInstance.ModalRef.Hide().

### Stateful Instantied Modals

&lt;ModalProvider&gt; can keep the state of the modals even after they have been closed.

To do this you will need to:

Set Stateful to true in the ModalProvider or in the ModalInstanceOptions.
                    The reason why you need to explicitly opt-in for this feature is because the instances you open will be kept in memory, and you should be mindful that you need to properly manage these.
                

                    Provide a unique Id so the instance can be tracked and reopen. This can be set in ModalInstanceOptions.ElementId.
                    Optionally you may keep track of the ModalInstance returned by the IModalService.Show() method to reopen the same instance.
                

                    Control how the modal renders, by setting the RenderMode.
                    If you'd like the state to be kept, use: ModalRenderMode.Default or ModalRenderMode.LazyLoad.

## Examples

### Instantiate a modal with a custom component

Instantiates a modal with a counter example taking in the counter number from the provided parameter.
         provides various overloads you can use to instantiate your custom content.

```
<Button Color="Color.Primary" Clicked="ShowCounter">Show Counter</Button>
```

```
@code {
    [Inject] public IModalService ModalService { get; set; }

    public Task ShowCounter()
    {
        Random random = new();
        var newValue = random.NextInt64( 100 );
        return ModalService.Show<CounterExample>( "My Custom Content!", x => x.Add( x => x.Value, newValue ) );
    }
}
```

ShowCounter.razor

```
<Heading>Counter</Heading>

<Paragraph>@Value</Paragraph>

<Button Color="Color.Primary" Clicked="Increment">Increment</Button>
```

```
@code {
    [Parameter] public long Value { get; set; }

    private void Increment()
    {
        Value++;
    }
}
```

### Instantiate a modal with a custom render fragment

```
<Button Color="Color.Primary" Clicked="ShowRenderFragment">Show Custom Structure</Button>
```

```
@code {
    [Inject] public IModalService ModalService { get; set; }

    private RenderFragment customFragment => __builder =>
    {
        <Paragraph>This content is provided by a custom RenderFragment</Paragraph>
    };

    public Task ShowRenderFragment()
    {
        return ModalService.Show( "My Custom RenderFragment!", customFragment );
    }
}
```

### Instantiate a modal with custom structure

If you want to customize the modal structure, you can do so, by setting UseModalStructure to false and providing the structure inside the custom content you are instantiating.
            You may do this by providing your custom html or by using the internal Modal components.

&lt;ModalHeader&gt;
&lt;ModalBody&gt;
&lt;ModalFooter&gt;

```
<Field Horizontal>
    <FieldLabel ColumnSize="ColumnSize.IsFull.OnTablet.Is2.OnDesktop">User Name</FieldLabel>
    <FieldBody ColumnSize="ColumnSize.IsFull.OnTablet.Is10.OnDesktop">
        <TextEdit @bind-Text="userName"></TextEdit>
    </FieldBody>
</Field>

<Button Color="Color.Primary" Clicked="ShowCustomStructure">Show Custom Structure</Button>
```

```
@code {
    [Inject] public IModalService ModalService { get; set; }
    private string userName = "John Doe";

    public Task ShowCustomStructure()
    {
        return ModalService.Show<CustomStructureModalExample>( parameters => parameters.Add( x => x.UserName, userName ), new ModalInstanceOptions() { UseModalStructure = false } );
    }
}
```

CustomStructureModalExample.razor

```
<ModalHeader>
    <ModalTitle>My Custom Structure</ModalTitle>
    <CloseButton />
</ModalHeader>
<ModalBody MaxHeight="70">
    Welcome @UserName!
</ModalBody>
<ModalFooter>
    <Button Color="Color.Success" Clicked="Confirm">Cheers!</Button>
</ModalFooter>
```

```
@code {
    [Inject] public IModalService ModalService { get; set; }

    [Parameter] public string UserName { get; set; }

    private async Task Confirm()
    {
        await ModalService.Hide();
    }
}
```

### Interaction

Since you can pass in parameters into your component, you can take advantage of this to interact with your .
        A common example, might be a generic formulary where the validation and success logic are not necessarily known by this component and are provided from "outside".
        The following example, setups a simple formulary showcasing this.

```
<Paragraph>
    @formularyMessage
</Paragraph>
<Button Color="Color.Primary" Clicked="ShowFormulary">Show</Button>
```

```
@code {
    [Inject] public IModalService ModalService { get; set; }

    private string formularyMessage = "";

    public Task ShowFormulary()
    {
        formularyMessage = string.Empty;
        return ModalService.Show<FormularyModalExample>( x =>
        {
            x.Add( x => x.OnValidate, FormularyValidate );
            x.Add( x => x.OnSuccess, FormularySuccess );
        },
        new ModalInstanceOptions()
            {
                UseModalStructure = false
            } );
    }

    private Task<bool> FormularyValidate( Employee employee )
        => Task.FromResult( !string.IsNullOrWhiteSpace( employee.FirstName ) && !string.IsNullOrWhiteSpace( employee.Email ) );

    private Task FormularySuccess( Employee employee )
    {
        formularyMessage = $"Employee : {employee.FirstName} saved successfully!";
        return InvokeAsync( StateHasChanged );
    }
}
```

FormularyModalExample.razor

```
<ModalHeader>
    <ModalTitle>
        Please fill in the formulary
    </ModalTitle>
    <CloseButton />
</ModalHeader>
<ModalBody>
    <Field Horizontal>
        <FieldLabel ColumnSize="ColumnSize.IsFull.OnTablet.Is3.OnDesktop">First Name</FieldLabel>
        <FieldBody ColumnSize="ColumnSize.IsFull.OnTablet.Is9.OnDesktop">
            <TextEdit @bind-Text="model.FirstName"></TextEdit>
        </FieldBody>
    </Field>

    <Field Horizontal>
        <FieldLabel ColumnSize="ColumnSize.IsFull.OnTablet.Is3.OnDesktop">Email</FieldLabel>
        <FieldBody ColumnSize="ColumnSize.IsFull.OnTablet.Is9.OnDesktop">
            <TextEdit @bind-Text="model.Email"></TextEdit>
        </FieldBody>
    </Field>

    @if ( !isValid )
    {
        <Paragraph>
            <Label>Invalid Submission!</Label>
        </Paragraph>
    }
</ModalBody>
<ModalFooter>
    <Button Color="Color.Success " Clicked="Confirm">Confirm</Button>
    <Button Color="Color.Secondary" Clicked="ModalService.Hide">Close</Button>
</ModalFooter>
```

```
@code {
    private Employee model = new();
    private bool isValid = true;
    [Inject] public IModalService ModalService { get; set; }
    [Parameter] public Func<Employee, Task<bool>> OnValidate { get; set; }
    [Parameter] public Func<Employee, Task> OnSuccess { get; set; }

    private async Task Confirm()
    {
        if ( OnValidate is not null )
            isValid = await OnValidate( model );

        if ( !isValid )
        {
            return;
        }

        await OnSuccess( model );
        await ModalService.Hide();
    }
}
```

### Instantiate a stateful modal

```
<Button Color="Color.Primary" Clicked="ShowStateful">Show Stateful</Button>
```

```
@code {
    [Inject] public IModalService ModalService { get; set; }

    public Task ShowStateful()
    {
        return ModalService.Show<CounterExample>( "My Stateful content", new ModalInstanceOptions()
        {
            Stateful = true,
            ElementId = "Stateful",
            RenderMode = ModalRenderMode.LazyLoad
        } );
    }
}
```

## API

### Attributes

You will find that &lt;ModalProvider&gt; provides most regular &lt;Modal&gt; parameters for you to override the modal behaviour.

#### ModalProvider

| Name              | Description                                                                                                        | Type                              | Default   |
|-------------------|--------------------------------------------------------------------------------------------------------------------|-----------------------------------|-----------|
| UseModalStructure | Uses the modal standard structure, by setting this to true you are only in charge of providing the custom content. | boolean                           | true      |
| Stateful          | Keeps the ModalInstance in memory after it has been closed.                                                        | boolean                           | false     |
| Visible           | Handles the visibility of modal dialog.                                                                            | boolean                           | false     |
| VisibleChanged    | Occurs when the modal visibility state changes.                                                                    | EventCallback<bool>               |           |
| Opening           | Occurs before the modal is opened and can be used to prevent the modal from opening.                               | Func<ModalOpeningEventArgs, Task> |           |
| Closing           | Occurs before the modal is closed and can be used to prevent the modal from closing.                               | Func<ModalClosingEventArgs, Task> |           |
| Opened            | Occurs after the modal has opened.                                                                                 | EventCallback                     |           |
| Closed            | Occurs after the modal has closed.                                                                                 | EventCallback                     |           |
| ScrollToTop       | If true modal will scroll to top when opened.                                                                      | boolean                           | true      |
| ShowBackdrop      | If true the the backdrop will be rendered.                                                                         | boolean                           | true      |
| Animated          | Gets or sets whether the component has any animations.                                                             | boolean                           | true      |
| AnimationDuration | Gets or sets the animation duration.                                                                               | int                               | 150       |
| RenderMode        | Defines how the modal content will be rendered.                                                                    | ModalRenderMode                   | Default   |
| FocusTrap         | Defines if the modal should keep the input focus at all times.                                                     | bool?                             | true      |
| Centered          | Centers the modal vertically.                                                                                      | boolean                           | false     |
| Scrollable        | Scrolls the modal content independent of the page itself.                                                          | boolean                           | false     |
| Size              | Changes the size of the modal.                                                                                     | ModalSize                         | Default   |

###### On this page

#### 

## 