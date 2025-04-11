# Blazorise Markdown component

The Markdown component allows you to edit markdown strings.

The Blazorise Markdown is based on the Easy MarkDown Editor JavaScript library.

## Installation

### NuGet

Install extension from NuGet.

```
Install-Package Blazorise.Markdown
```

### Imports

In your main  add:

```
@using Blazorise.Markdown
```

### Example

```
<Markdown Value="@markdownValue" ValueChanged="@OnMarkdownValueChanged" />
```

```
@code{
    string markdownValue = "# EasyMDE \n Go ahead, play around with the editor! Be sure to check out **bold**, *italic*, [links](https://google.com) and all the other features. You can type the Markdown syntax, use the toolbar, or use shortcuts like `ctrl-b` or `cmd-b`.";

    string markdownHtml;

    protected override void OnInitialized()
    {
        markdownHtml = Markdig.Markdown.ToHtml( markdownValue ?? string.Empty );

        base.OnInitialized();
    }

    Task OnMarkdownValueChanged( string value )
    {
        markdownValue = value;

        markdownHtml = Markdig.Markdown.ToHtml( markdownValue ?? string.Empty );

        return Task.CompletedTask;
    }
}
```

For transforming markdown value into HTML we used an excellent  library.

### Toolbar customization

The editor's toolbar can be edited to show more icons and even add custom icons!

```
<Markdown @bind-Value="@markdownValue" CustomButtonClicked="@OnCustomButtonClicked">
    <Toolbar>
        <MarkdownToolbarButton Action="MarkdownAction.Bold" Icon="fa fa-bolt" Title="Bold" />
        <MarkdownToolbarButton Separator Name="Custom button" Value="@("hello")" Icon="fa fa-star" Title="A Custom Button" Text="My Custom Button" />
        <MarkdownToolbarButton Separator Name="https://github.com/Ionaru/easy-markdown-editor" Icon="fa fab fa-github" Title="A Custom Link" />
    </Toolbar>
</Markdown>
```

```
@code {
    [Inject] private INotificationService NotificationService { get; set; }

    string markdownValue = "## Custom Toolbar\nCustom functions, icons and buttons can be defined for the toolbar.";

    Task OnCustomButtonClicked( MarkdownButtonEventArgs eventArgs )
    {
        NotificationService.Info( $"Name: {eventArgs.Name} Value: {eventArgs.Value}" );

        return Task.CompletedTask;
    }
}
```

### Upload image

Uploading an image has a similar API to our  component and is fairly simple to use.

```
<Markdown ImageUploadChanged="@OnImageUploadChanged"
          ImageUploadStarted="@OnImageUploadStarted"
          ImageUploadProgressed="@OnImageUploadProgressed"
          ImageUploadEnded="@OnImageUploadEnded" />
```

```
@code {
    async Task OnImageUploadChanged( FileChangedEventArgs e )
    {
        try
        {
            foreach ( var file in e.Files )
            {
                using ( var stream = new System.IO.MemoryStream() )
                {
                    await file.WriteToStreamAsync( stream );

                    // do something with the stream
                }
            }
        }
        catch ( Exception exc )
        {
            Console.WriteLine( exc.Message );
        }
        finally
        {
            this.StateHasChanged();
        }
    }

    Task OnImageUploadStarted( FileStartedEventArgs e )
    {
        Console.WriteLine( $"Started Image: {e.File.Name}" );

        return Task.CompletedTask;
    }

    Task OnImageUploadProgressed( FileProgressedEventArgs e )
    {
        Console.WriteLine( $"Image: {e.File.Name} Progress: {(int)e.Percentage}" );

        return Task.CompletedTask;
    }

    Task OnImageUploadEnded( FileEndedEventArgs e )
    {
        // We need to report back to Markdown that upload is done. We do this by setting the UploadUrl.
        // NOTE: Since we're faking the upload in this demo we will just set some dummy UploadUrl.
        e.File.UploadUrl = "https://images.pexels.com/photos/4966601/pexels-photo-4966601.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=200";

        Console.WriteLine( $"Finished Image: {e.File.Name}, Success: {e.Success}" );

        return Task.CompletedTask;
    }
}
```

### Change Shortcuts

EasyMDE comes with an array of predefined keyboard shortcuts, but they can be altered with a configuration option.

```
<Markdown Shortcuts="@(new MarkdownShortcuts{ CleanBlock = null, ToggleCodeBlock = "Cmd-E" })" />
```

### Custom Preview Render

Sometimes you don't want to render preview with the built-in parser. In those situations you can make use of  callback to override the preview HTML.

```
<Markdown Value="@markdownValue" ValueChanged="@OnMarkdownValueChanged" PreviewRender="@PreviewRender" />
```

```
@code {
    string markdownValue = "# EasyMDE \n Go ahead, play around with the editor! Be sure to check out **bold**, *italic*, [links](https://google.com) and all the other features. You can type the Markdown syntax, use the toolbar, or use shortcuts like `ctrl-b` or `cmd-b`.";

    Task OnMarkdownValueChanged( string value )
    {
        markdownValue = value;

        return Task.CompletedTask;
    }

    protected Task<string> PreviewRender( string plainText )
    {
        return Task.FromResult( Markdig.Markdown.ToHtml( markdownValue ?? string.Empty ) );
    }
}
```

## API

### Parameters

| Parameter                   | Description                                                                                                                                                                                                                                                                                                                                                                                                                     | Type                    | Default                                |
|-----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------|----------------------------------------|
| AutoDownloadFontAwesome     | If set to true, force downloads Font Awesome (used for icons). If set to false, prevents downloading.                                                                                                                                                                                                                                                                                                                           | bool?                   | null                                   |
| Autofocus                   | If set to true, focuses the editor automatically. Defaults to false.                                                                                                                                                                                                                                                                                                                                                            | bool                    | false                                  |
| AutoRefresh                 | Useful, when initializing the editor in a hidden DOM node. If set to { delay: 300 },     it will check every 300 ms if the editor is visible and if positive, call CodeMirror's refresh().                                                                                                                                                                                                                                      | MarkdownAutoRefresh     | null                                   |
| Autosave                    | Saves the text that's being written and will load it back in the future.     It will forget the text when the form it's contained in is submitted.                                                                                                                                                                                                                                                                              | MarkdownAutosave        | null                                   |
| BlockStyles                 | Customize how certain buttons that style blocks of text behave.                                                                                                                                                                                                                                                                                                                                                                 | MarkdownBlockStyles     | null                                   |
| Direction                   | rtl or ltr. Changes text direction to support right-to-left languages. Defaults to ltr.                                                                                                                                                                                                                                                                                                                                         | string                  | "ltr"                                  |
| DisableProgressReport       | Gets or sets whether report progress should be disabled. By enabling this setting, ImageUploadProgressed and ImageUploadWritten callbacks won't be called. Internal file progress won't be tracked.     This setting can speed up file transfer considerably.                                                                                                                                                                   | bool                    | false                                  |
| ErrorMessages               | Errors displayed to the user, using the errorCallback option, where #image_name#, #image_size#     and #image_max_size# will replaced by their respective values, that can be used for customization     or internationalization.                                                                                                                                                                                               | MarkdownErrorMessages   | null                                   |
| ForceSync                   | If set to true, force text changes made in EasyMDE to be immediately stored in original text area.     Defaults to false.                                                                                                                                                                                                                                                                                                       | bool                    | false                                  |
| HideIcons                   | An array of icon names to hide. Can be used to hide specific icons shown by default without     completely customizing the toolbar.                                                                                                                                                                                                                                                                                             | string[]                | new[] { "side-by-side", "fullscreen" } |
| ImageAccept                 | A comma-separated list of mime-types used to check image type before upload (note: never trust client, always     check file types at server-side). Defaults to image/png, image/jpeg.                                                                                                                                                                                                                                          | string                  | "image/png, image/jpeg"                |
| ImageCSRFToken              | CSRF token to include with AJAX call to upload image. For instance used with Django backend.                                                                                                                                                                                                                                                                                                                                    | string                  |                                        |
| ImageMaxSize                | Maximum image size in bytes, checked before upload (note: never trust client, always check image     size at server-side). Defaults to 1024*1024*2 (2Mb).                                                                                                                                                                                                                                                                       | long                    | 1024 * 1024 * 2                        |
| ImagePathAbsolute           | If set to true, will treat imageUrl from imageUploadFunction and filePath returned from imageUploadEndpoint as     an absolute rather than relative path, i.e. not prepend window.location.origin to it.                                                                                                                                                                                                                        | string                  |                                        |
| ImageTexts                  | Texts displayed to the user (mainly on the status bar) for the import image feature, where     #image_name#, #image_size# and #image_max_size# will replaced by their respective values, that     can be used for customization or internationalization.                                                                                                                                                                        | MarkdownImageTexts      | null                                   |
| ImageUploadEndpoint         | The endpoint where the images data will be sent, via an asynchronous POST request. The server is supposed to     save this image, and return a json response.                                                                                                                                                                                                                                                                   | string                  |                                        |
| IndentWithTabs              | If set to false, indent using spaces instead of tabs. Defaults to true.                                                                                                                                                                                                                                                                                                                                                         | bool                    | true                                   |
| InputStyle                  | textarea or contenteditable.     Defaults to textarea for desktop and contenteditable for mobile.     contenteditable option is necessary to enable nativeSpellcheck.                                                                                                                                                                                                                                                           | string                  |                                        |
| InsertTexts                 | Customize how certain buttons that insert text behave. Takes an array with two elements.     The first element will be the text inserted before the cursor or highlight, and the second     element will be inserted after.     For example, this is the default link value: ["[", "](http://)"].                                                                                                                               | MarkdownInsertTexts     | null                                   |
| LineNumbers                 | If set to true, enables line numbers in the editor.                                                                                                                                                                                                                                                                                                                                                                             | bool                    | false                                  |
| LineWrapping                | If set to false, disable line wrapping. Defaults to true.                                                                                                                                                                                                                                                                                                                                                                       | bool                    | true                                   |
| MaxHeight                   | Sets fixed height for the composition area. minHeight option will be ignored.     Should be a string containing a valid CSS value like "500px". Defaults to undefined.                                                                                                                                                                                                                                                          | string                  |                                        |
| MaxUploadImageChunkSize     | Gets or sets the max chunk size when uploading the file.     Take note that if you're using Markdown.Markdown.OpenReadStream(FileEntry,CancellationToken) you're provided with a stream and should configure the chunk size when handling with the stream.Remarks https://docs.microsoft.com/en-us/aspnet/core/blazor/javascript-interoperability/call-dotnet-from-javascript?view=aspnetcore-6.0#stream-from-javascript-to-net | int                     | 20 * 1024                              |
| MinHeight                   | Sets the minimum height for the composition area, before it starts auto-growing.     Should be a string containing a valid CSS value like "500px". Defaults to "300px".                                                                                                                                                                                                                                                         | string                  | "300px"                                |
| NativeSpellcheck            | If set to false, disable native spell checker. Defaults to true.                                                                                                                                                                                                                                                                                                                                                                | bool                    | true                                   |
| ParsingConfig               | Adjust settings for parsing the Markdown during editing (not previewing).                                                                                                                                                                                                                                                                                                                                                       | MarkdownParsingConfig   | null                                   |
| Placeholder                 | If set, displays a custom placeholder message.                                                                                                                                                                                                                                                                                                                                                                                  | string                  |                                        |
| PreviewClass                | A space-separated strings that will be applied to the preview screen when activated.     Defaults to "editor-preview".                                                                                                                                                                                                                                                                                                          | string                  | "editor-preview"                       |
| PreviewImagesInEditor       | EasyMDE will show preview of images, false by default,     preview for images will appear only for images on separate lines.                                                                                                                                                                                                                                                                                                    | bool                    | false                                  |
| PromptTexts                 | Customize the text used to prompt for URLs.                                                                                                                                                                                                                                                                                                                                                                                     | MarkdownPromptTexts     | null                                   |
| PromptURLs                  | If set to true, a JS alert window appears asking for the link or image URL.     Defaults to false.                                                                                                                                                                                                                                                                                                                              | bool                    | false                                  |
| RenderingConfig             | Adjust settings for parsing the Markdown during previewing (not editing).                                                                                                                                                                                                                                                                                                                                                       | MarkdownRenderingConfig | null                                   |
| ScrollbarStyle              | Chooses a scrollbar implementation.     The default is "native", showing native scrollbars.          The core library also provides the "null" style, which completely hides the scrollbars.     Addons can implement additional scrollbar models.                                                                                                                                                                              | string                  | "native"                               |
| SegmentFetchTimeout         | Gets or sets the Segment Fetch Timeout when uploading the file.                                                                                                                                                                                                                                                                                                                                                                 | TimeSpan                | TimeSpan.FromMinutes( 1 )              |
| Shortcuts                   | Keyboard shortcuts associated with this instance.     Defaults to the array of shortcuts.                                                                                                                                                                                                                                                                                                                                       | MarkdownShortcuts       | null                                   |
| ShowIcons                   | An array of icon names to show. Can be used to show specific icons hidden by default without     completely customizing the toolbar.                                                                                                                                                                                                                                                                                            | string[]                | new[] { "code", "table" }              |
| SideBySideFullscreen        | If set to false, allows side-by-side editing without going into fullscreen. Defaults to false.                                                                                                                                                                                                                                                                                                                                  | bool                    | false                                  |
| SpellChecker                | If set to false, disable the spell checker. Defaults to true                                                                                                                                                                                                                                                                                                                                                                    | bool                    | true                                   |
| Status                      | If set to empty array, hide the status bar. Defaults to the array of built-in status bar items.     Optionally, you can set an array of status bar items to include, and in what order.                                                                                                                                                                                                                                         | string[]                | null                                   |
| StyleSelectedText           | If set to false, remove the CodeMirror-selectedtext class from selected lines. Defaults to true.                                                                                                                                                                                                                                                                                                                                | bool                    | true                                   |
| SyncSideBySidePreviewScroll | If set to false, disable syncing scroll in side by side mode. Defaults to true.                                                                                                                                                                                                                                                                                                                                                 | bool                    | true                                   |
| TabSize                     | If set, customize the tab size. Defaults to 2.                                                                                                                                                                                                                                                                                                                                                                                  | int                     | 2                                      |
| Theme                       | Override the theme. Defaults to easymde.                                                                                                                                                                                                                                                                                                                                                                                        | string                  | "easymde"                              |
| Toolbar                     | [Optional] Gets or sets the content of the toolbar.                                                                                                                                                                                                                                                                                                                                                                             | RenderFragment          | null                                   |
| ToolbarButtonClassPrefix    | Adds a prefix to the toolbar button classes when set. For example, a value of `"mde"` results in `"mde-bold"` for the Bold button.                                                                                                                                                                                                                                                                                              | string                  | "mde"                                  |
| ToolbarTips                 | If set to false, disable toolbar button tips. Defaults to true.                                                                                                                                                                                                                                                                                                                                                                 | bool                    | true                                   |
| UnorderedListStyle          | can be *, - or +. Defaults to *.                                                                                                                                                                                                                                                                                                                                                                                                | string                  | "*"                                    |
| UploadImage                 | If set to true, enables the image upload functionality, which can be triggered by drag-drop,     copy-paste and through the browse-file window (opened when the user click on the upload-image icon).     Defaults to true.                                                                                                                                                                                                     | bool                    | true                                   |
| Value                       | Gets or sets the markdown value.                                                                                                                                                                                                                                                                                                                                                                                                | string                  |                                        |

### Events

| Event                 | Description                                                                                                            | Type                                   |
|-----------------------|------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| CustomButtonClicked   | Occurs after the custom toolbar button is clicked.                                                                     | EventCallback<MarkdownButtonEventArgs> |
| ErrorCallback         | A callback function used to define how to display an error message. Defaults to (errorMessage) => alert(errorMessage). | Func<string, Task>                     |
| ImageUploadChanged    | Occurs every time the selected image has changed.                                                                      | Func<FileChangedEventArgs, Task>       |
| ImageUploadEnded      | Occurs when an individual image upload has ended.                                                                      | Func<FileEndedEventArgs, Task>         |
| ImageUploadProgressed | Notifies the progress of image being written to the destination stream.                                                | Func<FileProgressedEventArgs, Task>    |
| ImageUploadStarted    | Occurs when an individual image upload has started.                                                                    | Func<FileStartedEventArgs, Task>       |
| ImageUploadWritten    | Occurs every time the part of image has being written to the destination stream.                                       | Func<FileWrittenEventArgs, Task>       |
| PreviewRender         | Custom function for parsing the plaintext Markdown and returning HTML. Used when user previews.                        | Func<string, Task<string>>             |
| ValueChanged          | An event that occurs after the markdown value has changed.                                                             | EventCallback<string>                  |

### Methods

| Method                  | Description                                                                        | Return       | Parameters                                                              |
|-------------------------|------------------------------------------------------------------------------------|--------------|-------------------------------------------------------------------------|
| GetValueAsync           | Gets the markdown value.                                                           | Task<string> |                                                                         |
| SetValueAsync           | Sets the markdown value.                                                           | Task         | string value                                                            |
| UpdateInternalValue     | Updates the internal markdown value. This method should only be called internally! | Task         | string value                                                            |
| UpdateFileStartedAsync  | Notifies the component that file upload is about to start.                         | Task         | IFileEntry fileEntry                                                    |
| UpdateFileEndedAsync    | Notifies the component that file upload has ended.                                 | Task         | IFileEntry fileEntry, bool success, FileInvalidReason fileInvalidReason |
| UpdateFileWrittenAsync  | Updates component with the latest file data.                                       | Task         | IFileEntry fileEntry, long position, byte[] data                        |
| UpdateFileProgressAsync | Updated the component with the latest upload progress.                             | Task         | IFileEntry fileEntry, long progressProgress                             |
| WriteToStreamAsync      | Writes the file data to the target stream.                                         | Task         | FileEntry fileEntry, Stream stream, CancellationToken cancellationToken |
| OpenReadStream          | Opens the stream for reading the uploaded file.                                    | Stream       | FileEntry fileEntry, CancellationToken cancellationToken                |
| Focus                   | Sets the focus on the underline element.                                           | Task         | bool scrollToElement                                                    |

###### On this page

#### 

## 