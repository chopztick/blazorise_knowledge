# Blazorise Testing Guide

Get started testing with Blazor and Blazorise in no time.

## Testing with bUnit

To ensure proper functioning during testing, it's necessary to set up an internal Blazorise Service as Transient. This adjustment is crucial to avoid errors from the bUnit testing framework. Implement the following configuration:

ctx.Services.AddBlazorise().Replace(ServiceDescriptor.Transient&lt;IComponentActivator, ComponentActivator&gt;());

Apart from this setup, the system should operate seamlessly. If you encounter any challenges, please reach out for assistance.

Additionally, for guidance on testing, you might find it useful to review some of our test cases. If you're looking for a starter package to facilitate testing of Blazorise components with bUnit, please refer to the subsequent section for more information.

## Setup Project

For initiating tests on Blazorise components using bUnit, we offer a supportive package.

### bUnit

The initial action involves installing a Blazorise testing package:

```
Install-Package Blazorise.Tests.bUnit
```

Following this, it's necessary to configure the dependencies of your project:

```
Services
	.AddBlazoriseTests()
	.AddBootstrapProviders()
	.AddEmptyIconProvider();
```

### Mocking

The package includes both AddBlazoriseTests and AddEmptyIconProvider. For providers, you have the flexibility to choose from any Blazorise provider options.

In bUnit testing, it's necessary to mock JavaScript interop calls due to their specific operational nature. Our package also offers methods to mock these JavaScript interop calls for various Blazorise components. For instance, to mock the JavaScript interop calls for the Blazorise Button component, you would use:

```
JSInterop.AddBlazoriseButton();
```

###### On this page

#### 

## 