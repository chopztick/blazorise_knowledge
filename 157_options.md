# Blazorise Theming Options API

Configuration settings for customizing the appearance and behavior of Blazorise components.

The Blazorise Theming Options API provides developers with a set of configuration settings to tailor the appearance and
    behavior of Blazorise components. By adjusting these options, you can define global styles, set default component properties,
    and manage theme-related settings to ensure a consistent and customized user interface across your Blazor applications.
    This flexibility allows for seamless integration of brand guidelines and personalized design preferences.

## API

### Parameters

#### ThemeAlertOptions

| Parameter               | Description                                                                                                                | Type   | Default   |
|-------------------------|----------------------------------------------------------------------------------------------------------------------------|--------|-----------|
| BackgroundLevel         | Defines a level of background color.Remarks Negative level values will lighten the color, while higher levels will darken. | int?   | -10       |
| BorderLevel             | Defines a level of border color.Remarks Negative level values will lighten the color, while higher levels will darken.     | int?   | -7        |
| ColorLevel              | Defines a level of text color.Remarks Negative level values will lighten the color, while higher levels will darken.       | int?   | 6         |
| GradientBlendPercentage | Defines the percentage of how much the colors will blend together.                                                         | float? | 15f       |

#### ThemeBackgroundOptions

| Parameter   | Description                                  | Type   | Default                        |
|-------------|----------------------------------------------|--------|--------------------------------|
| Body        | Gets or sets the background body color.      | string |                                |
| Danger      | Gets or sets the background danger color.    | string | ThemeColor.Shades["500"].Value |
| Dark        | Gets or sets the background dark color.      | string | ThemeColor.Shades["800"].Value |
| Info        | Gets or sets the background info color.      | string | ThemeColor.Shades["500"].Value |
| Light       | Gets or sets the background light color.     | string | ThemeColor.Shades["100"].Value |
| Muted       | Gets or sets the background muted color.     | string |                                |
| Primary     | Gets or sets the background primary color.   | string | ThemeColor.Shades["400"].Value |
| Secondary   | Gets or sets the background secondary color. | string | ThemeColor.Shades["600"].Value |
| Success     | Gets or sets the background success color.   | string | ThemeColor.Shades["500"].Value |
| Warning     | Gets or sets the background warning color.   | string | ThemeColor.Shades["500"].Value |

#### ThemeBarBrandColorOptions

| Parameter       | Description                              | Type   | Default   |
|-----------------|------------------------------------------|--------|-----------|
| BackgroundColor | Gets or sets the brand background color. | string |           |

#### ThemeBarColorOptions

| Parameter               | Description                                                                   | Type                         | Default   |
|-------------------------|-------------------------------------------------------------------------------|------------------------------|-----------|
| BackgroundColor         | Gets or sets the bar background color.                                        | string                       |           |
| BrandColorOptions       | Gets or sets the BarBrand color options.                                      | ThemeBarBrandColorOptions    | null      |
| Color                   | Gets or sets the bar text color.                                              | string                       |           |
| DropdownColorOptions    | Gets or sets the BarDropdown color options.                                   | ThemeBarDropdownColorOptions | null      |
| GradientBlendPercentage | Defines the percentage of how much the background colors will blend together. | float?                       | 15f       |
| ItemColorOptions        | Gets or sets the BarDropdownItem color options.                               | ThemeBarItemColorOptions     | null      |

#### ThemeBarDropdownColorOptions

| Parameter       | Description                        | Type   | Default   |
|-----------------|------------------------------------|--------|-----------|
| BackgroundColor | Gets or sets the background color. | string |           |

#### ThemeBarItemColorOptions

| Parameter             | Description                                                 | Type   | Default   |
|-----------------------|-------------------------------------------------------------|--------|-----------|
| ActiveBackgroundColor | Gets or sets the item background color when it is selected. | string |           |
| ActiveColor           | Gets or sets the item text color when it is selected.       | string |           |
| HoverBackgroundColor  | Gets or sets the item background color when it is hovered.  | string |           |
| HoverColor            | Gets or sets the item text color when it is hovered.        | string |           |

#### ThemeBarOptions

| Parameter               | Description                                                                                                 | Type                 | Default   |
|-------------------------|-------------------------------------------------------------------------------------------------------------|----------------------|-----------|
| DarkColors              | Gets or sets the theme settings for the Bar dark color scheme.                                              | ThemeBarColorOptions | null      |
| HorizontalHeight        | Gets or sets the height of the Bar in horizontal mode (only for Bar that is placed inside of LayoutHeader). | string               | "auto"    |
| LightColors             | Gets or sets the theme settings for the Bar light color scheme.                                             | ThemeBarColorOptions | null      |
| VerticalBrandHeight     | Gets or sets the size of the BarBrand component.                                                            | string               | "64px"    |
| VerticalPopoutMenuWidth | Gets or sets the width of the dropdown-menu in vertical mode.                                               | string               | "180px"   |
| VerticalSmallWidth      | Gets or sets the width of the Bar in vertical collapsed mode.                                               | string               | "64px"    |
| VerticalWidth           | Gets or sets the width of the Bar in vertical mode.                                                         | string               | "230px"   |

#### ThemeBasicOptions

| Parameter    | Description                                    | Type   | Default   |
|--------------|------------------------------------------------|--------|-----------|
| BorderRadius | Defines the size of the element border radius. | string | ".25rem"  |

#### ThemeBodyOptions

| Parameter       | Description                                                                                          | Type             | Default   |
|-----------------|------------------------------------------------------------------------------------------------------|------------------|-----------|
| BackgroundColor | Gets or sets the body background color.Remarks If defined it will also override any Background.Body. | string           |           |
| FontOptions     | Gets or sets the body font options.                                                                  | ThemeFontOptions | null      |
| TextColor       | Gets or sets the body text color.Remarks If defined it will also override any TextColor.Body.        | string           |           |

#### ThemeBreadcrumbOptions

| Parameter   | Description                             | Type   | Default                        |
|-------------|-----------------------------------------|--------|--------------------------------|
| Color       | Gets or sets the breadcrumb text color. | string | ThemeColor.Shades["400"].Value |

#### ThemeBreakpointOptions

| Parameter   | Description                                                               | Type   | Default   |
|-------------|---------------------------------------------------------------------------|--------|-----------|
| Desktop     | Gets or sets the breakpoint size for desktop screens. Defaults to 768px.  | string | "768px"   |
| FullHD      | Gets or sets the breakpoint size for largest screens. Defaults to 1200px. | string | "1200px"  |
| Mobile      | Gets or sets the breakpoint size for mobile screens. Defaults to 0px.     | string | "0"       |
| Tablet      | Gets or sets the breakpoint size for tablet screens. Defaults to 576px.   | string | "576px"   |
| Widescreen  | Gets or sets the breakpoint size for wide screens. Defaults to 992px.     | string | "992px"   |

#### ThemeButtonOptions

| Parameter               | Description                                                                   | Type   | Default   |
|-------------------------|-------------------------------------------------------------------------------|--------|-----------|
| ActiveDarkenColor       | Defines how much the color will darken when element is active(range 0-100).   | float? | 20f       |
| ActiveLightenColor      | Defines how much the color will lighten when element is active(range 0-100).  | float? | 25f       |
| BoxShadowSize           | Gets or sets the box shadow size of the button element.                       | string |           |
| BoxShadowTransparency   | Gets or sets the box shadow transparency of the button element(range 0-255)   | byte?  | 127       |
| DisabledOpacity         | Defined the opacity of disabled button(range 0-1).                            | float? | .65f      |
| GradientBlendPercentage | Defines the percentage of how much the colors will blend together.            | float? | 15f       |
| HoverDarkenColor        | Defines how much the color will darken when element is hovered(range 0-100).  | float? | 15f       |
| HoverLightenColor       | Defines how much the color will lighten when element is hovered(range 0-100). | float? | 20f       |
| LargeBorderRadius       | Defines the button border radius when it is Size.Large.                       | string | ".3rem"   |
| Margin                  | Gets or sets the margin for the button element.                               | string |           |
| Padding                 | Gets or sets the padding for the button element.                              | string |           |
| Size                    | Gets or sets the global size for button components.                           | Size?  | null      |
| SmallBorderRadius       | Defines the button border radius when it is Size.Small.                       | string | ".2rem"   |

#### ThemeCardOptions

| Parameter      | Description                                                            | Type   | Default              |
|----------------|------------------------------------------------------------------------|--------|----------------------|
| ImageTopRadius | Defines the top radius of the image element placed inside of the card. | string | "calc(.25rem - 1px)" |

#### ThemeColorOptions

| Parameter   | Description                             | Type   | Default                        |
|-------------|-----------------------------------------|--------|--------------------------------|
| Danger      | Gets or sets the danger theme color.    | string | ThemeColor.Shades["500"].Value |
| Dark        | Gets or sets the dark theme color.      | string | ThemeColor.Shades["800"].Value |
| Info        | Gets or sets the info theme color.      | string | ThemeColor.Shades["500"].Value |
| Light       | Gets or sets the light theme color.     | string | ThemeColor.Shades["100"].Value |
| Link        | Gets or sets the link theme color.      | string | ThemeColor.Shades["500"].Value |
| Primary     | Gets or sets the primary theme color.   | string | ThemeColor.Shades["500"].Value |
| Secondary   | Gets or sets the secondary theme color. | string | ThemeColor.Shades["600"].Value |
| Success     | Gets or sets the success theme color.   | string | ThemeColor.Shades["500"].Value |
| Warning     | Gets or sets the warning theme color.   | string | ThemeColor.Shades["500"].Value |

#### ThemeContainerMaxWidthOptions

| Parameter   | Description                                           | Type   | Default   |
|-------------|-------------------------------------------------------|--------|-----------|
| Desktop     | Gets or sets the breakpoint size for desktop screens. | string | "960px"   |
| FullHD      | Gets or sets the breakpoint size for largest screens. | string | "1320px"  |
| Mobile      | Gets or sets the breakpoint size for mobile screens.  | string | "540px"   |
| Tablet      | Gets or sets the breakpoint size for tablet screens.  | string | "720px"   |
| Widescreen  | Gets or sets the breakpoint size for wide screens.    | string | "1140px"  |

#### ThemeDropdownOptions

| Parameter               | Description                                                        | Type   | Default   |
|-------------------------|--------------------------------------------------------------------|--------|-----------|
| GradientBlendPercentage | Defines the percentage of how much the colors will blend together. | float? | 15f       |
| Size                    | Gets or sets the global size for dropdown components.              | Size?  | null      |
| ToggleIconVisible       | Defines the visibility of dropdown toggle icon.                    | bool?  | true      |

#### ThemeFontOptions

| Parameter   | Description                   | Type   | Default   |
|-------------|-------------------------------|--------|-----------|
| Family      | Gets or sets the font family. | string |           |
| Size        | Gets or sets the font size.   | string |           |
| Style       | Gets or sets the font style.  | string |           |
| Weight      | Gets or sets the font weight. | string |           |

#### ThemeInputOptions

| Parameter   | Description                                        | Type   | Default   |
|-------------|----------------------------------------------------|--------|-----------|
| CheckColor  | Gets or sets the checkbox color.                   | string |           |
| Color       | Gets or sets the input text color.                 | string |           |
| Size        | Gets or sets the global size for input components. | Size?  | null      |
| SliderColor | Gets or sets the slider text color.                | string |           |

#### ThemeListGroupItemOptions

| Parameter               | Description                                                                                                                | Type   | Default   |
|-------------------------|----------------------------------------------------------------------------------------------------------------------------|--------|-----------|
| BackgroundLevel         | Defines a level of background color.Remarks Negative level values will lighten the color, while higher levels will darken. | int?   | -9        |
| ColorLevel              | Defines a level of text color.Remarks Negative level values will lighten the color, while higher levels will darken.       | int?   | 6         |
| GradientBlendPercentage | Defines the percentage of how much the colors will blend together.                                                         | float? | 15f       |

#### ThemePaginationOptions

| Parameter         | Description                                             | Type   | Default   |
|-------------------|---------------------------------------------------------|--------|-----------|
| LargeBorderRadius | Gets or sets the border radius of the large pagination. | string | ".3rem"   |
| Size              | Gets or sets the global size for pagination components. | Size?  | null      |

#### ThemeProgressOptions

| Parameter                | Description                                           | Type   | Default   |
|--------------------------|-------------------------------------------------------|--------|-----------|
| PageProgressDefaultColor | Default color of the progress bar.                    | string | "#ffffff" |
| Size                     | Gets or sets the global size for progress components. | Size?  | null      |

#### ThemeRatingOptions

| Parameter    | Description                                                          | Type   | Default   |
|--------------|----------------------------------------------------------------------|--------|-----------|
| HoverOpacity | Gets or sets the mouse hover opacity for the rating item(range 0-1). | float? | 0.7f      |

#### ThemeSidebarOptions

| Parameter       | Description                                       | Type   | Default   |
|-----------------|---------------------------------------------------|--------|-----------|
| BackgroundColor | Gets or sets the background color of the sidebar. | string | "#343a40" |
| Color           | Gets or sets the text color of the sidebar items. | string | "#ced4da" |
| Width           | Gets or sets the width of the sidebar.            | string | "230px"   |

#### ThemeSnackbarOptions

| Parameter                   | Description                                                                                                                | Type   | Default   |
|-----------------------------|----------------------------------------------------------------------------------------------------------------------------|--------|-----------|
| BackgroundColor             | Default snackbar color.                                                                                                    | string |           |
| ButtonColor                 | Default button color.                                                                                                      | string |           |
| ButtonHoverColor            | Default button hover color.                                                                                                | string |           |
| TextColor                   | Default text color.                                                                                                        | string |           |
| VariantBackgroundColorLevel | Defines a level of background color.Remarks Negative level values will lighten the color, while higher levels will darken. | int?   | -3        |

#### ThemeSpacingOptions

| Parameter   | Description                                         | Type   | Default   |
|-------------|-----------------------------------------------------|--------|-----------|
| Is0         | Gets or sets the zero spacing size.                 | string | "0"       |
| Is1         | Gets or sets the spacing for the extra small sizes. | string | "0.25rem" |
| Is2         | Gets or sets the spacing for the small sizes.       | string | "0.5rem"  |
| Is3         | Gets or sets the spacing for the default sizes.     | string | "1rem"    |
| Is4         | Gets or sets the spacing for the large sizes.       | string | "1.5rem"  |
| Is5         | Gets or sets the spacing for the extra large sizes. | string | "3rem"    |

#### ThemeSpinKitOptions

| Parameter   | Description    | Type   | Default   |
|-------------|----------------|--------|-----------|
| Color       | SpinKit color. | string |           |
| Size        | SpinKit size.  | string |           |

#### ThemeStepsOptions

| Parameter                 | Description                                                    | Type   | Default   |
|---------------------------|----------------------------------------------------------------|--------|-----------|
| StepsItemIconActive       | Gets or sets the Step icon color for active state.             | string | "#007bff" |
| StepsItemIconActiveYiq    | Gets or sets the Step icon contrast color for active state.    | string | "#ffffff" |
| StepsItemIconColor        | Gets or sets the Step icon color.                              | string | "#adb5bd" |
| StepsItemIconCompleted    | Gets or sets the Step icon color for completed state.          | string | "#007bff" |
| StepsItemIconCompletedYiq | Gets or sets the Step icon contrast color for completed state. | string | "#ffffff" |
| StepsItemTextActive       | Gets or sets the Step text color for active state.             | string | "#28a745" |
| StepsItemTextColor        | Gets or sets the Step text color.                              | string | "#adb5bd" |
| StepsItemTextCompleted    | Gets or sets the Step text color for completed state.          | string | "#28a745" |

#### ThemeSwitchOptions

| Parameter             | Description                                                                | Type   |   Default |
|-----------------------|----------------------------------------------------------------------------|--------|-----------|
| BoxShadowLightenColor | Gets or sets how much the switch box-shadow will lighten(range 0-100).     | float? |        25 |
| DisabledLightenColor  | Gets or sets how much the switch disabled color will lighten(range 0-100). | float? |        50 |

#### ThemeTableOptions

| Parameter       | Description                                                                                                                | Type   |   Default |
|-----------------|----------------------------------------------------------------------------------------------------------------------------|--------|-----------|
| BackgroundLevel | Defines a level of background color.Remarks Negative level values will lighten the color, while higher levels will darken. | int?   |        -9 |
| BorderLevel     | Defines a level of border color.Remarks Negative level values will lighten the color, while higher levels will darken.     | int?   |        -6 |

#### ThemeTextColorOptions

| Parameter   | Description                            | Type   | Default                        |
|-------------|----------------------------------------|--------|--------------------------------|
| Black50     | Gets or sets the text black-50% color. | string | "#000000"                      |
| Body        | Gets or sets the text body color.      | string | ThemeColor.Shades["900"].Value |
| Danger      | Gets or sets the text danger color.    | string | ThemeColor.Shades["500"].Value |
| Dark        | Gets or sets the text dark color.      | string | ThemeColor.Shades["800"].Value |
| Info        | Gets or sets the text info color.      | string | ThemeColor.Shades["500"].Value |
| Light       | Gets or sets the text light color.     | string | ThemeColor.Shades["100"].Value |
| Muted       | Gets or sets the text muted color.     | string | ThemeColor.Shades["600"].Value |
| Primary     | Gets or sets the text primary color.   | string | ThemeColor.Shades["400"].Value |
| Secondary   | Gets or sets the text secondary color. | string | ThemeColor.Shades["600"].Value |
| Success     | Gets or sets the text success color.   | string | ThemeColor.Shades["500"].Value |
| Warning     | Gets or sets the text warning color.   | string | ThemeColor.Shades["500"].Value |
| White       | Gets or sets the text white color.     | string | ThemeColor.Shades["50"].Value  |
| White50     | Gets or sets the text white-50% color. | string | "#FFFFFF"                      |

#### ThemeTooltipOptions

| Parameter       | Description                                                                 | Type   | Default      |
|-----------------|-----------------------------------------------------------------------------|--------|--------------|
| BackgroundColor | Tooltip background color. Can contain alpha value in 8-hex formatted color. | string | "#808080e6"  |
| Color           | Tooltip text color. Can contain alpha value in 8-hex formatted color.       | string | "#ffffff"    |
| FadeTime        | Gets or sets the duration of the tooltip fade animation.                    | string | "0.3s"       |
| FontSize        | Gets or sets the tooltip font-size.                                         | string | ".875rem"    |
| MaxWidth        | Gets or sets the maximum width of the tooltip.                              | string | "15rem"      |
| Padding         | Gets or sets the padding of the tooltip container.                          | string | ".5rem 1rem" |
| ZIndex          | Gets or sets the tooltip z-index.                                           | string | "1020"       |

#### ThemeVariables

| Parameter                 | Description                                                                     | Type   | Default   |
|---------------------------|---------------------------------------------------------------------------------|--------|-----------|
| SpinKitColor              | CSS variable for defining the color of the SpinKit loader.                      | string |           |
| SpinKitSize               | CSS variable for defining the size of the SpinKit loader.                       | string |           |
| StepsItemIcon             | CSS variable for defining the icon color of a StepsItem component.              | string |           |
| StepsItemIconActive       | CSS variable for defining the icon color of an active StepsItem.                | string |           |
| StepsItemIconActiveYiq    | CSS variable for defining the YIQ contrast color of an active StepsItem icon.   | string |           |
| StepsItemIconCompleted    | CSS variable for defining the icon color of a completed StepsItem.              | string |           |
| StepsItemIconCompletedYiq | CSS variable for defining the YIQ contrast color of a completed StepsItem icon. | string |           |
| StepsItemText             | CSS variable for defining the text color of a StepsItem.                        | string |           |
| StepsItemTextActive       | CSS variable for defining the text color of an active StepsItem.                | string |           |
| StepsItemTextCompleted    | CSS variable for defining the text color of a completed StepsItem.              | string |           |

### Events

#### ThemeBackgroundOptions

| Event   | Description                                                     | Type         |
|---------|-----------------------------------------------------------------|--------------|
| this[]  | Gets the color handler associated with the specified color key. | Func<string> |

#### ThemeBreakpointOptions

| Event   | Description                                                               | Type         |
|---------|---------------------------------------------------------------------------|--------------|
| this[]  | Gets the breakpoint handler associated with the specified breakpoint key. | Func<string> |

#### ThemeColorOptions

| Event   | Description                                                     | Type         |
|---------|-----------------------------------------------------------------|--------------|
| this[]  | Gets the color handler associated with the specified color key. | Func<string> |

#### ThemeContainerMaxWidthOptions

| Event   | Description                                                               | Type         |
|---------|---------------------------------------------------------------------------|--------------|
| this[]  | Gets the breakpoint handler associated with the specified breakpoint key. | Func<string> |

#### ThemeSpacingOptions

| Event   | Description                                         | Type         |
|---------|-----------------------------------------------------|--------------|
| this[]  | Gets the spacing associated with the specified key. | Func<string> |

#### ThemeTextColorOptions

| Event   | Description                                                     | Type         |
|---------|-----------------------------------------------------------------|--------------|
| this[]  | Gets the color handler associated with the specified color key. | Func<string> |

### Methods

#### ThemeBasicOptions

| Method     | Description                                             | Return   | Parameters   |
|------------|---------------------------------------------------------|----------|--------------|
| HasOptions | Checks if the options has any option attribute defined. | bool     |              |

#### ThemeVariables

| Method                       | Description                                                                                                                                                     | Return   | Parameters     |
|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|----------------|
| Color                        | Gets the theme color variable name.                                                                                                                             | string   | string variant |
| BackgroundColor              | Gets the theme background color variable name.                                                                                                                  | string   | string variant |
| BackgroundYiqColor           | Gets the theme background contrast variable name.                                                                                                               | string   | string variant |
| TextColor                    | Gets the theme text color variable name.                                                                                                                        | string   | string variant |
| Breakpoint                   | Gets the breakpoint variable name.                                                                                                                              | string   | string name    |
| ButtonBackground             | Generates the CSS variable for the background color of a button with the specified variant.                                                                     | string   | string variant |
| ButtonBorder                 | Generates the CSS variable for the border color of a button with the specified variant.                                                                         | string   | string variant |
| ButtonHoverBackground        | Generates the CSS variable for the background color of a button when hovered.                                                                                   | string   | string variant |
| ButtonHoverBorder            | Generates the CSS variable for the border color of a button when hovered.                                                                                       | string   | string variant |
| ButtonActiveBackground       | Generates the CSS variable for the background color of a button when active (clicked).                                                                          | string   | string variant |
| ButtonActiveBorder           | Generates the CSS variable for the border color of a button when active (clicked).                                                                              | string   | string variant |
| ButtonYiqBackground          | Generates the CSS variable for the YIQ contrast background color of a button.     YIQ is used to determine text visibility on different backgrounds.            | string   | string variant |
| ButtonYiqHoverBackground     | Generates the CSS variable for the YIQ contrast background color of a button when hovered.                                                                      | string   | string variant |
| ButtonYiqActiveBackground    | Generates the CSS variable for the YIQ contrast background color of a button when active.                                                                       | string   | string variant |
| ButtonBoxShadow              | Generates the CSS variable for the box shadow of a button.                                                                                                      | string   | string variant |
| OutlineButtonColor           | Generates the CSS variable for the text color of an outlined button.                                                                                            | string   | string variant |
| OutlineButtonYiqColor        | Generates the CSS variable for the YIQ contrast color of an outlined button.     YIQ is used to ensure text visibility on different background colors.          | string   | string variant |
| OutlineButtonBoxShadowColor  | Generates the CSS variable for the box shadow color of an outlined button.                                                                                      | string   | string variant |
| OutlineButtonHoverColor      | Generates the CSS variable for the text color of an outlined button when hovered.                                                                               | string   | string variant |
| OutlineButtonActiveColor     | Generates the CSS variable for the text color of an outlined button when active (clicked).                                                                      | string   | string variant |
| VariantStepsItemIcon         | Generates the CSS variable for the icon color of a StepsItem component with the specified variant.                                                              | string   | string variant |
| VariantStepsItemIconYiq      | Generates the CSS variable for the YIQ contrast color of a StepsItem icon with the specified variant.     YIQ is used to adjust contrast for better visibility. | string   | string variant |
| VariantStepsItemText         | Generates the CSS variable for the text color of a StepsItem component with the specified variant.                                                              | string   | string variant |
| VariantPageProgressIndicator | Generates the CSS variable for the color of the page progress indicator with the specified variant.                                                             | string   | string variant |
| VariantRatingColor           | Generates the CSS variable for the color of the rating component with the specified variant.                                                                    | string   | string variant |

###### On this page

#### 

## 