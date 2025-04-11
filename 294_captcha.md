# Blazorise Captcha component

Integrate simple captchas into your Blazor applications with the Blazorise Captcha component.

This extension supports multiple captcha providers, enabling the addition of captcha functionality with provider-specific settings.

## Supported Captcha providers

Google reCAPTCHA Implemented via Blazorise.Captcha.ReCaptcha

## Installation

### 1. General Installation

Install the base captcha extension from NuGet.

```
Install-Package Blazorise.Captcha
```

### 2. Provider-Specific Installation

Install the ReCaptcha provider extension from NuGet.

```
Install-Package Blazorise.Captcha.ReCaptcha
```

### 3. Registering Services for reCAPTCHA

Incorporate ReCaptcha services by adding the following code to the relevant sections of .

```
using Blazorise.Captcha.ReCaptcha;

builder.Services
	.AddBlazorise( options =>
	{
		options.Immediate = true;
	} )
	.AddBlazoriseGoogleReCaptcha( reCaptchaOptions =>
	{
		reCaptchaOptions.SiteKey = Configuration["ReCaptchaSiteKey"]
		//Set any other ReCaptcha options here...
	});
```

### 4. Imports

In your main , ensure you include:

```
@using Blazorise.Captcha
```

### 5. Static Files - ReCaptcha

Modify your project's HTML template to include the google reCAPTCHA js files. The files you add depend on whether you're working with a WebAssembly or Server project:

For WebAssembly, update index.html.
                

                    For Server, update \_Layout.cshtml or \_Host.cshtml.
                

                    For .NET 8, update App.razor.

Google reCAPTCHA docs recommend adding the script to the end of the &lt;head&gt; tag with async and defer attributes.

```
<script src="https://www.google.com/recaptcha/api.js" async defer></script>
```

## Examples

### ReCaptcha Checkbox

The following example demonstrates how to use the  integration.
        You can use the  to configure the widget according to your needs.

```
@using Microsoft.Extensions.Options
@using System.Text.Json

<Div Flex="Flex.AlignItems.Center" Gap="Gap.Is3">
    <Captcha @ref="@captcha" Solved="@Solved" Validate="@Validate" Expired="Expired" />

    <Button Background="Background.Primary" Clicked="@Reset">
        Reset
    </Button>
</Div>
```

```
@code {
    [Inject] IOptions<AppSettings> AppSettings { get; set; }

    [Inject] IHttpClientFactory HttpClientFactory { get; set; }

    private Captcha captcha;

    private void Solved( CaptchaState state )
    {
        Console.WriteLine( $"Captcha Success: {state.Valid}" );
    }

    private void Expired()
    {
        Console.WriteLine( "Captcha Expired" );
    }

    private async Task<bool> Validate( CaptchaState state )
    {
        Console.WriteLine( "Captcha Validate" );

        //Perform server side validation
        //You should make sure to implement server side validation
        //https://developers.google.com/recaptcha/docs/verify
        //Here's a simple example:
        var content = new FormUrlEncodedContent( new[]
        {
            new KeyValuePair<string, string>("secret", AppSettings.Value.ReCaptchaServerKey),
            new KeyValuePair<string, string>("response", state.Response),
         } );

        var httpClient = HttpClientFactory.CreateClient();
        var response = await httpClient.PostAsync( "https://www.google.com/recaptcha/api/siteverify", content );

        var result = await response.Content.ReadAsStringAsync();
        var googleResponse = JsonSerializer.Deserialize<GoogleResponse>( result, new JsonSerializerOptions()
            {
                PropertyNamingPolicy = JsonNamingPolicy.CamelCase
            } );

        return googleResponse.Success;
    }

    private async Task Reset()
    {
        await captcha.Reset();
    }

    public class GoogleResponse
    {
        public bool Success { get; set; }
        public double Score { get; set; } //V3 only - The score for this request (0.0 - 1.0)
        public string Action { get; set; } //v3 only - An identifier
        public string Challenge_ts { get; set; }
        public string Hostname { get; set; }
        public string ErrorCodes { get; set; }
    }
}
```

## API

### Events

| Event    | Description                                                                                                     | Type                           |
|----------|-----------------------------------------------------------------------------------------------------------------|--------------------------------|
| Expired  | The Captcha expired event.                                                                                      | EventCallback                  |
| Solved   | A Captcha solved event.      Provides contextual information about the Captcha state after the user has solved. | EventCallback<CaptchaState>    |
| Validate | A Captcha validation event. Further validation may be performed here.                                           | Func<CaptchaState, Task<bool>> |

### Methods

| Method   | Description          | Return   | Parameters   |
|----------|----------------------|----------|--------------|
| Submit   | Submits the Captcha. | Task     |              |
| Reset    | Resets the Captcha.  | Task     |              |

### ReCaptchaOptions

| Name          | Description                                   | Type                   | Default                          |
|---------------|-----------------------------------------------|------------------------|----------------------------------|
| SiteKey       | The client side api key for google reCAPTCHA. | string                 |                                  |
| Size          | The size of the widget.                       | ReCaptchaSize          | ReCaptchaSize.Normal             |
| Theme         | The color theme of the widget.                | ReCaptchaTheme         | ReCaptchaTheme.Light             |
| BadgePosition | Reposition the reCAPTCHA badge. 'inline' lets you position it with CSS.         This option is only available for invisible reCAPTCHA.                                               | ReCaptchaBadgePosition | ReCaptchaBadgePosition.BottomEnd |
| LanguageCode  | Refer to: https://developers.google.com/recaptcha/docs/language         Defaults to: 'en' (English (US))                                               | string                 | en                               |

###### On this page

#### 

## 