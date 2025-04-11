# Blazorise Specifications: Autocomplete

Learn how the Autocomplete works and behaves under the certain scenarios, according to the defined parameters

## AutoSelectFirstItem

When active, the Autocomplete will attempt to select the first option upon initializing. This will trigger the change events.
    This is specially usefull when you've specified ReadData.

This option is only available when the Autocomplete is in AutocompleteSelectionMode.Default.

## AutoPreSelect

When disabled, the first option in the Autocomplete suggestion's box will no longer be "PreSelected".

This is specially useful for a corner case.
    If you would like your User to input a Free typed value (by using FreeTyping) you might want to consider disabling this option.
    In this manner, your User may Enter a similar value to the one's suggested by the Autocomplete, however this will make it so the confirmation Key does not Select the "PreSelected" option.

Please note the following simple example, where we would like a user to be able to commit a value of 10000 as their Employee Id, even tough there are suggestions based on that same number.

## CloseOnSelection

By default Autocomplete will close the suggestion's box upon the value being confirmed.
    However you might want it to remain open, this is specially usefull if you have the Autocomplete set to AutocompleteSelectionMode.Multiple or AutocompleteSelectionMode.Checkbox
    Here's an example:

## MinLength

This Parameter is quite self descriptive, it'll start displaying eligibile options from a defined minimum length, it defaults to the value of 1.

A recurring question, is how to display every Autocomplete option upon focus.
    Setting this Parameter  to the value of 0 is how you do it.

## Changed Triggers

Sometimes it's important to know when to expect a Parameter Changed EventCallback will trigger.
    The following table displays some common combinations which we find important for you to know.

| SelectedValueChanged   | FreeTyping   | No FreeTyping   | AutoSelectFirstItem          |
|------------------------|--------------|-----------------|------------------------------|
| Component Initialized  |              |                 | Triggers If Multiple="false" |
| User Input             | If SelectedValue has been found.                                               If SelectedValue has not been found. (If the current SelectedValue is not already default (null))              | If SelectedValue has been found.                                               If SelectedValue has not been found. (If the current SelectedValue is not already default (null))                 |                              |

| SelectedTextChanged   | FreeTyping      | No FreeTyping   | AutoSelectFirstItem          |
|-----------------------|-----------------|-----------------|------------------------------|
| Component Initialized |                 |                 | Triggers If Multiple="false" |
| User Input            | Triggers Always | If SelectedText has been found.                                               If SelectedText has not been found. (If the current SelectedText is not already default (null))                 |                              |

###### On this page

#### 

## 