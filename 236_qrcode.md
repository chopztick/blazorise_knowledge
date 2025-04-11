# Blazorise QR Code component

A component used to generate QR codes.

QR codes are great for presenting short amounts of information to people who can scan them rapidly with their smartphones. Because most smartphones come with built-in QR code scanners, simply pointing the camera at a QR code will decode it, allowing the user to browse a website, dial a phone number, read a message, and so on.

## Installation

### NuGet

Install extension from NuGet.

```
Install-Package Blazorise.QRCode
```

### Imports

In your main  add:

```
@using Blazorise.QRCode
```

## Examples

### Basic

To generate a QR code you only need to define a  parameter.

```
<QRCode Value="https://blazorise.com" Alt="QRCode image" />
```

### Color

Use the  and  attributes to modify the QR code's colors. You should always ensure good contrast for optimal compatibility with QR code scanners.

```
<QRCode Value="https://blazorise.com" Alt="QRCode image" DarkColor="#7474ed" />
```

### Error Correction

QR codes can be rendered with various levels of  that can be set using the  attribute. This example generates four codes with the same value using different error correction levels.

```
<QRCode Value="https://blazorise.com" Alt="QRCode image" EccLevel="EccLevel.L" PixelsPerModule="4" />
<QRCode Value="https://blazorise.com" Alt="QRCode image" EccLevel="EccLevel.M" PixelsPerModule="4" />
<QRCode Value="https://blazorise.com" Alt="QRCode image" EccLevel="EccLevel.Q" PixelsPerModule="4" />
<QRCode Value="https://blazorise.com" Alt="QRCode image" EccLevel="EccLevel.H" PixelsPerModule="4" />
```

### Custom Icon

Placing an icon in the middle of &lt;QRCode&gt; is very simple. You just need to set the Icon parameter. It can be in base64 format, or an absolute URL.

Please be aware that placing an icon in the middle will also cover part of the QR code and make it unreadable. So it would be best to increase the error level by setting the EccLevel parameter.

```
<QRCode Value="https://blazorise.com" Alt="QRCode image" EccLevel="EccLevel.H" Icon="@base64PngIcon" />
```

```
@code {
    string base64PngIcon = "data:image/png;base64, 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";
}
```

## Best Practices

### Set the Alt property

To optimize your web for SEO, define the Alt parameter to describe the QR image content, eg. Alt="QRCode image".

### Increase Error Correction Level for Images

Placing an image within the QRCode can make it unreadable, so it is best to increase the error level(EccLevel) of the code so that the QR scanners can easily read it.

## API

### Parameters

| Parameter          | Description                                                                                      | Type     | Default    |
|--------------------|--------------------------------------------------------------------------------------------------|----------|------------|
| Alt                | Image alt text.                                                                                  | string   |            |
| DarkColor          | Color used as dark color.                                                                        | string   | "#000000"  |
| DrawQuietZones     | Draw quiet zones (blank margins around QR Code image).                                           | bool     | true       |
| EccLevel           | The level of error correction to use.Possible values:L, M, Q, H                                  | EccLevel | EccLevel.L |
| Icon               | The icon that is places in the middle of the QRCode, can be in base64 format or an absolute url. | string   |            |
| IconBorderWidth    | Defines how large the borders will be for the icon that is placed within the QRCode.             | int      | 0          |
| IconSizePercentage | Defines how much space the icon will occupy within the QRCode.                                   | int      | 40         |
| LightColor         | Color used as light color.                                                                       | string   | "#ffffff"  |
| Payload            | Custom payload used for QR code generation.                                                      | Payload  | null       |
| PixelsPerModule    | Pixels per module.                                                                               | int      | 10         |
| Value              | Value used for QR code generation.                                                               | string   |            |

###### On this page

#### 

## 