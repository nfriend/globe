# world-map

A web page that displays a world map, configured by data passed through the URL.

## Usage

To use this map, link to https://world-map.nathanfriend.io with any of the URL hash parameters in the table below. Note that all hash parameter keys must be lowercase (e.g. `us_color`, _not_ `US_color`).

There are two main ways to color the map:

1. **Explicit colors:** specific colors are provided for each country using URL parameters like `us_color=red&ca_color=blue`.
1. **Calculated colors:** numerical values are provided for each country using URL parameters like `us_value=5&ca_value=1`. The map will automatically determine the color of each country based on where it falls in the range of provided values.

These options can be used together; when a country has both a `_value` and a `_color` parameter provided, the `_color` parameter takes precedence.

### URL parameter reference

| Parameter                         | Default             | Example                                     | Description                                                                                                                                                                                                                                 |
| --------------------------------- | ------------------- | ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `<two-letter country code>_color` | none                | `us_color=red`                              | Renders this country with the provided color. Color can be any valid CSS color (i.e. `red`, `#ff0000`, and `rgba(255, 0, 0, 1)` are all valid). Note that the value must be URL encoded; for example, to specific `#ff0000` as `%23ff0000`. |
| `default_color`                   | `gray`              | `default_color=pink`                        | The default country color.                                                                                                                                                                                                                  |
| `<two-letter country code>_label` | none                | `mx_label=Population: 126.7 million (2021)` | The label text to render when the country is hovered.                                                                                                                                                                                       |
| `default_label`                   | none                | `default_label=No data`                     | The label text to render for countries that have no specific label text provided.                                                                                                                                                           |
| `<two-letter country code>_value` | none                | `ca_value=4.5`                              | The numerical value to assign to this country. The map will automatically determine the country's color based on this value's relative size compared to all other provided country values.                                                  |
| `default_value`                   | `0`                 | `default_value=1.2`                         | The numerical value to assign to all countries that have no specific value provided.                                                                                                                                                        |
| `interpolate_fn`                  | `interpolateYlOrRd` | `interpolate_fn=interpolateRainbow`         | The D3 color interpolation function to use when calculating the color of each country. (Only relevant when using the `<country code>_value` parameters.) See https://github.com/d3/d3-scale-chromatic for a list of all options.            |
| `background`                      | none                | `background=white`                          | A solid color to set as the background. If not provided, an image of a starry sky is used instead.                                                                                                                                          |
| `globe_style`                     | `day`               | `globe_style=hollow`                        | The style to use when rendering the globe. Valid options are `night`, `day`, or `hollow`.                                                                                                                                                   |
| `hover_lift`                      | `0.02`              | `hover_lift=0.5`                            | How high to lift the country when hovered.                                                                                                                                                                                                  |

## Source

This is more-or-less a copy/paste of the ["Choropleth" example](https://github.com/vasturiano/globe.gl/blob/master/example/choropleth-countries/index.html) from [globe.gl](https://globe.gl/), with some additional logic to allow configuration of some properties through the URL.

## Attributions

- [Favicon image by macrovector](https://www.freepik.com/free-vector/globe-earth-world-icons-vector-white-black_10601425.htm#query=globe%20icon&position=0&from_view=search&track=ais) on Freepik

## Developing

- `npm install --global http-server`
- Run `http-server` at the root of the project
