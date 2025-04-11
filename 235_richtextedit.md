# Blazorise RichTextEdit component

The RichTextEdit component allows you to add and use a ‘WYSIWYG’ rich text editor.

The Blazorise RichTextEdit is based on the QuillJS JavaScript library.

- RichTextEdit the root editor component
    - Editor (Optional) the editor part with displayed html content
    - Toolbar (Optional) the editor toolbar definition
        - RichTextEditToolbarGroup toolbar group
            - RichTextEditToolbarButton toolbar button
            - RichTextEditToolbarSelect toolbar selection dropdown
                - RichTextEditToolbarSelectItem toolbar selection item
            - any custom button or component

## Installation

### NuGet

Install extension from NuGet.

```
Install-Package Blazorise.RichTextEdit
```

### Imports

In your main  add:

```
@using Blazorise.RichTextEdit
```

### Configuration

In your Blazor  add the following statement

```
builder.Services
    .AddBlazoriseRichTextEdit( options => { ... } );
```

### Options

| Name                  | Description                                                                                                                                       | Type   | Default   |
|-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|--------|-----------|
| UseShowTheme          | Load the QuillJS snow theme related resources.                                                                                                    | bool   | true      |
| UseBubbleTheme        | Load the QuillJS bubble theme related resources.                                                                                                  | bool   | false     |
| UseTables             | If true enables the QuillJs table module. Please be aware that this module is not part of the core QuillJs library, and it is still experimental. | bool   | false     |
| QuillJSVersion        | The QuillJS version to load.                                                                                                                      | string | 2.0.0     |
| DynamicLoadReferences | Load the RichTextEdit scripts and stylesheets on demand.                                                                                          | bool   | true      |

## Examples

### Basic

```
<RichTextEdit @ref="richTextEditRef"
              Theme="RichTextEditTheme.Snow"
              ContentChanged="@OnContentChanged"
              PlaceHolder="Type your post here..."
              ReadOnly="@readOnly"
              SubmitOnEnter="false"
              EnterPressed="@OnSave"
              ToolbarPosition="Placement.Bottom">
    <Editor>My example content</Editor>
    <Toolbar>
        <RichTextEditToolbarGroup>
            <RichTextEditToolbarButton Action="RichTextEditAction.Bold" />
            <RichTextEditToolbarButton Action="RichTextEditAction.Italic" />
            <RichTextEditToolbarSelect Action="RichTextEditAction.Size">
                <RichTextEditToolbarSelectItem Value="small" />
                <RichTextEditToolbarSelectItem Selected />
                <RichTextEditToolbarSelectItem Value="large" />
                <RichTextEditToolbarSelectItem Value="huge">Very Big</RichTextEditToolbarSelectItem>
            </RichTextEditToolbarSelect>
            <RichTextEditToolbarButton Action="RichTextEditAction.List" Value="ordered" />
            <RichTextEditToolbarButton Action="RichTextEditAction.List" Value="bullet" />
        </RichTextEditToolbarGroup>
        <!-- Custom toolbar content -->
        <RichTextEditToolbarGroup Float="Float.End">
            <Button onClick="window.open('https://www.quilljs.com/','quilljs')"><Icon Name="IconName.InfoCircle" /></Button>
            <Button Clicked="@OnSave"><Icon Name="IconName.Save" /></Button>
        </RichTextEditToolbarGroup>
    </Toolbar>
</RichTextEdit>
```

```
@code{
    protected RichTextEdit richTextEditRef;
    protected bool readOnly;
    protected string contentAsHtml;
    protected string contentAsDeltaJson;
    protected string contentAsText;
    protected string savedContent;

    public async Task OnContentChanged()
    {
        contentAsHtml = await richTextEditRef.GetHtmlAsync();
        contentAsDeltaJson = await richTextEditRef.GetDeltaAsync();
        contentAsText = await richTextEditRef.GetTextAsync();
    }

    public async Task OnSave()
    {
        savedContent = await richTextEditRef.GetHtmlAsync();
        await richTextEditRef.ClearAsync();
    }
}
```

### With Tables

To enable table support within the RichTextEdit component, you need to configure it in your Startup.cs file as follows:

```
.AddBlazoriseRichTextEdit( options =>
{
    options.UseTables = true;
} )
```

Once enabled, you can create tables within the RichTextEdit component using the following code:

Note:
                This feature is currently marked as experimental. While it provides basic table functionality, some advanced features may be limited or not fully supported. We recommend using it with caution until an official module is released by the Quill.js team.

```
<RichTextEdit>
    <Editor>My example content</Editor>
    <Toolbar>
        <RichTextEditToolbarGroup>
            <RichTextEditToolbarButton Action="RichTextEditAction.Bold" />
            <RichTextEditToolbarButton Action="RichTextEditAction.Italic" />
            <RichTextEditToolbarSelect Action="RichTextEditAction.Size">
                <RichTextEditToolbarSelectItem Value="small" />
                <RichTextEditToolbarSelectItem Selected />
                <RichTextEditToolbarSelectItem Value="large" />
                <RichTextEditToolbarSelectItem Value="huge">Very Big</RichTextEditToolbarSelectItem>
            </RichTextEditToolbarSelect>
            <RichTextEditToolbarButton Action="RichTextEditAction.List" Value="ordered" />
            <RichTextEditToolbarButton Action="RichTextEditAction.List" Value="bullet" />
        </RichTextEditToolbarGroup>
        <RichTextEditToolbarGroup>
            <RichTextEditToolbarButton Action="RichTextEditAction.Table" />
        </RichTextEditToolbarGroup>
    </Toolbar>
</RichTextEdit>
```

## Editor customization

### Theming

The  comes default with 2 themes  and . The  theme is a simple flat toolbar theme and the  theme is a tooltip based theme where the toolbar will be displayed in the tooltip.

See  for more information.

### Toolbar

The  toolbar can be completely customized. QuillJS defines a number of default actions that can be used through the  and  components

See  for more information.

### QuillJS Configuration

The  has the option to inject additional QuillJS configuration logic or load additional . Use the  property to indicate which javascript method needs to be called during initialization.

        If you for example want to change the way how links are sanitized you can use the following logic. Default all user typed url’s are relative to your pages base url. So when a user types  this will result in something like , but if you would probably like  then use the following configuration routine.

```
<RichTextEdit ConfigureQuillJsMethod="myComponent.configureQuillJs" />

@* Define this configuration in a javascript file
    window.myComponent = {
        configureQuillJs: () => {
            var link = Quill.import("formats/link");

            link.sanitize = url => {
                let newUrl = window.decodeURIComponent(url);
                newUrl = newUrl.trim().replace(/\s/g, "");

                if (/^(:\/\/)/.test(newUrl)) {
                    return `http${newUrl}`;
                }

                if (!/^(f|ht)tps?:\/\//i.test(newUrl)) {
                    return `http://${newUrl}`;
                }

                return newUrl;
            }
        }
    }
*@
```

## API

### Parameters

#### RichTextEdit

| Parameter              | Description                                                                                                  | Type              | Default                |
|------------------------|--------------------------------------------------------------------------------------------------------------|-------------------|------------------------|
| ConfigureQuillJsMethod | [Optional] The javascript method to call to configure additional QuillJs modules and or add custom bindings. | string            |                        |
| Editor                 | [Optional] Gets or sets the content visible in the editor.                                                   | RenderFragment    | null                   |
| PlaceHolder            | Place holder text visible in empty editor.                                                                   | string            |                        |
| ReadOnly               | Gets or sets a value indicating whether the editor is ReadOnly.                                              | bool              | false                  |
| SubmitOnEnter          | Call RichTextEdit.RichTextEdit.EnterPressed event when user presses the ENTER key.                           | bool              | false                  |
| Theme                  | The theme (Snow or Bubble) of the editor.Possible values:Snow, Bubble                                        | RichTextEditTheme | RichTextEditTheme.Snow |
| Toolbar                | [Optional] Gets or sets the content of the toolbar.                                                          | RenderFragment    | null                   |
| ToolbarPosition        | Toolbar placed on the top or bottom of the editor.Possible values:Top, Bottom, Start, End                    | Placement         | Top                    |

#### RichTextEditToolbarGroup

| Parameter    | Description                     | Type           | Default   |
|--------------|---------------------------------|----------------|-----------|
| ChildContent | Gets or sets the child content. | RenderFragment | null      |

#### RichTextEditToolbarButton

| Parameter   | Description                                         | Type                | Default   |
|-------------|-----------------------------------------------------|---------------------|-----------|
| Action      | Gets or sets the toolbar action.                    | RichTextEditAction? | null      |
| Value       | Gets or sets the value corresponding to the action. | string              |           |

#### RichTextEditToolbarSelect

| Parameter    | Description                     | Type                | Default   |
|--------------|---------------------------------|---------------------|-----------|
| Action       | Gets or sets the select action. | RichTextEditAction? | null      |
| ChildContent | Gets or sets the child content. | RenderFragment      | null      |

### Events

#### RichTextEdit

| Event          | Description                                                                                                                                          | Type          |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| ContentChanged | Occurs when the content within the editor changes.                                                                                                   | EventCallback |
| EditorBlur     | Occurs when the editor loses focus.                                                                                                                  | EventCallback |
| EditorFocus    | Occurs when the editor gains focus.                                                                                                                  | EventCallback |
| EnterPressed   | Occurs when the enter key is pressed within the editor.Remarks This event is triggered only when RichTextEdit.RichTextEdit.SubmitOnEnter is enabled. | EventCallback |

### Methods

#### RichTextEdit

| Method           | Description                                                   | Return            | Parameters       |
|------------------|---------------------------------------------------------------|-------------------|------------------|
| SetHtmlAsync     | Sets the editor content as HTML asynchronously.                     Remarks Improper handling of HTML can lead to cross-site scripting (XSS). Ensure that the HTML content is properly sanitized before setting it in the editor.                                                               | ValueTask         | string html      |
| GetHtmlAsync     | Gets the editor content as HTML asynchronously.               | ValueTask<string> |                  |
| SetDeltaAsync    | Sets the editor content as a Quill Delta JSON asynchronously.                     Remarks The Quill Delta format is a rich text format used by the Quill editor. See the official Quill.js documentation for more details.                                                               | ValueTask         | string deltaJson |
| GetDeltaAsync    | Gets the editor content as a Quill Delta JSON asynchronously. | ValueTask<string> |                  |
| SetTextAsync     | Sets the editor content as plain text asynchronously.         | ValueTask         | string text      |
| GetTextAsync     | Gets the editor content as plain text asynchronously.         | ValueTask<string> |                  |
| ClearAsync       | Clears the editor content asynchronously.                     | ValueTask         |                  |
| OnContentChanged | Javascript callback for when content changes.                 | Task              |                  |
| OnEnter          | Javascript callback for when enter is pressed.                | Task              |                  |
| OnEditorFocus    | Javascript callback for when editor get focus.                | Task              |                  |
| OnEditorBlur     | Javascript callback for when editor lost focus.               | Task              |                  |

###### On this page

#### 

## 