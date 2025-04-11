# Localization

### Overview

Localization within Blazorise can be done in multiple ways:

- By using ITextLocalizer and ITextLocalizerService.
- By using custom localizer handler(s) TextLocalizerHandler

List of predefined language that comes with Blazorise is:

- da Danish
- de German
- en English
- es Spanish
- fr French
- hr Croatian
- is Icelandic
- it Italian
- nl Dutch
- pl Polish
- pt Portuguese
- ru Russian
- sk Slovakian
- tr Turkish
- zh Chinese

In this guide we will explain both ways.

If not specified, a default language(or culture) will be .

### ITextLocalizerService

When using , by default the  changes the default thread culture, this means it will be an application wide change.
                If you want to change the language for a specific user, you need to use  instead.

```
@using System.Globalization

<Field>
    <FileEdit />
</Field>
<Field>
    <Addons>
        <Addon AddonType="AddonType.Start">
            <SelectList TItem="CultureInfo"
                        TValue="string"
                        Data="@LocalizationService.AvailableCultures"
                        TextField="@((item)=>item.IsNeutralCulture ? item.EnglishName : item.Parent.EnglishName)"
                        ValueField="@((item)=>item.Name)"
                        @bind-SelectedValue="selectedCulture"
                        DefaultItemText="Choose your culture" />
        </Addon>
        <Addon AddonType="AddonType.Body">
            <Button Clicked="OnButtonClick">Change culture</Button>
        </Addon>
    </Addons>
</Field>
```

```
@code{
    [Inject]
    Blazorise.Localization.ITextLocalizerService LocalizationService { get; set; }

    private string selectedCulture;

    Task OnButtonClick()
    {
        if ( string.IsNullOrWhiteSpace( selectedCulture ) )
            return Task.CompletedTask;

        return SelectCulture( selectedCulture );
    }

    Task SelectCulture( string name )
    {
        LocalizationService.ChangeLanguage( name, false );

        return Task.CompletedTask;
    }
}
```

### TextLocalizerHandler

TextLocalizerHandler handler is used to control the localization for each component individually. Once used it will override any localizations done by the ITextLocalizer or ITextLocalizerService.

While this is the good approach to handle localization, it is not very flexible since you need to do it on every component. But, for a quick override it is fairly easy. Just need to remember that.

```
<Field>
    <FileEdit BrowseButtonLocalizer="@((name, arguments)=>" My custom browse button")" />
</Field>
```

### Custom languages

While Blazorise will have all standard languages built-in it cannot have every one out there. So, if you want to have your own language injected into the component you can add it with  method, found on .

```
<Field>
    <FileEdit Multiple="false" />
    <FileEdit Multiple />
</Field>
<Field>
    <Button Clicked="OnButtonClick">Change culture to polish</Button>
</Field>
```

```
@code{
    [Inject]
    Blazorise.Localization.ITextLocalizerService LocalizationService { get; set; }

    // By using FileEdit as generic typeparam, Blazorise will know
    // what component need to update localization resources.
    [Inject]
    Blazorise.Localization.ITextLocalizer<FileEdit> FileEditLocalizer { get; set; }

    protected override Task OnInitializedAsync()
    {
        FileEditLocalizer.AddLanguageResource( new Blazorise.Localization.TextLocalizationResource
        {
            Culture = "pl-PL",
            Translations = new Dictionary<string, string>()
{
            { "Choose file", "Wybierz plik" },
            { "Choose files", "Wybierz pliki" },
        }
        } );

        return base.OnInitializedAsync();
    }

    Task OnButtonClick()
    {
        return SelectCulture( "pl-PL" );
    }

    Task SelectCulture( string name )
    {
        LocalizationService.ChangeLanguage( name, false );

        return Task.CompletedTask;
    }
}
```

### Global localization

To control the localization from a single place on an application level, you can use the  found in the . The  will provide you with two parameters, a  and an optional  that you can use to format the message if needed.

```
services
    .AddBlazorise( options =>
    {
        // other settings

        options.ValidationMessageLocalizer = ( message, arguments ) =>
        {
            return string.Format( applicationLocalizerDictionary[message], arguments );
        };
    } );
```

###### On this page

#### 

## 