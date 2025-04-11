# Enums: Common

A value type defined by a series of named constants of the underlying type.

We use enum type as a strongly typed options to

Take note of this caveat when using the following enums:

- DisplayType.None Does not render the html element at all in the page.
- Visibility.Default  Hides the element, but it still takes up space in the page. It is basically invisible.

### AddonType

Addon element type.

- AddonType.Body Main addon of a field.
- AddonType.Start Addon will placed at the start of a field.
- AddonType.End Addon will placed at the end of a field.

### Alignment

Defines the alignment of an element.

- Alignment.Default No alignment will be applied.
- Alignment.Start Aligns an element to the left.
- Alignment.Center Aligns an element on the center.
- Alignment.End Aligns an element to the right.

### Background

Predefined set of contextual background colors.

- Background.Default No color will be applied to an element.
- Background.Primary Primary color.
- Background.Secondary Secondary color.
- Background.Success Success color.
- Background.Danger Danger color.
- Background.Warning Warning color.
- Background.Info Info color.
- Background.Light Light color.
- Background.Dark Dark color.
- Background.White White color.
- Background.Transparent Transparent color.
- Background.Body Body color. Note that body color must be defined through the

### BarCollapseMode

Defines how the bar will be collapsed.

- BarCollapseMode.Hide Bar will be hidden completely when collapsed.
- BarCollapseMode.Small Bar will be collapsed into smaller version with icons.

### BarMode

Bar orientation and menu display.

- BarMode.Horizontal Horizontal navbar with dropdown menus.
- BarMode.VerticalPopout Vertical navbar with pop-out menus.
- BarMode.VerticalInline Vertical navbar with inline dropdown menus.
- BarMode.VerticalSmall Small vertical navbar with pop-out menus.

### BarTogglerMode

Defines the look and position of the bar toggler.

- BarTogglerMode.Normal The standard inline bar toggler. Supported by Horizontal and Vertical BarModes.
- BarTogglerMode.Popout A popout style bar toggler. Supported only on Vertical BarModes.

### BarMenuToggleBehavior

Defines how the bar menu will behave when toggled.

- BarMenuToggleBehavior.AllowSingleMenu Only a single menu will be toggled at a time.
- BarMenuToggleBehavior.AllowMultipleMenus Multiple menus can be toggled at a time.

### BorderColor

Predefined set of contextual border colors.

- BorderColor.None No color will be applied to an element.
- BorderColor.Primary Primary color.
- BorderColor.Secondary Secondary color.
- BorderColor.Success Success color.
- BorderColor.Danger Danger color.
- BorderColor.Warning Warning color.
- BorderColor.Info Info color.
- BorderColor.Light Light color.
- BorderColor.Dark Dark color.
- BorderColor.White White color.

### BorderRadius

Radius styles of an element.

- BorderRadius.Default Don't apply any borders.
- BorderRadius.Rounded Makes the element rounded on all sides.
- BorderRadius.RoundedTop Makes the element rounded on top side of the element.
- BorderRadius.RoundedRight Makes the element rounded on right side of the element.
- BorderRadius.RoundedBottom Makes the element rounded on bottom side of the element.
- BorderRadius.RoundedLeft Makes the element rounded on left side of the element.
- BorderRadius.RoundedCircle Makes the element as circle shaped.
- BorderRadius.RoundedPill Makes the element as pill shaped.
- BorderRadius.RoundedZero Makes the element without any round corners.

### BorderSide

Defines the border sides.

- BorderSide.All Shows the border on all sides of the element.
- BorderSide.Top Shows the border on top side of the element.
- BorderSide.Right Shows the border on right side of the element.
- BorderSide.Bottom Shows the border on bottom side of the element.
- BorderSide.Left Shows the border on left side of the element.

### BorderSize

Defines the border sizes.

- BorderSize.Default Border size will not be applied.
- BorderSize.Is0 Makes the element borderless.
- BorderSize.Is1 Borders will be 1px wide.
- BorderSize.Is2 Borders will be 2px wide.
- BorderSize.Is3 Borders will be 3px wide.
- BorderSize.Is4 Borders will be 4px wide.
- BorderSize.Is5 Borders will be 5px wide.

### BreadcrumbMode

Defines the breadcrumb activation mode.

- BreadcrumbMode.None No activation will be applied, meaning it must be applied manually by setting the
- BreadcrumbMode.Auto Breadcrumb items will be activated based on current navigation.

### Breakpoint

Defines the media breakpoint.

- Breakpoint.None Breakpoint is undefined.
- Breakpoint.Mobile Valid on all devices. (extra small)
- Breakpoint.Tablet Breakpoint on tablets (small).
- Breakpoint.Desktop Breakpoint on desktop (medium).
- Breakpoint.Widescreen Breakpoint on widescreen (large).
- Breakpoint.FullHD Breakpoint on large desktops (extra large).

### ButtonsRole

Buttons group behaviour.

- ButtonsRole.Addons Display buttons as addons.
- ButtonsRole.Toolbar Display buttons as toolbar buttons.

### ButtonType

Defines the button type and behaviour.

- ButtonType.Button The button is a clickable button.
- ButtonType.Submit The button is a submit button (submits form-data).
- ButtonType.Reset The button is a reset button (resets the form-data to its initial values).
- ButtonType.Link The button will be rendered as a link but will appear as a regular button.

### CarouselDirection

Defines the direction of carousel slides.

- CarouselDirection.Previous Slides will go in reverse, usually right-to-left.
- CarouselDirection.Next Slides will go forward, usually left-to-right.

### CharacterCasing

Specifies the case of characters in an element.

- CharacterCasing.Normal The case of characters is left unchanged.
- CharacterCasing.Upper Converts all characters to uppercase.
- CharacterCasing.Lower Converts all characters to lowercase.
- CharacterCasing.Title Convert first character to uppercase and all other to lowercase.

### CloseReason

Specifies the reason that a component was closed.

- CloseReason.None The cause of the closure was not defined or could not be determined.
- CloseReason.UserClosing The user is closing the component through the user interface.
- CloseReason.FocusLostClosing The component has lost focus or user has gone out of bounds.
- CloseReason.EscapeClosing Pressing the escape key is closing the component.

### Color

Predefined set of contextual colors.

- Color.Default No color will be applied to an element.
- Color.Primary Primary color.
- Color.Secondary Secondary color.
- Color.Success Success color.
- Color.Danger Danger color.
- Color.Warning Warning color.
- Color.Info Info color.
- Color.Light Light color.
- Color.Dark Dark color.
- Color.Link Link color.

### ColumnWidth

Defines number of columns to occupy in the grid.

- ColumnWidth.Default No sizing.
- ColumnWidth.Is1 One column width.
- ColumnWidth.Is2 Two columns width.
- ColumnWidth.Is3 Three columns width.
- ColumnWidth.Is4 Four columns width.
- ColumnWidth.Is5 Five columns width.
- ColumnWidth.Is6 Six columns width.
- ColumnWidth.Is7 Seven columns width.
- ColumnWidth.Is8 Eight columns width.
- ColumnWidth.Is9 Nine columns width.
- ColumnWidth.Is10 Ten columns width.
- ColumnWidth.Is11 Eleven columns width.
- ColumnWidth.Is12 Twelve columns width.
- ColumnWidth.Full Twelve columns width.
- ColumnWidth.Half Six columns width.
- ColumnWidth.Third Four columns width.
- ColumnWidth.Quarter Three columns width.
- ColumnWidth.Auto Fill all available space.

### ControlRole

Custom input roles.

- ControlRole.None Control doesn't have any special rule.
- ControlRole.Check Control is meant to be used with
- ControlRole.Radio Control is meant to be used with
- ControlRole.Switch Control is meant to be used with
- ControlRole.File Control is meant to be used with
- ControlRole.Text Control is meant to be used with

### CurrencySymbolPlacement

Placement of the currency sign, relative to the number shown (as a prefix or a suffix).

- CurrencySymbolPlacement.Prefix The symbol will be placed at the beginning of the number.
- CurrencySymbolPlacement.Suffix The symbol will be placed at the end of the number.

### Cursor

Defines the mouse cursor.

- Cursor.Default Default behaviour, nothing will be changed.
- Cursor.Pointer The cursor is a pointer and indicates a link.

### DateInputMode

Hints at the type of data that might be entered by the user while editing the

- DateInputMode.Date Only date is allowed to be entered.
- DateInputMode.DateTime Both date and time are allowed to be entered.
- DateInputMode.Month Allowed to select only year and month.

                Note that not all browser supports this mode, see

### DateInputSelectionMode

Defines the mode in which the dates can be selected.

- DateInputSelectionMode.Single Only one date can be selected.
- DateInputSelectionMode.Range Allowed to select a range of dates.
- DateInputSelectionMode.Multiple Allowed to select multiple dates.

### Direction

Direction of an dropdown menu.

- Direction.Default A default direction will be used, in most cases it is the same as Down.
- Direction.Down Trigger dropdown menus bellow an element (default behaviour).
- Direction.Up Trigger dropdown menus above an element.
- Direction.Right Trigger dropdown menus to the right of an element.
- Direction.Left Trigger dropdown menus to the left of an element.
- Direction.End Trigger dropdown menus to the end of an element.
- Direction.Start Trigger dropdown menus to the start of an element.

### DisplayDirection

Defines direction of flex items in a flex container.

- DisplayDirection.Default Direction will not be applied.
- DisplayDirection.Row The flex container's main-axis is defined to be the same as the text direction. The main-start and main-end points are the same as the content direction.
- DisplayDirection.Column The flex container's main-axis is the same as the block-axis. The main-start and main-end points are the same as the before and after points of the writing-mode.
- DisplayDirection.ReverseRow Behaves the same as row but the main-start and main-end points are permuted.
- DisplayDirection.ReverseColumn Behaves the same as column but the main-start and main-end are permuted.

### DisplayHeadingSize

Defines the display heading size.

- DisplayHeadingSize.Is1 Represents the h1 size element.
- DisplayHeadingSize.Is2 Represents the h2 size element.
- DisplayHeadingSize.Is3 Represents the h3 size element.
- DisplayHeadingSize.Is4 Represents the h4 size element.

### DisplayType

The display property specifies the display behavior (the type of rendering box) of an element.

- DisplayType.Always Display will not be applied, meaning an element will be visible.
- DisplayType.None Hides an element.
- DisplayType.Block Displays an element as a block element.
- DisplayType.Inline Displays an element as an inline element.
- DisplayType.InlineBlock Displays an element as an inline-level block container.
- DisplayType.Flex Displays an element as a block-level flex container.
- DisplayType.InlineFlex Displays an element as an inline-level flex container.
- DisplayType.Table Let the element behave like a table element.
- DisplayType.TableRow Let the element behave like a tr element.
- DisplayType.TableCell Let the element behave like a td element.

### DividerType

Specifies horizontal line style variants.

- DividerType.Solid Horizontal line will be solid.
- DividerType.Dashed Horizontal line will be dashed.
- DividerType.Dotted Horizontal line will be dotted.
- DividerType.TextContent Horizontal line be separated by text.

### FigureSize

Defines a figure size in pixels.

- FigureSize.Default No sizing will be applied.
- FigureSize.Is16x16 16x16px
- FigureSize.Is24x24 24x24px
- FigureSize.Is32x32 32x32px
- FigureSize.Is48x48 48x48px
- FigureSize.Is64x64 64x64px
- FigureSize.Is96x96 96x96px
- FigureSize.Is128x128 128x128px
- FigureSize.Is256x256 256x256px
- FigureSize.Is512x512 512x512px

### FileInvalidReason

Provides information about the invalid file.

- FileInvalidReason.None File is Valid.
- FileInvalidReason.MaxLengthExceeded File Max Lenght was exceeded.
- FileInvalidReason.UnexpectedBufferChunkLength The length of the buffer was not as expected when reading the file into the buffer.
- FileInvalidReason.TaskCancelled Task was cancelled.
- FileInvalidReason.UnexpectedError Unexpected error, please see exception.

### FlexAlignContent

The align-content property aligns a flex container’s lines within the
            flex container when there is extra space in the cross-axis.

- FlexAlignContent.Default Align-content will not be applied.
- FlexAlignContent.Start Lines are packed toward the start of the flex container.
- FlexAlignContent.End Lines are packed toward the end of the flex container.
- FlexAlignContent.Center Lines are packed toward the center of the flex container.
- FlexAlignContent.Between Lines are evenly distributed in the flex container.
- FlexAlignContent.Around Lines are evenly distributed in the flex container, with half-size spaces on either end.
- FlexAlignContent.Stretch Lines stretch to take up the remaining space.

### FlexAlignItems

Defines the default behavior for how flex items are laid out along the cross axis on the current line.

- FlexAlignItems.Default Align-items will not be applied.
- FlexAlignItems.Start Items are placed at the start of the cross axis. The difference between these is subtle,
                and is about respecting the flex-direction rules or the writing-mode rules.
- FlexAlignItems.End Items are placed at the end of the cross axis. The difference again is subtle and is about
                respecting flex-direction rules vs. writing-mode rules.
- FlexAlignItems.Center Items are centered in the cross-axis.
- FlexAlignItems.Baseline Items are aligned such as their baselines align.
- FlexAlignItems.Stretch Stretch to fill the container (still respect min-width/max-width).

### FlexAlignSelf

Allows the default alignment (or the one specified by align-items) to be overridden for individual flex items.

- FlexAlignSelf.Default Align-self will not be applied.
- FlexAlignSelf.Auto Equals to the value specified in the align-items property for the flex container (it’s the default value).
- FlexAlignSelf.Start Items are placed at the start of the cross axis. The difference between these is subtle,
                and is about respecting the flex-direction rules or the writing-mode rules.
- FlexAlignSelf.End Items are placed at the end of the cross axis. The difference again is subtle and is about
                respecting flex-direction rules vs. writing-mode rules.
- FlexAlignSelf.Center Items are centered in the cross-axis.
- FlexAlignSelf.Baseline Items are aligned such as their baselines align.
- FlexAlignSelf.Stretch Stretch to fill the container (still respect min-width/max-width).

### FlexDirection

Defines direction of flex items in a flex container.

- FlexDirection.Default Direction will not be applied.
- FlexDirection.Row The flex container's main-axis is defined to be the same as the text direction. The main-start and main-end points are the same as the content direction.
- FlexDirection.Column The flex container's main-axis is the same as the block-axis. The main-start and main-end points are the same as the before and after points of the writing-mode.
- FlexDirection.ReverseRow Behaves the same as row but the main-start and main-end points are permuted.
- FlexDirection.ReverseColumn Behaves the same as column but the main-start and main-end are permuted.

### FlexGrowShrink

The flex-grow property sets the flex grow factor to the provided

- FlexGrowShrink.Default No grow or shrink will be applied.
- FlexGrowShrink.Grow Grow rule will be applied.
- FlexGrowShrink.Shrink Shrink rule will be applied.

### FlexGrowShrinkSize

If all items have flex-grow set to 1, the remaining space in the container will be distributed equally to all children.

- FlexGrowShrinkSize.Default No size will be applied.
- FlexGrowShrinkSize.Is0 Element uses a default space.
- FlexGrowShrinkSize.Is1 Element uses all available space it can.

### FlexJustifyContent

Defines the alignment along the main axis.

- FlexJustifyContent.Default Justify-content will not be applied.
- FlexJustifyContent.Start Items are packed toward the start of the flex-direction.
- FlexJustifyContent.End Items are packed toward the end of the flex-direction.
- FlexJustifyContent.Center Items are centered along the line.
- FlexJustifyContent.Between Items are evenly distributed in the line; first item is on the start line, last item on the end line.
- FlexJustifyContent.Around Items are evenly distributed in the line with equal space around them.
                Note that visually the spaces aren't equal, since all the items have equal space on both sides.

### FlexOrder

Controls the order in which items appear in the flex container.

- FlexOrder.Default No order will be applied.
- FlexOrder.Is0 A default order.
- FlexOrder.Is1 An element will be shown as first item.
- FlexOrder.Is2 An element will be shown as second item.
- FlexOrder.Is3 An element will be shown as third item.
- FlexOrder.Is4 An element will be shown as fourth item.
- FlexOrder.Is5 An element will be shown as fifth item.
- FlexOrder.Is6 An element will be shown as sixth item.
- FlexOrder.Is7 An element will be shown as seventh item.
- FlexOrder.Is8 An element will be shown as eight item.
- FlexOrder.Is9 An element will be shown as ninth item.
- FlexOrder.Is10 An element will be shown as tenth item.
- FlexOrder.Is11 An element will be shown as eleventh item.
- FlexOrder.Is12 An element will be shown as twelveth item.

### FlexType

The flex types for the display property specifies the display behavior (the type of rendering box) of an element.

- FlexType.Default Display will not be defined.
- FlexType.Flex Displays an element as a block-level flex container.
- FlexType.InlineFlex Displays an element as an inline-level flex container.

### FlexWrap

Controls whether the flex container is single-line or multi-line.

- FlexWrap.Default No wrap will be applied.
- FlexWrap.Wrap Flex items will wrap onto multiple lines, from top to bottom.
- FlexWrap.ReverseWrap Flex items will wrap onto multiple lines from bottom to top.
- FlexWrap.NoWrap All flex items will be on one line.

### Float

Floats an element to the left or right, or disable floating.

- Float.Default Don't float on all viewport sizes.
- Float.Left Float left on all viewport sizes.
- Float.Right Float right on all viewport sizes.
- Float.Start Float start on all viewport sizes.
- Float.End Float end on all viewport sizes.

### HeadingSize

Defines the heading size.

- HeadingSize.Is1 Represents the h1 size element.
- HeadingSize.Is2 Represents the h2 size element.
- HeadingSize.Is3 Represents the h3 size element.
- HeadingSize.Is4 Represents the h4 size element.
- HeadingSize.Is5 Represents the h5 size element.
- HeadingSize.Is6 Represents the h6 size element.

### IconSize

Defines the size of an

- IconSize.Default The icon size will not be applied.
- IconSize.ExtraSmall The icon will be size 0.75em.
- IconSize.Small The icon will be size 0.875em.
- IconSize.Large The icon will be size 1.33em (Also applies vertical-align: -25%).
- IconSize.x2 The icon will be size 2em.
- IconSize.x3 The icon will be size 3em.
- IconSize.x4 The icon will be size 4em.
- IconSize.x5 The icon will be size 5em.
- IconSize.x6 The icon will be size 6em.
- IconSize.x7 The icon will be size 7em.
- IconSize.x8 The icon will be size 8em.
- IconSize.x9 The icon will be size 9em.
- IconSize.x10 The icon will be size 10em.

### IconStyle

Represents a different look of the same icons.

- IconStyle.Solid Icon will be filled with single-color.
- IconStyle.Regular Icon will be outlined with single-color.
- IconStyle.Light Icon will be slightly lighter.
- IconStyle.DuoTone Icon will be shown in two-color tones.

### InputMaskCaretPosition

Positioning of the caret on click.

- InputMaskCaretPosition.None Nothing will happen.
- InputMaskCaretPosition.LastValidPosition Based on the last valid position (default).
- InputMaskCaretPosition.RadixFocus Position caret to radixpoint on initial click.
- InputMaskCaretPosition.Select Select the whole input.
- InputMaskCaretPosition.Ignore Ignore the click and continue the mask.

### JumbotronTitleSize

Defines the jumbotron title size.

- JumbotronTitleSize.Is1 Represents the h1 size element.
- JumbotronTitleSize.Is2 Represents the h2 size element.
- JumbotronTitleSize.Is3 Represents the h3 size element.
- JumbotronTitleSize.Is4 Represents the h4 size element.

### JustifyContent

Aligns the flexible container's items when the items do not use all available space on the main-axis (horizontally).

- JustifyContent.Default Sets this property to its default value.
- JustifyContent.Start Items are positioned at the beginning of the container.
- JustifyContent.End Items are positioned at the end of the container.
- JustifyContent.Center Items are positioned at the center of the container.
- JustifyContent.Between Items are positioned with space between the lines.
- JustifyContent.Around Items are positioned with space before, between, and after the lines.

### LabelType

Defines the styling of a label for the component it belongs to.

- LabelType.None No additional styling is applied.
- LabelType.Check Style for check box will be applied.
- LabelType.Radio Style for radio will be applied.
- LabelType.Switch Style for switch will be applied.
- LabelType.File Style for file input will be applied.

### ListGroupMode

Defines the

- ListGroupMode.Static List group will act as a static list.
- ListGroupMode.Selectable List group will act on clicking the items.

### MaskType

Lists values that specify the type of mask used by an editor.

- MaskType.None Specifies that the mask feature is disabled.
- MaskType.Numeric Specifies that the editor should accept numeric values and that the mask string must use the Numeric format syntax.
- MaskType.DateTime Specifies that the editor should accept date/time values and that the mask string must use the DateTime format syntax.
- MaskType.RegEx Specifies that the mask should be created using full-functional regular expressions.

### Match

Modifies the URL matching behavior for a link.

- Match.Prefix Specifies that the link should be active when it matches any prefix
                of the current URL.
- Match.All Specifies that the link should be active when it matches the entire
                current URL.

### MessageType

Defines the possible UI message types with predefined actions.

- MessageType.Info Shows the simple info message.
- MessageType.Success Shows the success message.
- MessageType.Warning Shows the warning message.
- MessageType.Error Shows the error message.
- MessageType.Confirmation Prompt the user with the confirmation dialog.

### ModalRenderMode

Defines how the modal content will be rendered.

- ModalRenderMode.Default Always renders the modal html content to the DOM.
- ModalRenderMode.LazyLoad Lazy loads modal, meaning the modal html content will only be rendered/loaded the first time it is visited.
- ModalRenderMode.LazyReload Lazy loads modal everytime, meaning the modal html content will have it's html re-rendered to the DOM everytime.

### ModalSize

Changes the size of the modal.

- ModalSize.Default Default modal size.
- ModalSize.Small Small modal.
- ModalSize.Large Large modal.
- ModalSize.ExtraLarge Extra large modal.
- ModalSize.Fullscreen Defines the modal that covers the user viewport.

### MouseButton

Defines values that specify the buttons on a mouse device.

- MouseButton.Left The left mouse button.
- MouseButton.Middle The middle mouse button.
- MouseButton.Right The right mouse button.

### NotificationLocation

Defines the notification location.

- NotificationLocation.Center Default behavior, shows the notification on the center.
- NotificationLocation.Left Show the notification on the left side of the screen.
- NotificationLocation.Right Show the notification on the right side of the screen.

### NotificationType

Defines the possible UI notification types with predefined actions.

- NotificationType.Info Shows the simple info message.
- NotificationType.Success Shows the success message.
- NotificationType.Warning Shows the warning message.
- NotificationType.Error Shows the error message.

### NumericAllowDecimalPadding

Defines if the decimal places should be padded with zeroes.

- NumericAllowDecimalPadding.Always Always pad decimals with zeros (ie. '12.3400').
- NumericAllowDecimalPadding.Never Never pad with zeros (ie. '12.34').
- NumericAllowDecimalPadding.Floats Pad with zeroes only when there are decimals (ie. '12' and '12.3400').

### NumericRoundingMethod

Defines the rounding method to use.

- NumericRoundingMethod.HalfUpSymmetric Round-Half-Up Symmetric (default).
- NumericRoundingMethod.HalfUpAsymmetric Round-Half-Up Asymmetric.
- NumericRoundingMethod.HalfDownSymmetric Round-Half-Down Symmetric.
- NumericRoundingMethod.HalfDownAsymmetric Round-Half-Down Asymmetric.
- NumericRoundingMethod.HalfEvenBankersRounding Round-Half-Even "Bankers Rounding".
- NumericRoundingMethod.UpRoundAwayFromZero Round Up "Round-Away-From-Zero".
- NumericRoundingMethod.DownRoundTowardZero Round Down "Round-Toward-Zero" - same as truncate.
- NumericRoundingMethod.ToCeilingTowardPositiveInfinity Round to Ceiling "Toward Positive Infinity".
- NumericRoundingMethod.ToFloorTowardNegativeInfinity Round to Floor "Toward Negative Infinity".
- NumericRoundingMethod.ToNearest05 Rounds to the nearest .05 =&gt; same as
- NumericRoundingMethod.ToNearest05Alt Rounds up to next .05.
- NumericRoundingMethod.UpToNext05 Rounds up to next .05.
- NumericRoundingMethod.DownToNext05 Rounds down to next .05.

### OrderedListType

Defines the type of the list item marker.

- OrderedListType.Default The list items will be numbered with numbers (default).
- OrderedListType.LowerAlpha The list items will be numbered with lowercase letters.
- OrderedListType.LowerRoman The list items will be numbered with lowercase roman numbers.
- OrderedListType.UpperAlpha The list items will be numbered with uppercase letters.
- OrderedListType.UpperRoman The list items will be numbered with uppercase roman numbers.

### Orientation

Defines the orientation of the elements.

- Orientation.Horizontal Elements will be stacked horizontally.
- Orientation.Vertical Elements will be stacked vertically.

### OverflowType

The overflow property controls what happens to content that is too big to fit into an area.

- OverflowType.Default No overflow will be applied
- OverflowType.Visible The overflow is not clipped. The content renders outside the element's box.
- OverflowType.Hidden The overflow is clipped, and the rest of the content will be invisible.
- OverflowType.Scroll The overflow is clipped, and a scrollbar is added to see the rest of the content.
- OverflowType.Auto Similar to scroll, but it adds scrollbars only when necessary.

### Placement

Defines the placement of an element.

- Placement.Top Top side.
- Placement.Bottom Bottom side.
- Placement.Left Left side.
- Placement.Right Right side.
- Placement.Start Start side.
- Placement.End End side.

### PositionEdgeType

Defines the type of position edge type.

- PositionEdgeType.Default Edge type will not be applied.
- PositionEdgeType.Top For the vertical top position.
- PositionEdgeType.Start For the horizontal start position.
- PositionEdgeType.Bottom For the vertical bottom position.
- PositionEdgeType.End For the horizontal end position.

### PositionTranslateType

Defines the element translation based on its center.

- PositionTranslateType.None Translation will not be applied to an element.
- PositionTranslateType.Middle Translate on both X and Y coordinates.
- PositionTranslateType.MiddleX Translate on X coordinate.
- PositionTranslateType.MiddleY Translate on Y coordinate.

### PositionType

Type of positions allowed for the fluent position builder.

- PositionType.Default Position will not be applied to an element.
- PositionType.Static An element is not positioned in any special way; it is always positioned according to the normal flow of the page.
- PositionType.Relative An element is positioned relative to its normal position.
- PositionType.Absolute An element is positioned relative to the nearest positioned ancestor (instead of positioned relative to the
                viewport, like fixed).
- PositionType.Fixed An element is positioned relative to the viewport, which means it always stays in the
                same place even if the page is scrolled. The top, right, bottom, and left properties are used to position the element.
- PositionType.Sticky An element is positioned based on the user's scroll position.

### RowColumnsSize

Defines the number of columns to show in a row.

- RowColumnsSize.Default Nothing will be applied.
- RowColumnsSize.Are1 One column per row.
- RowColumnsSize.Are2 Two columns per row.
- RowColumnsSize.Are3 Three columns per row.
- RowColumnsSize.Are4 Four columns per row.
- RowColumnsSize.Are5 Five columns per row.
- RowColumnsSize.Are6 Six columns per row.

### Screenreader

Screen reader visibility.

- Screenreader.Always Default.
- Screenreader.Only Hide an element to all devices except screen readers.
- Screenreader.OnlyFocusable Show the element again when it’s focused.

### Shadow

Add or remove shadows to elements with box-shadow utilities.

- Shadow.None Shadow will not be applied.
- Shadow.Remove Disables any shadow on the element.
- Shadow.Default Regular shadow.
- Shadow.Small Small shadow.
- Shadow.Large Larger shadow.

### Side

Defines the side on which to apply the spacing.

- Side.None No side.
- Side.Top Top side.
- Side.Bottom Bottom side.
- Side.Left Left side.
- Side.Right Right side.
- Side.Start Start side.
- Side.End End side.
- Side.X Left and right side.
- Side.Y Top and bottom side.
- Side.All All 4 sides of the element.

### Size

Defines an element size.

- Size.Default Don't resize an element.
- Size.ExtraSmall Makes an element extra small size.
- Size.Small Makes an element small size.
- Size.Medium Makes an element medium size.
- Size.Large Makes an element large.
- Size.ExtraLarge Makes an element extra large.

### SizingSize

Predefined list of element sizes.

- SizingSize.Default No size will be defined.
- SizingSize.Is25 An element will occupy 25% of its parent space.
- SizingSize.Is50 An element will occupy 50% of its parent space.
- SizingSize.Is75 An element will occupy 75% of its parent space.
- SizingSize.Is100 An element will occupy 100% of its parent space.
- SizingSize.Auto The browser calculates the size.

### SizingType

Defines the sizing types.

- SizingType.None No sizing will be defined.
- SizingType.Width Sizing will be defined for the element width attribute(s).
- SizingType.Height Sizing will be defined for the element height attribute(s).

### SortDirection

Specifies the direction of a sort operation.

- SortDirection.Default No sorting will be applied.
- SortDirection.Ascending Sorts in ascending order.
- SortDirection.Descending Sorts in descending order.

### Spacing

Defines the spacing property.

- Spacing.None No spacing will be used.
- Spacing.Margin Use the margin spacing.
- Spacing.Padding Use the padding spacing.

### SpacingSize

Defines all supported spacing(margin and padding) sizes.

- SpacingSize.Is0 For classes that eliminate the margin or padding by setting it to 0.
- SpacingSize.Is1 (by default) for classes that set the margin or padding to $spacer * .25
- SpacingSize.Is2 (by default) for classes that set the margin or padding to $spacer * .5
- SpacingSize.Is3 (by default) for classes that set the margin or padding to $spacer
- SpacingSize.Is4 (by default) for classes that set the margin or padding to $spacer * 1.5
- SpacingSize.Is5 (by default) for classes that set the margin or padding to $spacer * 3
- SpacingSize.IsAuto For classes that set the margin to auto.

### TableResizeMode

Defines the resize mode of the Table's columns.

- TableResizeMode.Header The Table can only be resized from the columns header.
- TableResizeMode.Columns The Table can be resized from the entire column area.

### TabPosition

Defines the placement of a tab items.

- TabPosition.Top Top side.
- TabPosition.Bottom Bottom side.
- TabPosition.Left Left side.
- TabPosition.Right Right side.
- TabPosition.Start Start side.
- TabPosition.End End side.

### TabsRenderMode

Defines the Tabs Mode.

- TabsRenderMode.Default Always renders the tabs html content to the DOM.
- TabsRenderMode.LazyLoad Lazy loads tabs, meaning each tab will only be rendered/loaded the first time it is visited.
- TabsRenderMode.LazyReload Lazy loads tabs everytime, meaning only the active tab will have it's html rendered to the DOM.

### Target

The target attribute specifies where to open the linked document.

- Target.Default No target will be applied. Usually this is the same as
- Target.Self Opens the linked document in the same frame as it was clicked (this is default).
- Target.Blank Opens the linked document in a new window or tab.
- Target.Parent Opens the linked document in the parent frame.
- Target.Top Opens the linked document in the full body of the window.

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

- TextColor.Default No color will be applied to an element.
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

### ThemeContrast

Adjusts the theme contrast.

- ThemeContrast.None Undefined.
- ThemeContrast.Light Adjusts the theme for a light colors.
- ThemeContrast.Dark Adjusts the theme for a dark colors.

### TooltipPlacement

Defines the placement of an element.

- TooltipPlacement.Top Top-center side.
- TooltipPlacement.TopStart Top-left side.
- TooltipPlacement.TopEnd Top-right side.
- TooltipPlacement.Bottom Bottom-center side.
- TooltipPlacement.BottomStart Bottom-left side.
- TooltipPlacement.BottomEnd Bottom-right side.
- TooltipPlacement.Left Left-center side.
- TooltipPlacement.LeftStart Left-top side.
- TooltipPlacement.LeftEnd Left-bottom side.
- TooltipPlacement.Right Right-center side.
- TooltipPlacement.RightStart Right-top side.
- TooltipPlacement.RightEnd Right-bottom side.

### TooltipTrigger

Determines the events that cause the tooltip to show.

- TooltipTrigger.MouseEnterFocus Tooltip will show on mouse enter and focus event (default option).
- TooltipTrigger.Click Tooltip will show on click event only.
- TooltipTrigger.Focus Tooltip will show on focus event only.
- TooltipTrigger.MouseEnterClick Tooltip will show on mouse enter and click event.

### ValidationMode

Defines the validation execution mode.

- ValidationMode.Auto Validation will execute on every input change.
- ValidationMode.Manual Validation will run only when explicitly called.

### ValidationStatus

Defines the validation results.

- ValidationStatus.None No validation.
- ValidationStatus.Success Validation has passed the check.
- ValidationStatus.Error Validation has failed.

### VerticalAlignment

Used to change the vertical alignment of inline, inline-block, inline-table, and table cell elements.

- VerticalAlignment.Default Alignment will not be set.
- VerticalAlignment.Baseline Aligns the baseline of the element with the baseline of its parent.
- VerticalAlignment.Top Aligns the top of the element and its descendants with the top of the entire line.
- VerticalAlignment.Middle Centers the padding box of the cell within the row.
- VerticalAlignment.Bottom Aligns the bottom of the element and its descendants with the bottom of the entire line.
- VerticalAlignment.TextTop Aligns the top of the element with the top of the parent element's font.
- VerticalAlignment.TextBottom Aligns the bottom of the element with the bottom of the parent element's font.

### Visibility

Control the visibility, without modifying the display, of elements with visibility utilities.

- Visibility.Default No visibility will be applied to an element.
- Visibility.Visible Default value. The element is visible
- Visibility.Invisible The element is hidden (but still takes up space)

###### On this page

#### 

## 