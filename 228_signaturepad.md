# Blazorise Signature Pad component

A powerful tool for capturing and displaying user signatures on the web.

The Blazorise &lt;SignaturePad&gt; extension is a customizable and easy-to-use component that allows users to capture and display their signatures. The component provides a range of options to customize the appearance of the signature pad, such as the color and width of the signature stroke, and also allows you to save and load the signature data as an image file or a JSON object.

## Examples

### Basic example

Simply place the  extension and you're ready to capture signatures.

```
<SignaturePad />
```

### Two-way binding

The SignaturePad @bind-Value syntax is used in Blazor for two-way data binding. This means that when a user signs their name using the SignaturePad component, the data representing the signature is automatically updated in the @data-Value parameter. Similarly, if the @data-Value parameter changes elsewhere in your code, the signature displayed in the SignaturePad component will automatically update to reflect this.

To better understand how the SignaturePad component works with two-way data binding, consider the following example:

<!-- image -->

```
<Row>
    <Column>
        <Card>
            <CardHeader>
                <CardTitle>Signature pad</CardTitle>
            </CardHeader>
            <CardBody>
                <SignaturePad @bind-Value="@data"></SignaturePad>
            </CardBody>
        </Card>
    </Column>

    <Column>
        <Card>
            <CardHeader>
                <CardTitle>Preview</CardTitle>
            </CardHeader>
            <CardBody>
                <Image Source="@Image64" Fluid />
             </CardBody>
         </Card>
     </Column>
 </Row>
```

```
@code {
    byte[] data = null;

    string Image64 => SignaturePad.GetDataUrl( data );
}
```

### Background Color

The  property in Blazorise's SignaturePad customizes the pad's appearance by setting its background color. Accepting a CSS color string, it allows design flexibility, improving visibility or matching aesthetic requirements. It's advisable to use colors that contrast well with the signature for clear visibility.

```
<SignaturePad BackgroundColor="rgba(232, 222, 252, 1)" />
```

### Pen Color

The  parameter in Blazorise's SignaturePad adjusts the color of the pen used for signatures. Accepting a CSS color string, it enhances customization and user experience. Chosen color should contrast well with the background for optimum visibility.

```
<SignaturePad PenColor="#ff0000" />
```

### Dot Size

The  property controls the diameter of the signature's stroke. It interprets a numerical input to define the thickness of the line, facilitating user-customizable detail and individuality in the resultant signatures.

```
<SignaturePad DotSize="5" />
```

### Min Line Width

The  property in the SignaturePad component of Blazorise sets the minimum thickness of the line drawn for a signature. It accepts a numerical input that dictates the smallest possible line width, offering users control over the finesse and precision of the signature strokes.

```
<SignaturePad MinLineWidth="5" />
```

### Max Line Width

The  property within Blazorise's SignaturePad governs the maximum thickness of the signature stroke. By accepting a numerical input, it sets an upper limit to the line width, ensuring control over the boldness and prominence of the rendered signatures.

```
<SignaturePad MaxLineWidth="10"/>
```

### Min Distance

Blazorise's SignaturePad component includes the  parameter, which determines the minimum distance required for the pen to move before a new stroke is registered. By accepting numerical values, it provides control over the sensitivity of stroke detection, affecting the smoothness and precision of the resulting signatures.

```
<SignaturePad MinDistance="100" />
```

### Throttle

The  parameter of Blazorise's SignaturePad is responsible for controlling the rate of signature data collection. By accepting a numerical value, it limits how often the pad captures the signature data within a specific time frame, influencing the smoothness and responsiveness of the signature drawing process.

```
<SignaturePad Throttle="20" />
```

### Velocity Filter Weight

The  parameter in Blazorise's SignaturePad is employed to regulate the influence of velocity on the drawn stroke's width. It accepts a numerical value, contributing to a dynamic stroke width based on the speed of signing, which introduces a more natural and fluid appearance to the signatures.

```
<SignaturePad VelocityFilterWeight="20" />
```

### Custom Size

The CanvasWidth and CanvasHeight properties of the SignaturePad component in Blazorise are used to set the dimensions of the drawing area, or the "canvas", of the SignaturePad.

CanvasWidth: This property sets the width of the SignaturePad. The value is usually defined in pixels. By adjusting this value, you can control how wide the signature pad will appear in your application, thus influencing how much horizontal space a user has to create their signature.
                    
CanvasHeight: Similarly, this property sets the height of the SignaturePad. Also typically defined in pixels, adjusting this value will control how tall the signature pad is, effectively controlling the vertical space available for the signature.

The use case for these properties generally involves tailoring the size of the SignaturePad to fit a specific design or layout in your application. For instance, you may want a wider SignaturePad for a desktop application where screen real estate is plentiful, while a narrower SignaturePad might be more suitable for a mobile application or a form with a vertical layout.

```
<SignaturePad CanvasWidth="600" CanvasHeight="400" Shadow="Shadow.Small" />
```

### Image Type

The ImageType, ImageQuality, and IncludeImageBackgroundColor parameters in Blazorise's SignaturePad provide control over the final output of the signature.

ImageType determines the format of the exported image and supports PNG, JPEG, and SVG. This allows users to choose the appropriate format for their needs, balancing factors like image quality and file size.

ImageQuality adjusts the quality of the generated image, specifically for JPEG and PNG formats. It accepts a numerical value between 0 and 1, with 1 being the highest quality. This enables users to fine-tune the trade-off between image fidelity and file size. SVG images do not use this parameter since they're a vector format and do not lose quality.

The IncludeImageBackgroundColor property is an additional parameter that's specifically applicable when ImageType is set to SVG in Blazorise's SignaturePad. When it's enabled (set to true), the SVG output will include the background color as specified by the BackgroundColor property. This offers users more control over the look of the signature pad, especially when they need to maintain the background color in the final SVG image.

<!-- image -->

```
<Row>
    <Column>
        <Card>
            <CardHeader>
                <CardTitle>Signature pad</CardTitle>
            </CardHeader>
            <CardBody>
                <SignaturePad @bind-Value="@data" ImageType="SignaturePadImageType.Svg" />
            </CardBody>
        </Card>
    </Column>

    <Column>
        <Card>
            <CardHeader>
                <CardTitle>SVG Image</CardTitle>
            </CardHeader>
            <CardBody>
                <Image Source="@Image64" Fluid />
             </CardBody>
         </Card>
     </Column>
 </Row>
```

```
@code {
    byte[] data = null;

    string Image64 => SignaturePad.GetDataUrl( data, SignaturePadImageType.Svg );
}
```

### Undo

The  method in the SignaturePad component removes the last stroke drawn on the signature pad. Each action, or stroke, is independent, and calling  will only affect the most recent one. It's an effective way to correct errors without clearing the entire pad. This function doesn't revert changes to SignaturePad's configuration, such as pen color or width, and has no effect if no strokes have been made.

```
<Row>
    <Column>
        <Button Color="Color.Primary" Clicked="@OnUndoClicked">
            Undo
        </Button>
    </Column>
</Row>
<Row>
    <Column>
        <SignaturePad @ref="@signaturePadRef" @bind-Value="@data" />
    </Column>
</Row>
```

```
@code {
    SignaturePad signaturePadRef;

    byte[] data;

    async Task OnUndoClicked()
    {
        await signaturePadRef.Undo();
    }
}
```

## API

### Parameters

| Parameter                   | Description                                                                                                                               | Type                  | Default                   |
|-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|---------------------------|
| BackgroundColor             | The color used to define the background color of the signature pad. Can be any color format; including HEX, or rgb.                       | string                |                           |
| CanvasHeight                | Defines the height, in pixels, of the underline canvas element.                                                                           | int?                  | null                      |
| CanvasWidth                 | Defines the width, in pixels, of the underline canvas element.                                                                            | int?                  | null                      |
| DotSize                     | The radius of a single dot. Also the width of the start of a mark.                                                                        | double                | 0                         |
| ImageQuality                | The encoder options for image type [png, jpeg] to get from the canvas element. Accepted range is from 0 to 1, where 1 means best quality. | double?               | null                      |
| ImageType                   | The image type [png, jpeg, svg] to get from the canvas element.Possible values:Png, Jpeg, Svg                                             | SignaturePadImageType | SignaturePadImageType.Png |
| IncludeImageBackgroundColor | If true, the [svg] image returned from the canvas will include background color defined by the BackgroundColor parameter.                 | bool                  | false                     |
| MaxLineWidth                | The maximum width of a line.                                                                                                              | double                | 0                         |
| MinDistance                 | Add the next point only if the previous one is farther than 'n' pixels. Defaults to 5.                                                    | int                   | 0                         |
| MinLineWidth                | The minimum width of a line.                                                                                                              | double                | 0                         |
| PenColor                    | The color used to define the lines color of the signature pad. Can be any color format; including HEX, or rgb.                            | string                |                           |
| ReadOnly                    | If true, prevents the user interaction.                                                                                                   | bool                  | false                     |
| TabIndex                    | If defined, indicates that its element can be focused and can participates in sequential keyboard navigation.                             | int?                  | null                      |
| Throttle                    | The time in milliseconds to throttle drawing. Set to 0 to turn off throttling.                                                            | int                   | 0                         |
| Value                       | Gets or sets value for the signature pad.                                                                                                 | byte[]                | null                      |
| VelocityFilterWeight        | The weight used to modify new velocity based on the previous velocity.                                                                    | double                | 0                         |

### Events

| Event        | Description                                                                                                                                                    | Type                                            |
|--------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| BeginStroke  | Gets or sets the event that is triggered when a new stroke begins on the signature pad. The event provides information about the starting point of the stroke. | EventCallback<SignaturePadBeginStrokeEventArgs> |
| EndStroke    | Gets or sets the event that is triggered when a stroke ends on the signature pad. The event provides the signature pad's current image data as a Data URL.     | EventCallback<SignaturePadEndStrokeEventArgs>   |
| ValueChanged | Gets or sets the event that is triggered when the signature pad value changes. The event provides the new signature as a byte array.                           | EventCallback<byte[]>                           |

### Methods

| Method            | Description                                                                                                                                                                                                                                                                                                                                     | Return   | Parameters                                     |
|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|------------------------------------------------|
| Clear             | Clears the content of a signature canvas.                                                                                                                                                                                                                                                                                                       | Task     |                                                |
| Undo              | Undos the last stroke if there is any.                                                                                                                                                                                                                                                                                                          | Task     |                                                |
| NotifyBeginStroke | This method is called by JavaScript when a new stroke has begun in the signature pad. It invokes the BeginStroke     event asynchronously to notify any subscribers of the event.                                                                                                                                                               | Task     | double offsetX, double offsetY                 |
| NotifyEndStroke   | This method is called by JavaScript when a stroke has ended in the signature pad. It takes the encoded image     from the signature pad, converts it to bytes and sets the Value property of the component to the image data.     It then invokes the ValueChanged and EndStroke events asynchronously to notify any subscribers of the change. | Task     | string dataUrl, double offsetX, double offsetY |
| GetDataUrl        | Gets the data url based on the image type and the data array.                                                                                                                                                                                                                                                                                   | string   | byte[] data, SignaturePadImageType imageType   |

###### On this page

#### 

## 