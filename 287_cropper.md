# Blazorise Cropper component

A component used to crop images.

When building an application, best practice requires reducing an image's surrounding noise and directing a user's attention to a specific part of the image. Image cropping is a method for manipulating images to remove any unwanted elements. By changing the aspect ratio or orientation, we can draw viewers' eyes to the photograph's primary subject and improve the overall composition. This applies to profile pictures or uploading images with specific dimensions.

The new Cropper component handles all of that. You can upload an image and then select part of it, rotate, scale, and crop it. You can also add a preview by adding a CropperViewer whenever on a page, and it will automatically synchronize with the latest selection.

## Installation

### NuGet

Install extension from NuGet.

```
Install-Package Blazorise.Cropper
```

### Imports

In your main  add:

```
@using Blazorise.Cropper
```

### Message Size

This step is recommended for Blazor Server only. In a default Blazor Server project template, the SignalR settings might be too small for some components like Cropper. To make it work, you should increase the  in your projects .

```
.AddHubOptions(o =>
{
    o.MaximumReceiveMessageSize = 1024 * 1024 * 100;
})
```

## Examples

### Basic

The image cropper is pretty straightforward. You need to define a Source parameter, and a reference.

<!-- image -->

```
<Row>
    <Column>
        <FieldLabel>
            Image Cropper
        </FieldLabel>
        <FieldBody>
            <Cropper @ref="cropper" Source="img/gallery/6.jpg" SelectionChanged="@OnSelectionChanged" Style="aspect-ratio: 16 / 9; height: 100%;" />
        </FieldBody>
    </Column>
    <Column>
        <Div Margin="Margin.Is2.FromBottom">
            <Button Color="Color.Primary" Clicked="@GetCroppedImage" Disabled="@cropButtonDisabled">Get Cropped Image</Button>
            <Button Color="Color.Secondary" Clicked="@ResetSelection" Disabled="@cropButtonDisabled">Reset Selection</Button>
        </Div>
        <Image Source="@result" Border="Border.Is1" Style="width: 250px; height: 250px;" />
    </Column>
</Row>
```

```
@code {
    private Cropper cropper;
    private string result;
    private bool cropButtonDisabled = true;

    private Task OnSelectionChanged( CropperSelectionChangedEventArgs eventArgs )
    {
        if ( eventArgs.Width != 0 )
        {
            cropButtonDisabled = false;

            return InvokeAsync( StateHasChanged );
        }

        return Task.CompletedTask;
    }

    private async Task GetCroppedImage()
    {
        result = await cropper.CropAsBase64ImageAsync( new() { Width = 250, Height = 250 } );
    }

    private async Task ResetSelection()
    {
        cropButtonDisabled = true;

        await cropper.ResetSelection();
    }
}
```

### Viewer

To add a preview support you can use a  component. Once added you need to connect it to a  by assigning the  parameter. This parameter is used as a synchronization context bewteen the cropper and a viewer.

```
<Row>
    <Column>
        <FieldLabel>
            Image Cropper
        </FieldLabel>
        <FieldBody>
            <Cropper Source="img/gallery/3.jpg" CropperState="@cropperState" />
        </FieldBody>
    </Column>
    <Column>
        <FieldLabel>
            Preview
        </FieldLabel>
        <FieldBody>
            <CropperViewer CropperState="@cropperState" Margin="Margin.Is2.FromBottom" Style="width: 150px; height: 150px;" />
            <CropperViewer CropperState="@cropperState" Margin="Margin.Is2.FromBottom" Style="width: 100px; height: 100px;" />
            <CropperViewer CropperState="@cropperState" Margin="Margin.Is2.FromBottom" Style="width: 50px; height: 50px;" />
        </FieldBody>
    </Column>
</Row>
```

```
@code {
    private CropperState cropperState = new();
}
```

## API

### Parameters

#### Cropper

| Parameter        | Description                                                                                  | Type                    | Default                       |
|------------------|----------------------------------------------------------------------------------------------|-------------------------|-------------------------------|
| Alt              | The alt text of the image.                                                                   | string                  |                               |
| CropperState     | Provides a shared state and syncronization context between the cropper and cropper viewer.   | CropperState            | null                          |
| CrossOrigin      | The cross-origin attribute of the image.                                                     | string                  |                               |
| Enabled          | Indicates whether this element is disabled.                                                  | bool                    | true                          |
| GridOptions      | Provides properties for manipulating the layout and presentation of selection grid elements. | CropperGridOptions      | new CropperGridOptions()      |
| ImageOptions     | Provides properties for manipulating the layout and presentation of image elements.          | CropperImageOptions     | new CropperImageOptions()     |
| SelectionOptions | Provides properties for manipulating the layout and presentation.                            | CropperSelectionOptions | new CropperSelectionOptions() |
| ShowBackground   | Indicates whether this element has a grid background.                                        | bool                    | true                          |
| Source           | The original image source.                                                                   | string                  |                               |

#### CropperViewer

| Parameter    | Description                                                                                | Type         | Default   |
|--------------|--------------------------------------------------------------------------------------------|--------------|-----------|
| CropperState | Provides a shared state and syncronization context between the cropper and cropper viewer. | CropperState | null      |

#### CropperCropOptions

| Parameter    | Description                                                                                                                                                                                                                                                                                                        | Type    | Default     |
|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|-------------|
| Height       | The destination height  of the output canvas.                                                                                                                                                                                                                                                                      | int     | 0           |
| ImageQuality | A Number between 0 and 1 indicating the image quality to be used when creating images using file formats that support lossy compression (such as image/jpeg or image/webp).Remarks A user agent will use its default quality value if this option is not specified, or if the number is outside the allowed range. | double? | 1d          |
| ImageType    | A string indicating the image format. The default type is image/png; this image format will be also used if the specified type is not supported.                                                                                                                                                                   | string  | "image/png" |
| Width        | The destination width of the output canvas.                                                                                                                                                                                                                                                                        | int     | 0           |

### Events

#### Cropper

| Event            | Description                                                                                        | Type                                         |
|------------------|----------------------------------------------------------------------------------------------------|----------------------------------------------|
| CropEnded        | This event fires when the canvas (image wrapper) or the crop box stops changing.                   | Func<Task>                                   |
| CropMoved        | This event fires when the canvas (image wrapper) or the crop box is changing.                      | Func<Task>                                   |
| Cropped          | This event fires when the canvas (image wrapper) or the crop box changes.                          | Func<CropperCroppedEventArgs, Task>          |
| CropStarted      | This event fires when the canvas (image wrapper) or the crop box starts to change.                 | Func<Task>                                   |
| ImageReady       | This event fires when the image is ready / loaded.                                                 | Func<Task>                                   |
| SelectionChanged | The event is fired when the position or size of the selection is going to change.                  | Func<CropperSelectionChangedEventArgs, Task> |
| Zoomed           | This event fires when a cropper instance starts to zoom in or zoom out its canvas (image wrapper). | Func<CropperZoomedEventArgs, Task>           |

### Methods

#### Cropper

| Method                 | Description                                            | Return            | Parameters                 |
|------------------------|--------------------------------------------------------|-------------------|----------------------------|
| CropAsBase64ImageAsync | Get the cropped image as Base64 image.                 | ValueTask<string> | CropperCropOptions options |
| Move                   | Moves the image.                                       | ValueTask         | int x, int y               |
| MoveTo                 | Moves the image to a specific position.                | ValueTask         | int x, int y               |
| Zoom                   | Zooms the image.                                       | ValueTask         | double scale               |
| Rotate                 | Rotates the image.                                     | ValueTask         | double angle               |
| Scale                  | Scale the image.                                       | ValueTask         | int x, int y               |
| Center                 | Center the image.                                      | ValueTask         | string size                |
| ResetSelection         | Resets the selection to its initial position and size. | ValueTask         |                            |

###### On this page

#### 

## 