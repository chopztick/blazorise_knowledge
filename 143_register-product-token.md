# Register Blazorise Product Token in Blazor Application

Quickly setup Blazorise Product Token.

## Overview

All evaluators and paid customers who use NuGet packages from NuGet.org are eligible for the Blazorise products token. As a result, if you use the evaluation installer or the NuGet feed to reference Blazorise assemblies, you must also include the platform and version product tokens in your projects.

Read more about Blazorise license on our Licensing page.

## Setup

### Log in to your Blazorise account

Go to the Blazorise website and log in to your account using your username and password.

### Generate your unique Product Token

Once you are logged in, navigate to the "License" section of your account.
        

            Click the "Generate" button to create your unique product token.

### Add the Product Token

Open the solution containing your Blazor application in Visual Studio or another development environment.

In the Startup class, find the ConfigureServices method. This method is used to configure the services used in your Blazor application.

In the ConfigureServices method, add the following code snippet.

```
services
    .AddBlazorise( options =>
    {
        options.ProductToken = "<your-product-token>";
    } )
```

Save the changes you made to the Startup class. Run your Blazor application and your product token will now be registered.

If you encounter any issues or need assistance, please don't hesitate to contact the Blazorise team.

###### On this page

#### 

## 