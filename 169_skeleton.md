# Blazorise Skeleton component

Use loading placeholders for your components or pages to indicate something may still be loading.

Skeletons can be used to enhance the experience of your application. They are used to indicate that something is still loading or that the content is not yet available.

## Structure

- &lt; Skeleton&gt; The main container, used to define the skeleton layout.
- &lt;Skeleton&gt; The main container, used to define the skeleton layout.
    - &lt;SkeletonItem&gt; used to define the size of the skeleton element.

## Examples

### Basic

The most basic skeleton example.

```
<Skeleton>
    <SkeletonItem ColumnSize="ColumnSize.Is6" />
</Skeleton>
```

### Pulse Animation

A skeleton with a pulse animation to better convey the perception of something being actively loaded.

```
<Skeleton Animation="SkeletonAnimation.Pulse">
    <SkeletonItem ColumnSize="ColumnSize.Is7" />
    <SkeletonItem ColumnSize="ColumnSize.Is4" />
    <SkeletonItem ColumnSize="ColumnSize.Is4" />
    <SkeletonItem ColumnSize="ColumnSize.Is6" />
    <SkeletonItem ColumnSize="ColumnSize.Is8" />
</Skeleton>
```

### Wave Animation

A skeleton with a wave animation to better convey the perception of something being actively loaded.

```
<Skeleton Animation="SkeletonAnimation.Wave">
    <SkeletonItem ColumnSize="ColumnSize.Is7" />
    <SkeletonItem ColumnSize="ColumnSize.Is4" />
    <SkeletonItem ColumnSize="ColumnSize.Is4" />
    <SkeletonItem ColumnSize="ColumnSize.Is6" />
    <SkeletonItem ColumnSize="ColumnSize.Is8" />
</Skeleton>
```

### Table

allows you to scaffold a basic table structure by utilizing the  and  parameters to define the size of the table.

|    |    |    |    |
|----|----|----|----|
|    |    |    |    |
|    |    |    |    |
|    |    |    |    |
|    |    |    |    |
|    |    |    |    |

```
<SkeletonTable Rows="5" Columns="4" />
```

## Best Practices

### Do

Use Skeleton to help ease a UI transition when we know the service will potentially take a longer amount of time to retrieve the data.
Provide size for each of the Skeleton elements you used to build a skeleton layout looking as close as possible to real content it is replacing.
Use Skeleton if you know the UI loading time is longer than 1 second.

### Don't

Build Skeleton UI with a lot of details. Circles and rectangles are really as detailed as you want to get. Adding more detail will result in confusion once the UI loads.
Use Skeleton if you are confident that the UI will take less than a second to load.

## API

### Parameters

#### Skeleton

| Parameter    | Description                                                                                   | Type              | Default                   |
|--------------|-----------------------------------------------------------------------------------------------|-------------------|---------------------------|
| Animation    | Gets or sets the animation style applied to the skeleton.Possible values:Default, Wave, Pulse | SkeletonAnimation | SkeletonAnimation.Default |
| ChildContent | Gets or sets the child content to be rendered inside the skeleton component.                  | RenderFragment    | null                      |

#### SkeletonItem

| Parameter    | Description                                                                       | Type           | Default   |
|--------------|-----------------------------------------------------------------------------------|----------------|-----------|
| ChildContent | Gets or sets the child content to be rendered inside the skeleton item component. | RenderFragment | null      |
| ColumnSize   | Gets or sets the column size configuration for the skeleton item.                 | IFluentColumn  | null      |

#### SkeletonTable

| Parameter    | Description                                                                              | Type              | Default                   |
|--------------|------------------------------------------------------------------------------------------|-------------------|---------------------------|
| Animation    | Defined the animation style applied to the skeleton.Possible values:Default, Wave, Pulse | SkeletonAnimation | SkeletonAnimation.Default |
| ChildContent | Specifies the content to be rendered inside this Skeleton.                               | RenderFragment    | null                      |
| Columns      | Specifies the number of columns to be rendered. Default is 5.                            | int               | 5                         |
| Rows         | Specifies the number of rows to be rendered. Default is 3.                               | int               | 3                         |

###### On this page

#### 

## 