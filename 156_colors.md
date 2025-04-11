# Blazorise Colors API

Classes and structures for defining and managing color schemes in Blazorise applications.

The Blazorise Colors API provides developers with a comprehensive set of classes and structures to define and manage color
    schemes within Blazor applications. By utilizing this API, you can create consistent and customizable color palettes that
    enhance the visual appeal and user experience of your application.

## API

### Parameters

#### ThemeColor

| Parameter   | Description                    | Type                                | Default   |
|-------------|--------------------------------|-------------------------------------|-----------|
| Key         | Gets the color key.            | string                              |           |
| Name        | Gets the color display name.   | string                              |           |
| Shades      | Gets the list of color shades. | Dictionary<string, ThemeColorShade> | null      |

#### ThemeColorAmber

| Parameter   | Description                                        | Type            | Default                          |
|-------------|----------------------------------------------------|-----------------|----------------------------------|
| _100        | A very light shade of the amber theme color.       | ThemeColorShade | new( "100", "_100", "#ffecb3" )  |
| _200        | A light shade of the amber theme color.            | ThemeColorShade | new( "200", "_200", "#ffe082" )  |
| _300        | A medium-light shade of the amber theme color.     | ThemeColorShade | new( "300", "_300", "#ffd54f" )  |
| _400        | A medium shade of the amber theme color.           | ThemeColorShade | new( "400", "_400", "#ffca28" )  |
| _50         | The lightest shade of the amber theme color.       | ThemeColorShade | new( "50", "_50", "#fff8e1" )    |
| _500        | The base amber theme color shade.                  | ThemeColorShade | new( "500", "_500", "#ffc107" )  |
| _600        | A slightly darker shade of the amber theme color.  | ThemeColorShade | new( "600", "_600", "#ffb300" )  |
| _700        | A dark shade of the amber theme color.             | ThemeColorShade | new( "700", "_700", "#ffa000" )  |
| _800        | A very dark shade of the amber theme color.        | ThemeColorShade | new( "800", "_800", "#ff8f00" )  |
| _900        | The darkest shade of the amber theme color.        | ThemeColorShade | new( "900", "_900", "#ff6f00" )  |
| A100        | A bright variant of the amber theme color.         | ThemeColorShade | new( "A100", "A100", "#ffe57f" ) |
| A200        | A lighter accent shade of the amber theme color.   | ThemeColorShade | new( "A200", "A200", "#ffd740" ) |
| A400        | A strong accent shade of the amber theme color.    | ThemeColorShade | new( "A400", "A400", "#ffc400" ) |
| A700        | The darkest accent shade of the amber theme color. | ThemeColorShade | new( "A700", "A700", "#ffab00" ) |

#### ThemeColorBlue

| Parameter   | Description                                       | Type            | Default                          |
|-------------|---------------------------------------------------|-----------------|----------------------------------|
| _100        | A very light shade of the blue theme color.       | ThemeColorShade | new( "100", "_100", "#bbdefb" )  |
| _200        | A light shade of the blue theme color.            | ThemeColorShade | new( "200", "_200", "#90caf9" )  |
| _300        | A medium-light shade of the blue theme color.     | ThemeColorShade | new( "300", "_300", "#64b5f6" )  |
| _400        | A medium shade of the blue theme color.           | ThemeColorShade | new( "400", "_400", "#42a5f5" )  |
| _50         | The lightest shade of the blue theme color.       | ThemeColorShade | new( "50", "_50", "#e3f2fd" )    |
| _500        | The base blue theme color shade.                  | ThemeColorShade | new( "500", "_500", "#2196f3" )  |
| _600        | A slightly darker shade of the blue theme color.  | ThemeColorShade | new( "600", "_600", "#1e88e5" )  |
| _700        | A dark shade of the blue theme color.             | ThemeColorShade | new( "700", "_700", "#1976d2" )  |
| _800        | A very dark shade of the blue theme color.        | ThemeColorShade | new( "800", "_800", "#1565c0" )  |
| _900        | The darkest shade of the blue theme color.        | ThemeColorShade | new( "900", "_900", "#0d47a1" )  |
| A100        | A bright variant of the blue theme color.         | ThemeColorShade | new( "A100", "A100", "#82b1ff" ) |
| A200        | A lighter accent shade of the blue theme color.   | ThemeColorShade | new( "A200", "A200", "#448aff" ) |
| A400        | A strong accent shade of the blue theme color.    | ThemeColorShade | new( "A400", "A400", "#2979ff" ) |
| A700        | The darkest accent shade of the blue theme color. | ThemeColorShade | new( "A700", "A700", "#2962ff" ) |

#### ThemeColorBlueGray

| Parameter   | Description                                           | Type            | Default                         |
|-------------|-------------------------------------------------------|-----------------|---------------------------------|
| _100        | A very light shade of the blue-gray theme color.      | ThemeColorShade | new( "100", "_100", "#cfd8dc" ) |
| _200        | A light shade of the blue-gray theme color.           | ThemeColorShade | new( "200", "_200", "#b0bec5" ) |
| _300        | A medium-light shade of the blue-gray theme color.    | ThemeColorShade | new( "300", "_300", "#90a4ae" ) |
| _400        | A medium shade of the blue-gray theme color.          | ThemeColorShade | new( "400", "_400", "#78909c" ) |
| _50         | The lightest shade of the blue-gray theme color.      | ThemeColorShade | new( "50", "_50", "#eceff1" )   |
| _500        | The base blue-gray theme color shade.                 | ThemeColorShade | new( "500", "_500", "#607d8b" ) |
| _600        | A slightly darker shade of the blue-gray theme color. | ThemeColorShade | new( "600", "_600", "#546e7a" ) |
| _700        | A dark shade of the blue-gray theme color.            | ThemeColorShade | new( "700", "_700", "#455a64" ) |
| _800        | A very dark shade of the blue-gray theme color.       | ThemeColorShade | new( "800", "_800", "#37474f" ) |
| _900        | The darkest shade of the blue-gray theme color.       | ThemeColorShade | new( "900", "_900", "#263238" ) |

#### ThemeColorBrown

| Parameter   | Description                                       | Type            | Default                         |
|-------------|---------------------------------------------------|-----------------|---------------------------------|
| _100        | A very light shade of the brown theme color.      | ThemeColorShade | new( "100", "_100", "#d7ccc8" ) |
| _200        | A light shade of the brown theme color.           | ThemeColorShade | new( "200", "_200", "#bcaaa4" ) |
| _300        | A medium-light shade of the brown theme color.    | ThemeColorShade | new( "300", "_300", "#a1887f" ) |
| _400        | A medium shade of the brown theme color.          | ThemeColorShade | new( "400", "_400", "#8d6e63" ) |
| _50         | The lightest shade of the brown theme color.      | ThemeColorShade | new( "50", "_50", "#efebe9" )   |
| _500        | The base brown theme color shade.                 | ThemeColorShade | new( "500", "_500", "#795548" ) |
| _600        | A slightly darker shade of the brown theme color. | ThemeColorShade | new( "600", "_600", "#6d4c41" ) |
| _700        | A dark shade of the brown theme color.            | ThemeColorShade | new( "700", "_700", "#5d4037" ) |
| _800        | A very dark shade of the brown theme color.       | ThemeColorShade | new( "800", "_800", "#4e342e" ) |
| _900        | The darkest shade of the brown theme color.       | ThemeColorShade | new( "900", "_900", "#3e2723" ) |

#### ThemeColorCyan

| Parameter   | Description                                       | Type            | Default                          |
|-------------|---------------------------------------------------|-----------------|----------------------------------|
| _100        | A very light shade of the cyan theme color.       | ThemeColorShade | new( "100", "_100", "#b2ebf2" )  |
| _200        | A light shade of the cyan theme color.            | ThemeColorShade | new( "200", "_200", "#80deea" )  |
| _300        | A medium-light shade of the cyan theme color.     | ThemeColorShade | new( "300", "_300", "#4dd0e1" )  |
| _400        | A medium shade of the cyan theme color.           | ThemeColorShade | new( "400", "_400", "#26c6da" )  |
| _50         | The lightest shade of the cyan theme color.       | ThemeColorShade | new( "50", "_50", "#e0f7fa" )    |
| _500        | The base cyan theme color shade.                  | ThemeColorShade | new( "500", "_500", "#00bcd4" )  |
| _600        | A slightly darker shade of the cyan theme color.  | ThemeColorShade | new( "600", "_600", "#00acc1" )  |
| _700        | A dark shade of the cyan theme color.             | ThemeColorShade | new( "700", "_700", "#0097a7" )  |
| _800        | A very dark shade of the cyan theme color.        | ThemeColorShade | new( "800", "_800", "#00838f" )  |
| _900        | The darkest shade of the cyan theme color.        | ThemeColorShade | new( "900", "_900", "#006064" )  |
| A100        | A bright variant of the cyan theme color.         | ThemeColorShade | new( "A100", "A100", "#84ffff" ) |
| A200        | A lighter accent shade of the cyan theme color.   | ThemeColorShade | new( "A200", "A200", "#18ffff" ) |
| A400        | A strong accent shade of the cyan theme color.    | ThemeColorShade | new( "A400", "A400", "#00e5ff" ) |
| A700        | The darkest accent shade of the cyan theme color. | ThemeColorShade | new( "A700", "A700", "#00b8d4" ) |

#### ThemeColorDeepOrange

| Parameter   | Description                                              | Type            | Default                          |
|-------------|----------------------------------------------------------|-----------------|----------------------------------|
| _100        | A very light shade of the deep orange theme color.       | ThemeColorShade | new( "100", "_100", "#ffccbc" )  |
| _200        | A light shade of the deep orange theme color.            | ThemeColorShade | new( "200", "_200", "#ffab91" )  |
| _300        | A medium-light shade of the deep orange theme color.     | ThemeColorShade | new( "300", "_300", "#ff8a65" )  |
| _400        | A medium shade of the deep orange theme color.           | ThemeColorShade | new( "400", "_400", "#ff7043" )  |
| _50         | The lightest shade of the deep orange theme color.       | ThemeColorShade | new( "50", "_50", "#fbe9e7" )    |
| _500        | The base deep orange theme color shade.                  | ThemeColorShade | new( "500", "_500", "#ff5722" )  |
| _600        | A slightly darker shade of the deep orange theme color.  | ThemeColorShade | new( "600", "_600", "#f4511e" )  |
| _700        | A dark shade of the deep orange theme color.             | ThemeColorShade | new( "700", "_700", "#e64a19" )  |
| _800        | A very dark shade of the deep orange theme color.        | ThemeColorShade | new( "800", "_800", "#d84315" )  |
| _900        | The darkest shade of the deep orange theme color.        | ThemeColorShade | new( "900", "_900", "#bf360c" )  |
| A100        | A bright variant of the deep orange theme color.         | ThemeColorShade | new( "A100", "A100", "#ff9e80" ) |
| A200        | A lighter accent shade of the deep orange theme color.   | ThemeColorShade | new( "A200", "A200", "#ff6e40" ) |
| A400        | A strong accent shade of the deep orange theme color.    | ThemeColorShade | new( "A400", "A400", "#ff3d00" ) |
| A700        | The darkest accent shade of the deep orange theme color. | ThemeColorShade | new( "A700", "A700", "#dd2c00" ) |

#### ThemeColorDeepPurple

| Parameter   | Description                                              | Type            | Default                          |
|-------------|----------------------------------------------------------|-----------------|----------------------------------|
| _100        | A very light shade of the deep purple theme color.       | ThemeColorShade | new( "100", "_100", "#d1c4e9" )  |
| _200        | A light shade of the deep purple theme color.            | ThemeColorShade | new( "200", "_200", "#b39ddb" )  |
| _300        | A medium-light shade of the deep purple theme color.     | ThemeColorShade | new( "300", "_300", "#9575cd" )  |
| _400        | A medium shade of the deep purple theme color.           | ThemeColorShade | new( "400", "_400", "#7e57c2" )  |
| _50         | The lightest shade of the deep purple theme color.       | ThemeColorShade | new( "50", "_50", "#ede7f6" )    |
| _500        | The base deep purple theme color shade.                  | ThemeColorShade | new( "500", "_500", "#673ab7" )  |
| _600        | A slightly darker shade of the deep purple theme color.  | ThemeColorShade | new( "600", "_600", "#5e35b1" )  |
| _700        | A dark shade of the deep purple theme color.             | ThemeColorShade | new( "700", "_700", "#512da8" )  |
| _800        | A very dark shade of the deep purple theme color.        | ThemeColorShade | new( "800", "_800", "#4527a0" )  |
| _900        | The darkest shade of the deep purple theme color.        | ThemeColorShade | new( "900", "_900", "#311b92" )  |
| A100        | A bright variant of the deep purple theme color.         | ThemeColorShade | new( "A100", "A100", "#b388ff" ) |
| A200        | A lighter accent shade of the deep purple theme color.   | ThemeColorShade | new( "A200", "A200", "#7c4dff" ) |
| A400        | A strong accent shade of the deep purple theme color.    | ThemeColorShade | new( "A400", "A400", "#651fff" ) |
| A700        | The darkest accent shade of the deep purple theme color. | ThemeColorShade | new( "A700", "A700", "#6200ea" ) |

#### ThemeColorGray

| Parameter   | Description                                      | Type            | Default                         |
|-------------|--------------------------------------------------|-----------------|---------------------------------|
| _100        | A very light shade of the gray theme color.      | ThemeColorShade | new( "100", "_100", "#f5f5f5" ) |
| _200        | A light shade of the gray theme color.           | ThemeColorShade | new( "200", "_200", "#eee" )    |
| _300        | A medium-light shade of the gray theme color.    | ThemeColorShade | new( "300", "_300", "#e0e0e0" ) |
| _400        | A medium shade of the gray theme color.          | ThemeColorShade | new( "400", "_400", "#bdbdbd" ) |
| _50         | The lightest shade of the gray theme color.      | ThemeColorShade | new( "50", "_50", "#fafafa" )   |
| _500        | The base gray theme color shade.                 | ThemeColorShade | new( "500", "_500", "#9e9e9e" ) |
| _600        | A slightly darker shade of the gray theme color. | ThemeColorShade | new( "600", "_600", "#757575" ) |
| _700        | A dark shade of the gray theme color.            | ThemeColorShade | new( "700", "_700", "#616161" ) |
| _800        | A very dark shade of the gray theme color.       | ThemeColorShade | new( "800", "_800", "#424242" ) |
| _900        | The darkest shade of the gray theme color.       | ThemeColorShade | new( "900", "_900", "#212121" ) |

#### ThemeColorGreen

| Parameter   | Description                                        | Type            | Default                          |
|-------------|----------------------------------------------------|-----------------|----------------------------------|
| _100        | A very light shade of the green theme color.       | ThemeColorShade | new( "100", "_100", "#c8e6c9" )  |
| _200        | A light shade of the green theme color.            | ThemeColorShade | new( "200", "_200", "#a5d6a7" )  |
| _300        | A medium-light shade of the green theme color.     | ThemeColorShade | new( "300", "_300", "#81c784" )  |
| _400        | A medium shade of the green theme color.           | ThemeColorShade | new( "400", "_400", "#66bb6a" )  |
| _50         | The lightest shade of the green theme color.       | ThemeColorShade | new( "50", "_50", "#e8f5e9" )    |
| _500        | The base green theme color shade.                  | ThemeColorShade | new( "500", "_500", "#4caf50" )  |
| _600        | A slightly darker shade of the green theme color.  | ThemeColorShade | new( "600", "_600", "#43a047" )  |
| _700        | A dark shade of the green theme color.             | ThemeColorShade | new( "700", "_700", "#388e3c" )  |
| _800        | A very dark shade of the green theme color.        | ThemeColorShade | new( "800", "_800", "#2e7d32" )  |
| _900        | The darkest shade of the green theme color.        | ThemeColorShade | new( "900", "_900", "#1b5e20" )  |
| A100        | A bright variant of the green theme color.         | ThemeColorShade | new( "A100", "A100", "#b9f6ca" ) |
| A200        | A lighter accent shade of the green theme color.   | ThemeColorShade | new( "A200", "A200", "#69f0ae" ) |
| A400        | A strong accent shade of the green theme color.    | ThemeColorShade | new( "A400", "A400", "#00e676" ) |
| A700        | The darkest accent shade of the green theme color. | ThemeColorShade | new( "A700", "A700", "#00c853" ) |

#### ThemeColorIndigo

| Parameter   | Description                                         | Type            | Default                          |
|-------------|-----------------------------------------------------|-----------------|----------------------------------|
| _100        | A very light shade of the indigo theme color.       | ThemeColorShade | new( "100", "_100", "#c5cae9" )  |
| _200        | A light shade of the indigo theme color.            | ThemeColorShade | new( "200", "_200", "#9fa8da" )  |
| _300        | A medium-light shade of the indigo theme color.     | ThemeColorShade | new( "300", "_300", "#7986cb" )  |
| _400        | A medium shade of the indigo theme color.           | ThemeColorShade | new( "400", "_400", "#5c6bc0" )  |
| _50         | The lightest shade of the indigo theme color.       | ThemeColorShade | new( "50", "_50", "#e8eaf6" )    |
| _500        | The base indigo theme color shade.                  | ThemeColorShade | new( "500", "_500", "#3f51b5" )  |
| _600        | A slightly darker shade of the indigo theme color.  | ThemeColorShade | new( "600", "_600", "#3949ab" )  |
| _700        | A dark shade of the indigo theme color.             | ThemeColorShade | new( "700", "_700", "#303f9f" )  |
| _800        | A very dark shade of the indigo theme color.        | ThemeColorShade | new( "800", "_800", "#283593" )  |
| _900        | The darkest shade of the indigo theme color.        | ThemeColorShade | new( "900", "_900", "#1a237e" )  |
| A100        | A bright variant of the indigo theme color.         | ThemeColorShade | new( "A100", "A100", "#8c9eff" ) |
| A200        | A lighter accent shade of the indigo theme color.   | ThemeColorShade | new( "A200", "A200", "#536dfe" ) |
| A400        | A strong accent shade of the indigo theme color.    | ThemeColorShade | new( "A400", "A400", "#3d5afe" ) |
| A700        | The darkest accent shade of the indigo theme color. | ThemeColorShade | new( "A700", "A700", "#304ffe" ) |

#### ThemeColorLightBlue

| Parameter   | Description                                             | Type            | Default                          |
|-------------|---------------------------------------------------------|-----------------|----------------------------------|
| _100        | A very light shade of the light blue theme color.       | ThemeColorShade | new( "100", "_100", "#b3e5fc" )  |
| _200        | A light shade of the light blue theme color.            | ThemeColorShade | new( "200", "_200", "#81d4fa" )  |
| _300        | A medium-light shade of the light blue theme color.     | ThemeColorShade | new( "300", "_300", "#4fc3f7" )  |
| _400        | A medium shade of the light blue theme color.           | ThemeColorShade | new( "400", "_400", "#29b6f6" )  |
| _50         | The lightest shade of the light blue theme color.       | ThemeColorShade | new( "50", "_50", "#e1f5fe" )    |
| _500        | The base light blue theme color shade.                  | ThemeColorShade | new( "500", "_500", "#03a9f4" )  |
| _600        | A slightly darker shade of the light blue theme color.  | ThemeColorShade | new( "600", "_600", "#039be5" )  |
| _700        | A dark shade of the light blue theme color.             | ThemeColorShade | new( "700", "_700", "#0288d1" )  |
| _800        | A very dark shade of the light blue theme color.        | ThemeColorShade | new( "800", "_800", "#0277bd" )  |
| _900        | The darkest shade of the light blue theme color.        | ThemeColorShade | new( "900", "_900", "#01579b" )  |
| A100        | A bright variant of the light blue theme color.         | ThemeColorShade | new( "A100", "A100", "#80d8ff" ) |
| A200        | A lighter accent shade of the light blue theme color.   | ThemeColorShade | new( "A200", "A200", "#40c4ff" ) |
| A400        | A strong accent shade of the light blue theme color.    | ThemeColorShade | new( "A400", "A400", "#00b0ff" ) |
| A700        | The darkest accent shade of the light blue theme color. | ThemeColorShade | new( "A700", "A700", "#0091ea" ) |

#### ThemeColorLightGreen

| Parameter   | Description                                              | Type            | Default                          |
|-------------|----------------------------------------------------------|-----------------|----------------------------------|
| _100        | A very light shade of the light green theme color.       | ThemeColorShade | new( "100", "_100", "#dcedc8" )  |
| _200        | A light shade of the light green theme color.            | ThemeColorShade | new( "200", "_200", "#c5e1a5" )  |
| _300        | A medium-light shade of the light green theme color.     | ThemeColorShade | new( "300", "_300", "#aed581" )  |
| _400        | A medium shade of the light green theme color.           | ThemeColorShade | new( "400", "_400", "#9ccc65" )  |
| _50         | The lightest shade of the light green theme color.       | ThemeColorShade | new( "50", "_50", "#f1f8e9" )    |
| _500        | The base light green theme color shade.                  | ThemeColorShade | new( "500", "_500", "#8bc34a" )  |
| _600        | A slightly darker shade of the light green theme color.  | ThemeColorShade | new( "600", "_600", "#7cb342" )  |
| _700        | A dark shade of the light green theme color.             | ThemeColorShade | new( "700", "_700", "#689f38" )  |
| _800        | A very dark shade of the light green theme color.        | ThemeColorShade | new( "800", "_800", "#558b2f" )  |
| _900        | The darkest shade of the light green theme color.        | ThemeColorShade | new( "900", "_900", "#33691e" )  |
| A100        | A bright variant of the light green theme color.         | ThemeColorShade | new( "A100", "A100", "#ccff90" ) |
| A200        | A lighter accent shade of the light green theme color.   | ThemeColorShade | new( "A200", "A200", "#b2ff59" ) |
| A400        | A strong accent shade of the light green theme color.    | ThemeColorShade | new( "A400", "A400", "#76ff03" ) |
| A700        | The darkest accent shade of the light green theme color. | ThemeColorShade | new( "A700", "A700", "#64dd17" ) |

#### ThemeColorLime

| Parameter   | Description                                       | Type            | Default                          |
|-------------|---------------------------------------------------|-----------------|----------------------------------|
| _100        | A very light shade of the lime theme color.       | ThemeColorShade | new( "100", "_100", "#f0f4c3" )  |
| _200        | A light shade of the lime theme color.            | ThemeColorShade | new( "200", "_200", "#e6ee9c" )  |
| _300        | A medium-light shade of the lime theme color.     | ThemeColorShade | new( "300", "_300", "#dce775" )  |
| _400        | A medium shade of the lime theme color.           | ThemeColorShade | new( "400", "_400", "#d4e157" )  |
| _50         | The lightest shade of the lime theme color.       | ThemeColorShade | new( "50", "_50", "#f9fbe7" )    |
| _500        | The base lime theme color shade.                  | ThemeColorShade | new( "500", "_500", "#cddc39" )  |
| _600        | A slightly darker shade of the lime theme color.  | ThemeColorShade | new( "600", "_600", "#c0ca33" )  |
| _700        | A dark shade of the lime theme color.             | ThemeColorShade | new( "700", "_700", "#afb42b" )  |
| _800        | A very dark shade of the lime theme color.        | ThemeColorShade | new( "800", "_800", "#9e9d24" )  |
| _900        | The darkest shade of the lime theme color.        | ThemeColorShade | new( "900", "_900", "#827717" )  |
| A100        | A bright variant of the lime theme color.         | ThemeColorShade | new( "A100", "A100", "#f4ff81" ) |
| A200        | A lighter accent shade of the lime theme color.   | ThemeColorShade | new( "A200", "A200", "#eeff41" ) |
| A400        | A strong accent shade of the lime theme color.    | ThemeColorShade | new( "A400", "A400", "#c6ff00" ) |
| A700        | The darkest accent shade of the lime theme color. | ThemeColorShade | new( "A700", "A700", "#aeea00" ) |

#### ThemeColorOrange

| Parameter   | Description                                         | Type            | Default                          |
|-------------|-----------------------------------------------------|-----------------|----------------------------------|
| _100        | A very light shade of the orange theme color.       | ThemeColorShade | new( "100", "_100", "#ffe0b2" )  |
| _200        | A light shade of the orange theme color.            | ThemeColorShade | new( "200", "_200", "#ffcc80" )  |
| _300        | A medium-light shade of the orange theme color.     | ThemeColorShade | new( "300", "_300", "#ffb74d" )  |
| _400        | A medium shade of the orange theme color.           | ThemeColorShade | new( "400", "_400", "#ffa726" )  |
| _50         | The lightest shade of the orange theme color.       | ThemeColorShade | new( "50", "_50", "#fff3e0" )    |
| _500        | The base orange theme color shade.                  | ThemeColorShade | new( "500", "_500", "#ff9800" )  |
| _600        | A slightly darker shade of the orange theme color.  | ThemeColorShade | new( "600", "_600", "#fb8c00" )  |
| _700        | A dark shade of the orange theme color.             | ThemeColorShade | new( "700", "_700", "#f57c00" )  |
| _800        | A very dark shade of the orange theme color.        | ThemeColorShade | new( "800", "_800", "#ef6c00" )  |
| _900        | The darkest shade of the orange theme color.        | ThemeColorShade | new( "900", "_900", "#e65100" )  |
| A100        | A bright variant of the orange theme color.         | ThemeColorShade | new( "A100", "A100", "#ffd180" ) |
| A200        | A lighter accent shade of the orange theme color.   | ThemeColorShade | new( "A200", "A200", "#ffab40" ) |
| A400        | A strong accent shade of the orange theme color.    | ThemeColorShade | new( "A400", "A400", "#ff9100" ) |
| A700        | The darkest accent shade of the orange theme color. | ThemeColorShade | new( "A700", "A700", "#ff6d00" ) |

#### ThemeColorPink

| Parameter   | Description                                       | Type            | Default                          |
|-------------|---------------------------------------------------|-----------------|----------------------------------|
| _100        | A very light shade of the pink theme color.       | ThemeColorShade | new( "100", "_100", "#f8bbd0" )  |
| _200        | A light shade of the pink theme color.            | ThemeColorShade | new( "200", "_200", "#f48fb1" )  |
| _300        | A medium-light shade of the pink theme color.     | ThemeColorShade | new( "300", "_300", "#f06292" )  |
| _400        | A medium shade of the pink theme color.           | ThemeColorShade | new( "400", "_400", "#ec407a" )  |
| _50         | The lightest shade of the pink theme color.       | ThemeColorShade | new( "50", "_50", "#fce4ec" )    |
| _500        | The base pink theme color shade.                  | ThemeColorShade | new( "500", "_500", "#e91e63" )  |
| _600        | A slightly darker shade of the pink theme color.  | ThemeColorShade | new( "600", "_600", "#d81b60" )  |
| _700        | A dark shade of the pink theme color.             | ThemeColorShade | new( "700", "_700", "#c2185b" )  |
| _800        | A very dark shade of the pink theme color.        | ThemeColorShade | new( "800", "_800", "#ad1457" )  |
| _900        | The darkest shade of the pink theme color.        | ThemeColorShade | new( "900", "_900", "#880e4f" )  |
| A100        | A bright variant of the pink theme color.         | ThemeColorShade | new( "A100", "A100", "#ff80ab" ) |
| A200        | A lighter accent shade of the pink theme color.   | ThemeColorShade | new( "A200", "A200", "#ff4081" ) |
| A400        | A strong accent shade of the pink theme color.    | ThemeColorShade | new( "A400", "A400", "#f50057" ) |
| A700        | The darkest accent shade of the pink theme color. | ThemeColorShade | new( "A700", "A700", "#c51162" ) |

#### ThemeColorPurple

| Parameter   | Description                                         | Type            | Default                          |
|-------------|-----------------------------------------------------|-----------------|----------------------------------|
| _100        | A very light shade of the purple theme color.       | ThemeColorShade | new( "100", "_100", "#e1bee7" )  |
| _200        | A light shade of the purple theme color.            | ThemeColorShade | new( "200", "_200", "#ce93d8" )  |
| _300        | A medium-light shade of the purple theme color.     | ThemeColorShade | new( "300", "_300", "#ba68c8" )  |
| _400        | A medium shade of the purple theme color.           | ThemeColorShade | new( "400", "_400", "#ab47bc" )  |
| _50         | The lightest shade of the purple theme color.       | ThemeColorShade | new( "50", "_50", "#f3e5f5" )    |
| _500        | The base purple theme color shade.                  | ThemeColorShade | new( "500", "_500", "#9c27b0" )  |
| _600        | A slightly darker shade of the purple theme color.  | ThemeColorShade | new( "600", "_600", "#8e24aa" )  |
| _700        | A dark shade of the purple theme color.             | ThemeColorShade | new( "700", "_700", "#7b1fa2" )  |
| _800        | A very dark shade of the purple theme color.        | ThemeColorShade | new( "800", "_800", "#6a1b9a" )  |
| _900        | The darkest shade of the purple theme color.        | ThemeColorShade | new( "900", "_900", "#4a148c" )  |
| A100        | A bright variant of the purple theme color.         | ThemeColorShade | new( "A100", "A100", "#ea80fc" ) |
| A200        | A lighter accent shade of the purple theme color.   | ThemeColorShade | new( "A200", "A200", "#e040fb" ) |
| A400        | A strong accent shade of the purple theme color.    | ThemeColorShade | new( "A400", "A400", "#d500f9" ) |
| A700        | The darkest accent shade of the purple theme color. | ThemeColorShade | new( "A700", "A700", "#a0f" )    |

#### ThemeColorRed

| Parameter   | Description                                      | Type            | Default                          |
|-------------|--------------------------------------------------|-----------------|----------------------------------|
| _100        | A very light shade of the red theme color.       | ThemeColorShade | new( "100", "_100", "#ffcdd2" )  |
| _200        | A light shade of the red theme color.            | ThemeColorShade | new( "200", "_200", "#ef9a9a" )  |
| _300        | A medium-light shade of the red theme color.     | ThemeColorShade | new( "300", "_300", "#e57373" )  |
| _400        | A medium shade of the red theme color.           | ThemeColorShade | new( "400", "_400", "#ef5350" )  |
| _50         | The lightest shade of the red theme color.       | ThemeColorShade | new( "50", "_50", "#ffebee" )    |
| _500        | The base red theme color shade.                  | ThemeColorShade | new( "500", "_500", "#f44336" )  |
| _600        | A slightly darker shade of the red theme color.  | ThemeColorShade | new( "600", "_600", "#e53935" )  |
| _700        | A dark shade of the red theme color.             | ThemeColorShade | new( "700", "_700", "#d32f2f" )  |
| _800        | A very dark shade of the red theme color.        | ThemeColorShade | new( "800", "_800", "#c62828" )  |
| _900        | The darkest shade of the red theme color.        | ThemeColorShade | new( "900", "_900", "#b71c1c" )  |
| A100        | A bright variant of the red theme color.         | ThemeColorShade | new( "A100", "A100", "#ff8a80" ) |
| A200        | A lighter accent shade of the red theme color.   | ThemeColorShade | new( "A200", "A200", "#ff5252" ) |
| A400        | A strong accent shade of the red theme color.    | ThemeColorShade | new( "A400", "A400", "#ff1744" ) |
| A700        | The darkest accent shade of the red theme color. | ThemeColorShade | new( "A700", "A700", "#d50000" ) |

#### ThemeColors

| Parameter   | Description                                | Type                           | Default   |
|-------------|--------------------------------------------|--------------------------------|-----------|
| Amber       | Gets the theme ThemeColorAmber color.      | ThemeColorAmber                | null      |
| Blue        | Gets the theme ThemeColorBlue color.       | ThemeColorBlue                 | null      |
| BlueGray    | Gets the theme ThemeColorBlueGray color.   | ThemeColorBlueGray             | null      |
| Brown       | Gets the theme ThemeColorBrown color.      | ThemeColorBrown                | null      |
| Cyan        | Gets the theme ThemeColorCyan color.       | ThemeColorCyan                 | null      |
| DeepOrange  | Gets the theme ThemeColorDeepOrange color. | ThemeColorDeepOrange           | null      |
| DeepPurple  | Gets the theme ThemeColorDeepPurple color. | ThemeColorDeepPurple           | null      |
| Gray        | Gets the theme ThemeColorGray color.       | ThemeColorGray                 | null      |
| Green       | Gets the theme ThemeColorGreen color.      | ThemeColorGreen                | null      |
| Indigo      | Gets the theme ThemeColorIndigo color.     | ThemeColorIndigo               | null      |
| Items       | Gets or sets the map of all theme colors.  | Dictionary<string, ThemeColor> | null      |
| LightBlue   | Gets the theme ThemeColorLightBlue color.  | ThemeColorLightBlue            | null      |
| LightGreen  | Gets the theme ThemeColorLightGreen color. | ThemeColorLightGreen           | null      |
| Lime        | Gets the theme ThemeColorLime color.       | ThemeColorLime                 | null      |
| Orange      | Gets the theme ThemeColorOrange color.     | ThemeColorOrange               | null      |
| Pink        | Gets the theme ThemeColorPink color.       | ThemeColorPink                 | null      |
| Purple      | Gets the theme ThemeColorPurple color.     | ThemeColorPurple               | null      |
| Red         | Gets the theme ThemeColorRed color.        | ThemeColorRed                  | null      |
| Teal        | Gets the theme ThemeColorTeal color.       | ThemeColorTeal                 | null      |
| Yellow      | Gets the theme ThemeColorYellow color.     | ThemeColorYellow               | null      |

#### ThemeColorShade

| Parameter   | Description                  | Type   | Default   |
|-------------|------------------------------|--------|-----------|
| Key         | Gets the shade key.          | string |           |
| Name        | Gets the shade display name. | string |           |
| Value       | Gets the shade color.        | string |           |

#### ThemeColorTeal

| Parameter   | Description                                       | Type            | Default                          |
|-------------|---------------------------------------------------|-----------------|----------------------------------|
| _100        | A very light shade of the teal theme color.       | ThemeColorShade | new( "100", "_100", "#b2dfdb" )  |
| _200        | A light shade of the teal theme color.            | ThemeColorShade | new( "200", "_200", "#80cbc4" )  |
| _300        | A medium-light shade of the teal theme color.     | ThemeColorShade | new( "300", "_300", "#4db6ac" )  |
| _400        | A medium shade of the teal theme color.           | ThemeColorShade | new( "400", "_400", "#26a69a" )  |
| _50         | The lightest shade of the teal theme color.       | ThemeColorShade | new( "50", "_50", "#e0f2f1" )    |
| _500        | The base teal theme color shade.                  | ThemeColorShade | new( "500", "_500", "#009688" )  |
| _600        | A slightly darker shade of the teal theme color.  | ThemeColorShade | new( "600", "_600", "#00897b" )  |
| _700        | A dark shade of the teal theme color.             | ThemeColorShade | new( "700", "_700", "#00796b" )  |
| _800        | A very dark shade of the teal theme color.        | ThemeColorShade | new( "800", "_800", "#00695c" )  |
| _900        | The darkest shade of the teal theme color.        | ThemeColorShade | new( "900", "_900", "#004d40" )  |
| A100        | A bright variant of the teal theme color.         | ThemeColorShade | new( "A100", "A100", "#a7ffeb" ) |
| A200        | A lighter accent shade of the teal theme color.   | ThemeColorShade | new( "A200", "A200", "#64ffda" ) |
| A400        | A strong accent shade of the teal theme color.    | ThemeColorShade | new( "A400", "A400", "#1de9b6" ) |
| A700        | The darkest accent shade of the teal theme color. | ThemeColorShade | new( "A700", "A700", "#00bfa5" ) |

#### ThemeColorYellow

| Parameter   | Description                                         | Type            | Default                          |
|-------------|-----------------------------------------------------|-----------------|----------------------------------|
| _100        | A very light shade of the yellow theme color.       | ThemeColorShade | new( "100", "_100", "#fff9c4" )  |
| _200        | A light shade of the yellow theme color.            | ThemeColorShade | new( "200", "_200", "#fff59d" )  |
| _300        | A medium-light shade of the yellow theme color.     | ThemeColorShade | new( "300", "_300", "#fff176" )  |
| _400        | A medium shade of the yellow theme color.           | ThemeColorShade | new( "400", "_400", "#ffee58" )  |
| _50         | The lightest shade of the yellow theme color.       | ThemeColorShade | new( "50", "_50", "#fffde7" )    |
| _500        | The base yellow theme color shade.                  | ThemeColorShade | new( "500", "_500", "#ffeb3b" )  |
| _600        | A slightly darker shade of the yellow theme color.  | ThemeColorShade | new( "600", "_600", "#fdd835" )  |
| _700        | A dark shade of the yellow theme color.             | ThemeColorShade | new( "700", "_700", "#fbc02d" )  |
| _800        | A very dark shade of the yellow theme color.        | ThemeColorShade | new( "800", "_800", "#f9a825" )  |
| _900        | The darkest shade of the yellow theme color.        | ThemeColorShade | new( "900", "_900", "#f57f17" )  |
| A100        | A bright variant of the yellow theme color.         | ThemeColorShade | new( "A100", "A100", "#ffff8d" ) |
| A200        | A lighter accent shade of the yellow theme color.   | ThemeColorShade | new( "A200", "A200", "#ff0" )    |
| A400        | A strong accent shade of the yellow theme color.    | ThemeColorShade | new( "A400", "A400", "#ffea00" ) |
| A700        | The darkest accent shade of the yellow theme color. | ThemeColorShade | new( "A700", "A700", "#ffd600" ) |

###### On this page

#### 

## 