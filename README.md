# chartjs-plugin-zoom

A zoom and pan plugin for Chart.js >= 3.0.0

For Chart.js 2.6.0 to 2.9.x support, use [version 0.7.7 of this plugin](https://github.com/chartjs/chartjs-plugin-zoom/releases/tag/v0.7.7).

Panning can be done via the mouse or with a finger.
Zooming is done via the mouse wheel or via a pinch gesture. [Hammer.js](https://hammerjs.github.io/) is used for gesture recognition.

[Live Codepen Demo](https://codepen.io/jledentu/pen/NWWZryv)

## Installation

Run `npm install --save chartjs-plugin-zoom` to install with `npm`.

If including via a `<script>` tag, make sure to include `Hammer.js` as well:

```html
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script src="https://cdn.jsdelivr.net/npm/hammerjs@2.0.8"></script>
<script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-zoom@next"></script>
```

## Configuration

To configure the zoom and pan plugin, you can simply add new config options to your chart config.

```javascript
plugins: {
 zoom: {
  // Container for pan options
  pan: {
   // Boolean to enable panning
   enabled: true,

   // Panning directions. Remove the appropriate direction to disable
   // Eg. 'y' would only allow panning in the y direction
   // A function that is called as the user is panning and returns the
   // available directions can also be used:
   //   mode: function({ chart }) {
   //     return 'xy';
   //   },
   mode: 'xy',

   // Which of the enabled panning directions should only be available
   // when the mouse cursor is over one of scale.
   overScaleMode: 'xy',

   rangeMin: {
    // Format of min pan range depends on scale type
    x: null,
    y: null
   },
   rangeMax: {
    // Format of max pan range depends on scale type
    x: null,
    y: null
   },

   // On category scale, factor of pan velocity
   speed: 20,

   // Minimal pan distance required before actually applying pan
   threshold: 10,

   // Function called while the user is panning
   onPan: function({chart}) { console.log(`I'm panning!!!`); },
   // Function called once panning is completed
   onPanComplete: function({chart}) { console.log(`I was panned!!!`); },
   // Function called when pan fails because modifier key was not detected.
   // event is the a hammer event that failed - see https://hammerjs.github.io/api#event-object
   onPanRejected: function({chart, event}) { console.log(`I didn't start panning!`); }
  },

  // Container for zoom options
  zoom: {
   // Boolean to enable zooming
   enabled: true,

   // Enable drag-to-zoom behavior
   drag: true,

   // Drag-to-zoom effect can be customized
   // drag: {
   //   borderColor: 'rgba(225,225,225,0.3)'
   //   borderWidth: 5,
   //   backgroundColor: 'rgb(225,225,225)',
   //   animationDuration: 0
   // },

   // Zooming directions. Remove the appropriate direction to disable
   // Eg. 'y' would only allow zooming in the y direction
   // A function that is called as the user is zooming and returns the
   // available directions can also be used:
   //   mode: function({ chart }) {
   //     return 'xy';
   //   },
   mode: 'xy',

   // Which of the enabled zooming directions should only be available
   // when the mouse cursor is over one of scale.
   overScaleMode: 'xy',

   rangeMin: {
    // Format of min zoom range depends on scale type
    x: null,
    y: null
   },
   rangeMax: {
    // Format of max zoom range depends on scale type
    x: null,
    y: null
   },

   // Speed of zoom via mouse wheel
   // (percentage of zoom on a wheel event)
   speed: 0.1,

   // Minimal zoom distance required before actually applying zoom
   threshold: 2,

   // On category scale, minimal zoom level before actually applying zoom
   sensitivity: 3,

   // Function called while the user is zooming
   onZoom: function({chart}) { console.log(`I'm zooming!!!`); },
   // Function called once zooming is completed
   onZoomComplete: function({chart}) { console.log(`I was zoomed!!!`); },
   // Function called when wheel input occurs without modifier key
   onZoomRejected: function({chart, event}) { console.log(`I didn't start zooming!`); }
  }
 }
}
```

## API

### chart.resetZoom()

Programmatically resets the zoom to the default state. See [samples/zoom-time.html](samples/zoom-time.html) for an example.

## Documentation

You can find documentation for Chart.js at [www.chartjs.org/docs](https://www.chartjs.org/docs).

Examples for this plugin are available in the [samples folder](samples).

Prior to v0.4.0, this plugin was known as 'Chart.Zoom.js'. Old versions are still available on npm under that name.

## Contributing

Before submitting an issue or a pull request to the project, please take a moment to look over the [contributing guidelines](CONTRIBUTING.md) first.

## License

chartjs-plugin-zoom.js is available under the [MIT license](https://opensource.org/licenses/MIT).
