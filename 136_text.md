# Enums: Text

### TextAlignment

Defines the text alignment.

- TextAlignment.Default No alignment will be applied.
- TextAlignment.Left Aligns the text to the left.
- TextAlignment.Right Aligns the text to the right.
- TextAlignment.Start Aligns the text to the start.
- TextAlignment.End Aligns the text to the end.
- TextAlignment.Center Centers the text.
- TextAlignment.Justified Stretches the lines so that each line has equal width.

### TextColor

Predefined set of contextual text colors.

- TextColor.None No color will be applied to an element.
- TextColor.Primary Primary color.
- TextColor.Secondary Secondary color.
- TextColor.Success Success color.
- TextColor.Danger Danger color.
- TextColor.Warning Warning color.
- TextColor.Info Info color.
- TextColor.Light Light color.
- TextColor.Dark Dark color.
- TextColor.Body Body color.
- TextColor.Muted Muted color.
- TextColor.White White color.
- TextColor.Black50 Black text with 50% opacity on white background.
- TextColor.White50 White text with 50% opacity on black background.

### TextInputMode

Specifies what kind of input mechanism would be most helpful for users entering content.

- TextInputMode.None The user agent should not display a virtual keyboard. This keyword is useful for content that renders its own keyboard control.
- TextInputMode.Text The user agent should display a virtual keyboard capable of text input in the user's locale.
- TextInputMode.Tel The user agent should display a virtual keyboard capable of telephone number input. This should including keys for the digits 0 to 9, the "#" character, and the "*" character. In some locales, this can also include alphabetic mnemonic labels (e.g., in the US, the key labeled "2" is historically also labeled with the letters A, B, and C).
- TextInputMode.Url The user agent should display a virtual keyboard capable of text input in the user's locale, with keys for aiding in the input of URLs, such as that for the "/" and "." characters and for quick input of strings commonly found in domain names such as "www." or ".com".
- TextInputMode.Email The user agent should display a virtual keyboard capable of text input in the user's locale, with keys for aiding in the input of e-mail addresses, such as that for the "@" character and the "." character.
- TextInputMode.Numeric The user agent should display a virtual keyboard capable of numeric input. This keyword is useful for PIN entry.
- TextInputMode.Decimal The user agent should display a virtual keyboard capable of fractional numeric input. Numeric keys and the format separator for the locale should be shown.
- TextInputMode.Search The user agent should display a virtual keyboard optimized for search.

### TextOverflow

Determines how the text will behave when it is larger than a parent container.

- TextOverflow.Default No overflow will be applied.
- TextOverflow.Wrap Text will wrap into a new line when it reaches the end of container.
- TextOverflow.NoWrap Prevents text from wrapping.
- TextOverflow.Truncate Truncate the text with an ellipsis.

### TextRole

Defines the behaviour of the text input.

- TextRole.Text Defines a default text input field.
- TextRole.Email Used for input fields that should contain an e-mail address.
- TextRole.Password Defines a password field.
- TextRole.Url Used for input fields that should contain a URL address.
- TextRole.Search Define a search field (like a site search, or Google search).
- TextRole.Telephone Define a field for entering a telephone number.

### TextTransform

Defines the text transformation.

- TextTransform.Default No capitalization. The text renders as it is. This is default.
- TextTransform.Lowercase Transforms all characters to lowercase.
- TextTransform.Uppercase Transforms all characters to uppercase.
- TextTransform.Capitalize Transforms the first character of each word to uppercase.

### TextWeight

Defines the text weight.

- TextWeight.Default No weight will be applied.
- TextWeight.Normal Defines normal characters. This is default.
- TextWeight.Bold Defines thick characters.
- TextWeight.Light Defines lighter characters.

### TextSize

Defines the font size.

- TextSize.Default No particular size rule will be applied, meaning a default size will be used..
- TextSize.ExtraSmall Makes an element text extra small size.
- TextSize.Small Makes an element text small size.
- TextSize.Medium Makes an element text medium size.
- TextSize.Large Makes an element text large.
- TextSize.ExtraLarge Makes an element text extra large.
- TextSize.Heading1 Matches the element text size with the h1 text size.
- TextSize.Heading2 Matches the element text size with the h2 text size.
- TextSize.Heading3 Matches the element text size with the h3 text size.
- TextSize.Heading4 Matches the element text size with the h4 text size.
- TextSize.Heading5 Matches the element text size with the h5 text size.
- TextSize.Heading6 Matches the element text size with the h6 text size.

### Screenreader

Screen reader visibility.

- Screenreader.Always Default.
- Screenreader.Only Hide an element to all devices except screen readers.
- Screenreader.OnlyFocusable Show the element again when it’s focused.

### MaskType

Lists values that specify the type of mask used by an editor.

- MaskType.None Specifies that the mask feature is disabled.
- MaskType.Numeric Specifies that the editor should accept numeric values and that the mask string must use the Numeric format syntax.
- MaskType.DateTime Specifies that the editor should accept date/time values and that the mask string must use the DateTime format syntax.
- MaskType.RegEx Specifies that the mask should be created using full-functional regular expressions.

###### On this page

#### 

## 