# Blazorise Layout system

Handling the overall layout of a page.

The &lt;Layout&gt; is a component for building common application layouts.

The layout consists of four diferent sections: a horizontal navigation bar (LayoutHeader), a collapsible navigation sidebar (LayoutSider) and a content area (LayoutContent). An applicationss main navigation blocks should be positioned in the navbar and/or sidebar, whereas views are rendered in the content area.

Layout is responsive and adjusts automatically to fit desktop, tablet, and mobile screen sizes.

- &lt; Layout&gt; The main container.
- &lt;Layout&gt; The main container.
    - &lt;LayoutHeader&gt; The top container for a Bar or navigation.
    - &lt;LayoutContent&gt; The main content area.
    - &lt;LayoutFooter&gt; The bottom container for a Bar or navigation.
    - &lt; LayoutSider&gt; The sidebar container.
    - &lt;LayoutSider&gt; The sidebar container.
        - &lt;LayoutSiderContent&gt; The main content area of the sidebar.

## Examples

### Basic

```
<Layout>
    <LayoutHeader>
        Header
    </LayoutHeader>
    <LayoutContent>
        Content
    </LayoutContent>
    <LayoutFooter>
        Footer
    </LayoutFooter>
</Layout>
```

### Sider with Header on top

The LayoutHeader can be located on top or to the side of the drawer.

When put on top, the LayoutHeader is typically used as an application header. Application headers contain, for example, the application's name and branding, as well as actions that apply to the entire application, such as notifications, settings, etc.

Sider

```
<Layout>
    <LayoutHeader Fixed>
        Header
    </LayoutHeader>
    <Layout Sider>
        <LayoutSider>
            <LayoutSiderContent>
                Sider
            </LayoutSiderContent>
        </LayoutSider>
        <Layout>
            <LayoutContent>
                Content
            </LayoutContent>
        </Layout>
    </Layout>
</Layout>
```

### With Sider

When placed to the side, the  is often seen as a view header, housing the view's title, and actions and secondary navigation that relate only to the current view.

Sider

```
<Layout Sider>
    <LayoutSider>
        <LayoutSiderContent>
            Sider
        </LayoutSiderContent>
    </LayoutSider>
    <Layout>
        <LayoutHeader Fixed>
            Header
        </LayoutHeader>
        <LayoutContent>
            Content
        </LayoutContent>
    </Layout>
</Layout>
```

## API

### Parameters

#### Layout

| Parameter       | Description                                                                               | Type           | Default   |
|-----------------|-------------------------------------------------------------------------------------------|----------------|-----------|
| ChildContent    | Specifies the content to be rendered inside this Layout.                                  | RenderFragment | null      |
| Loading         | If true, an overlay will be created so the user cannot click anything until set to false. | bool           | false     |
| LoadingClass    | Sets the custom classname for loading element.                                            | string         |           |
| LoadingTemplate | Specifies the content to be rendered the loading container.                               | RenderFragment | null      |
| Sider           | Indicates that layout will contain sider container.                                       | bool           | false     |

#### LayoutHeader

| Parameter    | Description                                                    | Type           | Default   |
|--------------|----------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this LayoutHeader. | RenderFragment | null      |
| Fixed        | If true header will be fixed to the top of the page.           | bool           | false     |

#### LayoutFooter

| Parameter    | Description                                                    | Type           | Default   |
|--------------|----------------------------------------------------------------|----------------|-----------|
| ChildContent | Specifies the content to be rendered inside this LayoutFooter. | RenderFragment | null      |
| Fixed        | If true footer will be fixed to the bottom of the page.        | bool           | false     |

### Events

#### Layout

| Event          | Description                            | Type                |
|----------------|----------------------------------------|---------------------|
| LoadingChanged | Occurs when loading state had changed. | EventCallback<bool> |

###### On this page

#### 

## 