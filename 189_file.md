# Blazorise FileEdit component

The FileEdit component is a specialized input that provides a clean interface for selecting files.

Customized, cross-browser consistent, file input control that supports single file and multiple files upload.

## Examples

### Single file (default)

On single file mode, when file is selected or user does not cancel Browse dialog,  event will be raised.
        The return value will be a  that will contain only one item in the  property.

```
<Field>
    <FileEdit Changed="@OnChanged" />
</Field>
```

```
@code {
    Task OnChanged( FileChangedEventArgs e )
    {
        return Task.CompletedTask;
    }
}
```

### Multiple files

Multiple file uploading is supported by enabling  attribute to component. In this case  property
        of  can contain multiple files.

```
<Field>
    <FileEdit Changed="@OnChanged" Multiple />
</Field>
```

```
@code {
    Task OnChanged( FileChangedEventArgs e )
    {
        return Task.CompletedTask;
    }
}
```

### Directories

Directory uploading is supported by enabling  attribute to component. In this case  property
        of  can contain multiple files within a directory.

```
<Field>
    <FileEdit Changed="@OnChanged" Directory />
</Field>
```

```
@code {
    Task OnChanged( FileChangedEventArgs e )
    {
        return Task.CompletedTask;
    }
}
```

### Multiple Directories

Multiple Directory uploading is supported by enabling  and  attribute to component. In this case  property
        of  can contain multiple files within a directory.

```
<Field>
    <FileEdit Changed="@OnChanged" Directory Multiple />
</Field>
```

```
@code {
    Task OnChanged( FileChangedEventArgs e )
    {
        return Task.CompletedTask;
    }
}
```

### Limiting to certain file types

Not all browsers support or respect the  attribute on file inputs.

```
<!-- Accept all image formats by IANA media type wildcard-->
<Field>
    <FileEdit Filter="image/*" />
</Field>

<!-- Accept specific image formats by IANA type -->
<Field>
    <FileEdit Filter="image/jpeg, image/png, image/gif" />
</Field>

<!-- Accept specific image formats by extension -->
<Field>
    <FileEdit Filter=".jpg, .png, .gif" />
</Field>
```

## Events

### Changed

This is the main event that will be called every time a user selects a single or multiple files.
    Depending on the mode in which the FileEdit currently operates. In all cases the event argument is the same.
    Only difference is that Files array will contain single or multiple items.

### Written

This event will be called on every buffer of data that has being written to the destination stream.
    It is directly related to the MaxMessageSize attribute found on FileEdit component and will contain the information
    about currently processed file, it’s offset and data array.

### Progressed

Similar to the Written, this event will also be called while file is writing to the destination stream but it will
    contain only the progress and percentage on how much the file is being uploaded.

    Note: If Progressed  and Written events aren't important to you, we highly advise you the usage of the DisableProgressReport Parameter, as it will improve file transfer significantly.

### Started

This event will be called each time one of the selected file(s) has started the upload process.

### Ended

This event is fired after the file has ended the upload process. If there was no error it will have Success property set to true.

## Examples

### WriteToStreamAsync

In this example you can see the usage of all events, including the  and .
        For your own use case you can just focus on  event.

```
@using System.IO

<Field>
    <FileEdit Changed="@OnChanged" Written="@OnWritten" Progressed="@OnProgressed" />
</Field>
```

```
@code {
    string fileContent;

    async Task OnChanged( FileChangedEventArgs e )
    {
        try
        {
            foreach ( var file in e.Files )
            {
                // A stream is going to be the destination stream we're writing to.
                using ( var stream = new MemoryStream() )
                {
                    // Here we're telling the FileEdit where to write the upload result
                    await file.WriteToStreamAsync( stream );

                    // Once we reach this line it means the file is fully uploaded.
                    // In this case we're going to offset to the beginning of file
                    // so we can read it.
                    stream.Seek( 0, SeekOrigin.Begin );

                    // Use the stream reader to read the content of uploaded file,
                    // in this case we can assume it is a textual file.
                    using ( var reader = new StreamReader( stream ) )
                    {
                        fileContent = await reader.ReadToEndAsync();
                    }
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

    void OnWritten( FileWrittenEventArgs e )
    {
        Console.WriteLine( $"File: {e.File.Name} Position: {e.Position} Data: {Convert.ToBase64String( e.Data )}" );
    }

    void OnProgressed( FileProgressedEventArgs e )
    {
        Console.WriteLine( $"File: {e.File.Name} Progress: {e.Percentage}" );
    }
}
```

### OpenReadStream

We highly advise the usage of this api on Blazor WebAssembly as it is very performant.

```
@using System.IO

<Field>
    <FileEdit Changed="@OnChanged" Written="@OnWritten" Progressed="@OnProgressed" />
</Field>
```

```
@code {
    async Task OnChanged( FileChangedEventArgs e )
    {
        try
        {
            var file = e.Files.FirstOrDefault();
            if ( file == null )
            {
                return;
            }

            using ( MemoryStream result = new MemoryStream() )
            {
                await file.OpenReadStream( long.MaxValue ).CopyToAsync( result );
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

    void OnWritten( FileWrittenEventArgs e )
    {
        Console.WriteLine( $"File: {e.File.Name} Position: {e.Position} Data: {Convert.ToBase64String( e.Data )}" );
    }

    void OnProgressed( FileProgressedEventArgs e )
    {
        Console.WriteLine( $"File: {e.File.Name} Progress: {e.Percentage}" );
    }
}
```

### Reset

By default after each file upload has finished, file input will automatically reset to it’s initial state.
        If you want this behavior disabled and control it manually you need to first set  to .
        After that you can call  every time you want the file input to be reset.

```
<Field>
    <FileEdit @ref="@fileEdit" AutoReset="false" Changed="@OnChanged" />
</Field>
<Field>
    <Button Color="Color.Primary" Clicked="Reset">Reset</Button>
</Field>
```

```
@code {
    FileEdit fileEdit;

    Task OnChanged(FileChangedEventArgs e)
    {
        return Task.CompletedTask;
    }

    Task Reset()
    {
        return fileEdit.Reset().AsTask();
    }
}
```

### Show Picker

If you want to show the default picker that comes with the file input element you can make it by using the ShowPicker() function.

Note: Keep in mind that not all browser will support the ShowPicker() function.

```
<Field>
    <Button Color="Color.Primary" Clicked="@(()=>fileEditRef.ShowPicker())">
        Show Picker
    </Button>
</Field>
<Field>
    <FileEdit @ref="@fileEditRef" />
</Field>
```

```
@code {
    FileEdit fileEditRef;
}
```

## API

### Parameters

| Parameter             | Description                                                                                                                                                                                                                                                                      | Type                 | Default                   |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|---------------------------|
| Autofocus             | Set's the focus to the component after the rendering is done.                                                                                                                                                                                                                    | bool                 | false                     |
| AutoReset             | If true file input will be automatically reset after it has being uploaded.                                                                                                                                                                                                      | bool                 | true                      |
| BrowseButtonLocalizer | Function used to handle custom localization that will override a default Localization.ITextLocalizer.                                                                                                                                                                            | TextLocalizerHandler | null                      |
| ChildContent          | Specifies the content to be rendered inside this FileEdit.                                                                                                                                                                                                                       | RenderFragment       | null                      |
| Directory             | Gets or Sets whether file picker should upload directories.                                                                                                                                                                                                                      | bool                 | false                     |
| Disabled              | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.                                                                                                                                                                          | bool                 | false                     |
| DisableProgressReport | Gets or sets whether report progress should be disabled. By enabling this setting, Progressed and Written callbacks won't be called. Internal file progress won't be tracked.     This setting can speed up file transfer considerably.                                          | bool                 | false                     |
| Feedback              | Placeholder for validation messages.                                                                                                                                                                                                                                             | RenderFragment       | null                      |
| Filter                | Specifies the types of files that the input accepts. See w3schools.com.                                                                                                                                                                                                          | string               |                           |
| MaxChunkSize          | Gets or sets the max chunk size when uploading the file.     Take note that if you're using FileEdit.OpenReadStream(FileEntry,CancellationToken) you're provided with a stream and should configure the chunk size when handling with the stream.Remarks See docs.microsoft.com. | int                  | 20 * 1024                 |
| MaxFileSize           | Maximum file size in bytes, checked before starting upload (note: never trust client, always check file     size at server-side). Defaults to long.MaxValue.                                                                                                                     | long                 | long.MaxValue             |
| Multiple              | Enables the multiple file selection.                                                                                                                                                                                                                                             | bool                 | false                     |
| Placeholder           | Sets the placeholder for the empty file input.                                                                                                                                                                                                                                   | string               |                           |
| ReadOnly              | Add the readonly boolean attribute on an input to prevent modification of the input’s value.                                                                                                                                                                                     | bool                 | false                     |
| SegmentFetchTimeout   | Gets or sets the Segment Fetch Timeout when uploading the file.                                                                                                                                                                                                                  | TimeSpan             | TimeSpan.FromMinutes( 1 ) |
| Size                  | Sets the size of the input control.                                                                                                                                                                                                                                              | Size?                | null                      |
| TabIndex              | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation.                                                                                                                                                                    | int?                 | null                      |

### Events

| Event                 | Description                                                                                                                                                                                                                                                                            | Type                                   |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------|
| Blur                  | The blur event fires when an element has lost focus.                                                                                                                                                                                                                                   | EventCallback<FocusEventArgs>          |
| Changed               | Occurs every time the selected file has changed, including when the reset operation is executed.                                                                                                                                                                                       | EventCallback<FileChangedEventArgs>    |
| CustomValidationValue | Used to provide custom validation value on which the validation will be processed with     the Validation.Validator handler.Remarks Should be used carefully as it's only meant for some special cases when input is used     in a wrapper component, like Autocomplete or SelectList. | Func<TValue>                           |
| Ended                 | Occurs when an individual file upload has ended.                                                                                                                                                                                                                                       | EventCallback<FileEndedEventArgs>      |
| FocusIn               | Occurs when the input box gains focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>          |
| FocusOut              | Occurs when the input box loses focus.                                                                                                                                                                                                                                                 | EventCallback<FocusEventArgs>          |
| KeyDown               | Occurs when a key is pressed down while the control has focus.                                                                                                                                                                                                                         | EventCallback<KeyboardEventArgs>       |
| KeyPress              | Occurs when a key is pressed while the control has focus.                                                                                                                                                                                                                              | EventCallback<KeyboardEventArgs>       |
| KeyUp                 | Occurs when a key is released while the control has focus.                                                                                                                                                                                                                             | EventCallback<KeyboardEventArgs>       |
| OnFocus               | Occurs when the input box gains or loses focus.                                                                                                                                                                                                                                        | EventCallback<FocusEventArgs>          |
| Progressed            | Notifies the progress of file being written to the destination stream.                                                                                                                                                                                                                 | EventCallback<FileProgressedEventArgs> |
| Started               | Occurs when an individual file upload has started.                                                                                                                                                                                                                                     | EventCallback<FileStartedEventArgs>    |
| Written               | Occurs every time the part of file has being written to the destination stream.                                                                                                                                                                                                        | EventCallback<FileWrittenEventArgs>    |

### Methods

| Method                  | Description                                                                                  | Return    | Parameters                                                              |
|-------------------------|----------------------------------------------------------------------------------------------|-----------|-------------------------------------------------------------------------|
| NotifyChange            | Notifies the component that file input value has changed.                                    | Task      | FileEntry[] files                                                       |
| UpdateFileStartedAsync  | Notifies the component that file upload is about to start.                                   | Task      | IFileEntry fileEntry                                                    |
| UpdateFileEndedAsync    | Notifies the component that file upload has ended.                                           | Task      | IFileEntry fileEntry, bool success, FileInvalidReason fileInvalidReason |
| UpdateFileWrittenAsync  | Updates component with the latest file data.                                                 | Task      | IFileEntry fileEntry, long position, byte[] data                        |
| UpdateFileProgressAsync | Updated the component with the latest upload progress.                                       | Task      | IFileEntry fileEntry, long progressProgress                             |
| WriteToStreamAsync      | Writes the file data to the target stream.                                                   | Task      | FileEntry fileEntry, Stream stream, CancellationToken cancellationToken |
| OpenReadStream          | Opens the stream for reading the uploaded file.                                              | Stream    | FileEntry fileEntry, CancellationToken cancellationToken                |
| Reset                   | Manually resets the input file value.                                                        | ValueTask |                                                                         |
| RemoveFile              | Removes a file from the current file selection.                                              | ValueTask | int fileId                                                              |
| ShowPicker              | Show a browser picker for the file input.                                                    | Task      |                                                                         |
| Focus                   | Sets the focus on the underline element.                                                     | Task      | bool scrollToElement                                                    |
| Revalidate              | Forces the Validation (if any is used) to re-validate with the new custom or internal value. | Task      |                                                                         |

###### On this page

#### 

## 