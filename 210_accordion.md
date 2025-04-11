# Blazorise Accordion component

An accordion allows users to toggle the display of sections of content.

## Overview

Accordion is a vertically stacked set of expandable panels. It reduces clutter and helps maintain the user's focus by showing only the relevant content at any time.

## Structure

The Accordion structure is very simple:

- &lt; Accordion&gt; the main container.
- &lt;Accordion&gt; the main container.
    - &lt; AccordionItem&gt; defines a collapsible element - controled by the Visible state.
    - &lt;AccordionItem&gt; defines a collapsible element - controled by the Visible state.
        - &lt; AccordionHeader&gt; the header that will always be shown - this is where you would put a toggle element (such as a Button ).
        - &lt;AccordionHeader&gt; the header that will always be shown - this is where you would put a toggle element (such as a Button).
            - &lt;AccordionToggle&gt; the specialized button used to toggle the state of accordion and the accordion item components.
        - &lt;AccordionBody&gt; the main content of the accordion item.

## Examples

### Default accordion

Use the @bind-Visible parameter to properly keep previously opened accordion elements unchanged.

##### What is Blazorise?

Blazorise is a component library built on top of Blazor, which is a framework from Microsoft for building interactive client-side web UIs using .NET. Blazorise provides a rich set of components that are easy to use and customizable, helping developers to build responsive and modern web applications more efficiently.

##### What CSS  frameworks does Blazorise support?

Blazorise supports several CSS frameworks, including Bootstrap (known for responsive design elements), Bulma (valued for simplicity and Flexbox base), Material (inspired by Google's Material Design), Ant Design (geared towards enterprise-level products and adapting React components' design principles), and Tailwind CSS (famous for its utility-first approach and versatility). These frameworks provide distinct styles and philosophies, offering developers a range of options to best suit their project's requirements.

##### What are the benefits of Blazorise commercial license?

A Blazorise commercial license typically includes access to advanced components, priority support, options for dedicated consultations, frequent updates and bug fixes, a license for unrestricted commercial use, potential access to the source code, and opportunities for training and workshops. This package enhances functionality, offers better support, and provides operational security for commercial projects.

```
<Accordion>
    <AccordionItem @bind-Visible="@accordionItem1Visible">
        <AccordionHeader>
            <Heading Size="HeadingSize.Is5">
                <AccordionToggle>What is Blazorise?</AccordionToggle>
            </Heading>
        </AccordionHeader>
        <AccordionBody>
            Blazorise is a component library built on top of Blazor, which is a framework from Microsoft for building interactive client-side web UIs using .NET. Blazorise provides a rich set of components that are easy to use and customizable, helping developers to build responsive and modern web applications more efficiently.
        </AccordionBody>
    </AccordionItem>
    <AccordionItem @bind-Visible="@accordionItem2Visible">
        <AccordionHeader>
            <Heading Size="HeadingSize.Is5">
                <AccordionToggle>What CSS  frameworks does Blazorise support?</AccordionToggle>
            </Heading>
        </AccordionHeader>
        <AccordionBody>
            Blazorise supports several CSS frameworks, including Bootstrap (known for responsive design elements), Bulma (valued for simplicity and Flexbox base), Material (inspired by Google's Material Design), Ant Design (geared towards enterprise-level products and adapting React components' design principles), and Tailwind CSS (famous for its utility-first approach and versatility). These frameworks provide distinct styles and philosophies, offering developers a range of options to best suit their project's requirements.
        </AccordionBody>
    </AccordionItem>
    <AccordionItem @bind-Visible="@accordionItem3Visible">
        <AccordionHeader>
            <Heading Size="HeadingSize.Is5">
                <AccordionToggle>What are the benefits of Blazorise commercial license?</AccordionToggle>
            </Heading>
        </AccordionHeader>
        <AccordionBody>
            A Blazorise commercial license typically includes access to advanced components, priority support, options for dedicated consultations, frequent updates and bug fixes, a license for unrestricted commercial use, potential access to the source code, and opportunities for training and workshops. This package enhances functionality, offers better support, and provides operational security for commercial projects.
        </AccordionBody>
    </AccordionItem>
</Accordion>
```

```
@code {
    bool accordionItem1Visible = true;
    bool accordionItem2Visible = false;
    bool accordionItem3Visible = false;
}
```

Please note the changes starting from 1.5 versions:
        
Button is obsolete: Placing a regular Button component inside of Accordion is no longer recommended and should be replaced with new &lt;AccordionToggle&gt; component.
                
Collapse is obsolete: Placing a regular &lt;Collapse&gt; component inside of Accordion is no longer recommended and should be replaced with the new &lt;AccordionHeader&gt;, and &lt;AccordionBody&gt;, &lt;AccordionItem&gt; components.

## API

### Parameters

#### Accordion

| Parameter    | Description                                                 | Type           | Default   |
|--------------|-------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this Accordion. | RenderFragment | null      |

#### AccordionToggle

| Parameter    | Description                                                       | Type           | Default   |
|--------------|-------------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this AccordionToggle. | RenderFragment | null      |

#### AccordionItem

| Parameter    | Description                                                     | Type           | Default   |
|--------------|-----------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this AccordionItem. | RenderFragment | null      |
| Visible      | Gets or sets the accordion item visibility state.               | bool           | false     |

#### AccordionHeader

| Parameter    | Description                                                       | Type           | Default   |
|--------------|-------------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this AccordionHeader. | RenderFragment | null      |

#### AccordionBody

| Parameter    | Description                                                     | Type           | Default   |
|--------------|-----------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this AccordionBody. | RenderFragment | null      |

### Events

#### AccordionToggle

| Event   | Description                               | Type                          |
|---------|-------------------------------------------|-------------------------------|
| Clicked | Occurs when the toggle button is clicked. | EventCallback<MouseEventArgs> |

#### AccordionItem

| Event          | Description                                              | Type                |
|----------------|----------------------------------------------------------|---------------------|
| VisibleChanged | Occurs when the accordion item visibility state changes. | EventCallback<bool> |

#### AccordionHeader

| Event   | Description                                  | Type                          |
|---------|----------------------------------------------|-------------------------------|
| Clicked | Occurs when the accordion header is clicked. | EventCallback<MouseEventArgs> |

### Methods

#### AccordionItem

| Method   | Description                                  | Return   | Parameters   |
|----------|----------------------------------------------|----------|--------------|
| Toggle   | Toggles the accordion item visibility state. | Task     |              |

###### On this page

#### 

## 