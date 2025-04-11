# Blazorise SpinKit component

A component used to show loading indicators animated with CSS.

## Installation

### NuGet

Install extension from NuGet.

```
Install-Package Blazorise.SpinKit
```

### Imports

In your main  add:

```
@using Blazorise.SpinKit
```

### Static files

Include CSS link into your  or  /  file, depending if you’re using a Blazor WebAssembly or Blazor Server side project.

```
<link href="_content/Blazorise.SpinKit/blazorise.spinkit.css" rel="stylesheet" />
```

### Basic example

A basic spinner with default settings.

```
<SpinKit Type="SpinKitType.Plane" />
```

### Color

The color can be changed with HEX value.

```
<SpinKit Type="SpinKitType.Plane" Color="#ff4a3d" />
```

### Size

Size can be changed using any unit type. In this example we’re using .

```
<SpinKit Type="SpinKitType.Plane" Size="20px" />
```

## API

### Parameters

| Parameter   | Description                                                                                                                          | Type        | Default           |
|-------------|--------------------------------------------------------------------------------------------------------------------------------------|-------------|-------------------|
| Centered    | Position the spinner to the center of it's container.                                                                                | bool        | false             |
| Color       | Gets or sets the spinner color.                                                                                                      | string      |                   |
| Size        | Gets or sets the spinner size.                                                                                                       | string      |                   |
| Type        | Gets or sets the spinner type.Possible values:Plane, Chase, Bounce, Wave, Pulse, Flow, Swing, Circle, CircleFade, Grid, Fold, Wander | SpinKitType | SpinKitType.Plane |

###### On this page

#### 

## 