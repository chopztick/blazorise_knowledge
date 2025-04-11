# FilePicker component

Customized, cross-browser consistent, enchanced file input control that supports single file and multiple files upload.

Blazorise FilePicker component provides extra functionality, listing and detailing files, providing clear and upload buttons and inbuilt progress.
    Note: The inbuilt progress can be disabled by the DisableProgressReport Parameter, this will in exchange improve file transfer significantly.

## Examples

### Upload Files with List view mode

An example using the FilePicker's list show mode and  upload method.

#### 

```
@using System.IO

<Field>
    <FilePicker Multiple Upload="OnFileUpload" ShowMode="FilePickerShowMode.List" />
</Field>
```

```
@code {

    async Task OnFileUpload( FileUploadEventArgs e )
    {
        try
        {
            using ( MemoryStream result = new MemoryStream() )
            {
                await e.File.OpenReadStream( long.MaxValue ).CopyToAsync( result );
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
}
```

### Upload Folders with List view mode

An example using the FilePicker's list show mode and  upload method.

#### 

```
@using System.IO

<Field>
    <FilePicker Directory Multiple Upload="OnFileUpload" ShowMode="FilePickerShowMode.List" />
</Field>
```

```
@code {
    async Task OnFileUpload( FileUploadEventArgs e )
    {
        try
        {
            using ( MemoryStream result = new MemoryStream() )
            {
                await e.File.OpenReadStream( long.MaxValue ).CopyToAsync( result );
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
}
```

### Upload Files with Dropdown view mode

An example using the FilePicker's dropdown show mode and  upload method.

#### 

```
@using System.IO

<Field>
    <FilePicker Multiple Upload="OnFileUpload" ShowMode="FilePickerShowMode.Dropdown" />
</Field>
```

```
@code {
    string fileContent;

    async Task OnFileUpload( FileUploadEventArgs e )
    {
        try
        {
            // A stream is going to be the destination stream we're writing to.
            using ( var stream = new MemoryStream() )
            {
                // Here we're telling the FileEdit where to write the upload result
                await e.File.WriteToStreamAsync( stream );

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
        catch ( Exception exc )
        {
            Console.WriteLine( exc.Message );
        }
        finally
        {
            this.StateHasChanged();
        }
    }
}
```

### Custom

An example customizing the FilePicker.

#### 

```
@using System.IO

<Field>
    <FilePicker @ref="filePickerCustom"
                Multiple
                Upload="OnFileUpload"
                ShowMode="FilePickerShowMode.List">
        <FileTemplate>
            <Div Flex="Flex.JustifyContent.Between">
                <Div>
                    <Heading Size="HeadingSize.Is5">@context.File.Name</Heading>
                    <Paragraph>@FilePicker.GetFileSizeReadable(context.File)</Paragraph>
                </Div>
                <Div>
                    @if ( context.File.Status == FileEntryStatus.Ready )
                    {
                        <Icon TextColor="TextColor.Primary" Name="IconName.FileUpload" />
                    }
                    else if ( context.File.Status == FileEntryStatus.Uploading )
                    {
                        <Icon TextColor="TextColor.Warning" Name="IconName.Bolt" />
                    }
                    else if ( context.File.Status == FileEntryStatus.Uploaded )
                    {
                        <Icon TextColor="TextColor.Success" Name="IconName.CheckCircle" />
                    }
                    else if ( context.File.Status == FileEntryStatus.Error )
                    {
                        <Icon TextColor="TextColor.Danger" Name="IconName.TimesCircle" />
                    }
                </Div>
            </Div>
            <Divider Margin="Margin.Is0" />
        </FileTemplate>
        <ButtonsTemplate>
            <Progress Value="@filePickerCustom.GetProgressPercentage()" />
            <Buttons>
                <Button Clicked="@context.Clear" Color="Color.Warning"><Icon Name="IconName.Clear" /></Button>
                <Button Clicked="@context.Upload" Color="Color.Primary"><Icon Name="IconName.FileUpload" /></Button>
            </Buttons>
        </ButtonsTemplate>
    </FilePicker>
</Field>
```

```
@code {
    private FilePicker filePickerCustom;

    async Task OnFileUpload( FileUploadEventArgs e )
    {
        try
        {
            using ( MemoryStream result = new MemoryStream() )
            {
                await e.File.OpenReadStream( long.MaxValue ).CopyToAsync( result ) ;
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
}
```

## API

### Parameters

| Parameter             | Description                                                                                                                                                                                                                             | Type                                     | Default                   |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------|---------------------------|
| AutoReset             | If true file input will be automatically reset after it has being uploaded.                                                                                                                                                             | bool                                     | false                     |
| ButtonsTemplate       | Provides a custom content for upload, clear and cancel buttons.                                                                                                                                                                         | RenderFragment<FilePickerButtonsContext> | null                      |
| ChildTemplate         | Input content.                                                                                                                                                                                                                          | RenderFragment                           | null                      |
| Directory             | Gets or Sets whether file picker should upload directories.                                                                                                                                                                             | bool                                     | false                     |
| Disabled              | Add the disabled boolean attribute on an input to prevent user interactions and make it appear lighter.                                                                                                                                 | bool                                     | false                     |
| DisableProgressReport | Gets or sets whether report progress should be disabled. By enabling this setting, Progressed and Written callbacks won't be called. Internal file progress won't be tracked.     This setting can speed up file transfer considerably. | bool                                     | false                     |
| Feedback              | Placeholder for validation messages.                                                                                                                                                                                                    | RenderFragment                           | null                      |
| FilePickerLocalizer   | Function used to handle custom localization that will override a default Localization.ITextLocalizer.                                                                                                                                   | TextLocalizerHandler                     | null                      |
| FileTemplate          | Provides a custom file content.                                                                                                                                                                                                         | RenderFragment<FilePickerFileContext>    | null                      |
| Filter                | Specifies the types of files that the input accepts. See w3schools.com.                                                                                                                                                                 | string                                   |                           |
| MaxChunkSize          | Gets or sets the max chunk size when uploading the file.                                                                                                                                                                                | int                                      | 20 * 1024                 |
| MaxFileSize           | Maximum file size in bytes, checked before starting upload (note: never trust client, always check file     size at server-side). Defaults to long.MaxValue.                                                                            | long                                     | long.MaxValue             |
| Multiple              | Enables the multiple file selection.                                                                                                                                                                                                    | bool                                     | false                     |
| Placeholder           | Sets the placeholder for the empty file input.                                                                                                                                                                                          | string                                   |                           |
| ReadOnly              | Add the readonly boolean attribute on an input to prevent modification of the input value.                                                                                                                                              | bool                                     | false                     |
| SegmentFetchTimeout   | Gets or sets the Segment Fetch Timeout when uploading the file.                                                                                                                                                                         | TimeSpan                                 | TimeSpan.FromMinutes( 1 ) |
| ShowMode              | Gets or Sets FilePicker's show mode.     Defaults to FilePickerShowMode.ListPossible values:List, Dropdown                                                                                                                              | FilePickerShowMode                       | FilePickerShowMode.List   |

### Events

| Event      | Description                                                                                      | Type                                   |
|------------|--------------------------------------------------------------------------------------------------|----------------------------------------|
| Changed    | Occurs every time the selected file has changed, including when the reset operation is executed. | EventCallback<FileChangedEventArgs>    |
| Ended      | Occurs when an individual file upload has ended.                                                 | EventCallback<FileEndedEventArgs>      |
| Progressed | Notifies the progress of file being written to the destination stream.                           | EventCallback<FileProgressedEventArgs> |
| Started    | Occurs when an individual file upload has started.                                               | EventCallback<FileStartedEventArgs>    |
| Upload     | Occurs once the FilePicker's Upload is triggered for every file.                                 | EventCallback<FileUploadEventArgs>     |
| Written    | Occurs every time the part of file has being written to the destination stream.                  | EventCallback<FileWrittenEventArgs>    |

### Methods

| Method                | Description                                                                    | Return   | Parameters                        |
|-----------------------|--------------------------------------------------------------------------------|----------|-----------------------------------|
| GetProgressPercentage | Gets progress for percentage display.                                          | int      |                                   |
| IsFileBeingUploaded   | Tracks whether the current file is being uploaded.                             | bool     | IFileEntry file                   |
| IsBusy                | Tracks whether the FilePicker is busy and user interaction should be disabled. | bool     |                                   |
| IsUploadReady         | Tracks whether the FilePicker has files ready to upload.                       | bool     |                                   |
| GetFileSizeReadable   | Converts the file size in bytes into a proper human readable format.           | string   | IFileEntry file                   |
| GetFileStatus         | Gets the File Status                                                           | string   | IFileEntry file                   |
| GetLocalizedString    | Gets a FilePicker Localized string.                                            | string   | string name                       |
| RemoveFile            | Removes the file from FileEdit.                                                | Task     | IFileEntry file, bool confirm     |
| Clear                 | Clears the FileEdit by resetting the state.                                    | Task     | bool confirm                      |
| UploadAll             | Uploads the current files.                                                     | Task     |                                   |
| UploadFile            | Uploads a single file if the status is set to ready.                           | Task     | IFileEntry file, bool forceUpload |
| Cancel                | Cancels any ongoing upload operation.                                          | Task     | bool confirm                      |

###### On this page

#### 

## 