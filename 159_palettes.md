# Blazorise Palettes API

Classes for defining and managing color palettes in Blazorise.

The Blazorise Palettes API provides an overview of how Blazorise allows developers to define and manage color palettes within their applications. By utilizing the Palettes API, users can create customized themes with structured color configurations, ensuring consistency across components. This enables dynamic theming and easy adaptation of styles to match branding requirements or user preferences.

## API

### Parameters

#### ThemeSwatch

| Parameter       | Description                                     | Type   | Default   |
|-----------------|-------------------------------------------------|--------|-----------|
| HexColor        | Gets the swatch color in hex format.            | string |           |
| Hue             | Gets the swatch hls-color hue component.        | double | 0         |
| HueScale        | Gets the swatch hls-color hue scale.            | double | 0         |
| Key             | Gets the swatch key.                            | double | 0         |
| Lightness       | Gets the swatch hls-color lightness component.  | double | 0         |
| Saturation      | Gets the swatch hls-color saturation component. | double | 0         |
| SaturationScale | Gets the swatch hls-color saturation scale.     | double | 0         |

#### ThemeSwatchOptions

| Parameter    | Description                                                                          | Type    | Default   |
|--------------|--------------------------------------------------------------------------------------|---------|-----------|
| HexColor     | Gets or sets the color in HEX format.                                                | string  |           |
| Hue          | Gets or sets the palete Hue component.                                               | double? | null      |
| LightnessMax | Lightness/Luminance Distribution 0-100.                                              | double? | null      |
| LightnessMin | Gets or sets the Lightness/Luminance Distribution 0-100.                             | double? | null      |
| Saturation   | Gets or sets the palete Saturation component.                                        | double? | null      |
| UseLightness | Set to true if you want to calculate colors based on lightness instead of luminance. | bool?   | null      |

###### On this page

#### 

## 