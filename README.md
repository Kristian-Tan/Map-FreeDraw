# Map FreeDraw

## Dependency
- Leaflet
- mapbox
- jQuery

## Feature
- Draw marker, circle, line and polygon on map
- Save (and load) drawings to JSON file
- Frame-by-frame animation

## Concept
- Frame: condition of whole map in a set of time
- Animation: multiple frame being played in 1 second interval

### Drawable Objects
- Marker, parameters: coordinate, color (optional), label (optional)
- Circle, parameters: center coordinate, radius, label (optional), fillcolor (optional), linecolor (optional)
- Polyline (line), parameters: coordinates, linecolor (optional)
- Polygon, parameters: coordinates, fillcolor (optional), linecolor (optional)


## Drawing Guide

### Manual Draw
- Enter the parameter of desired drawable object in html input form
- Click ```Add to Frame``` button

### Mouse Shortcuts
- Clicking on map will set ```marker's coordinate```, ```circle's center coordinate```, ```polyline's next vertex```, and ```polygon's next vertex``` html input form to clicked coordinate position

### Keyboard Shortcuts
- Keyboard shortcuts work by mapping a keyboard key code to specific button's trigger event (click event)
- To customize keyboard shortcuts, change key binding in ```Shortcut``` section
- Default shortcut binding:
    - c = add new circle ```submitCircle```
    - m = add new marker ```submitMarker```
    - \` = reset current frame ```submitReset```
    - o = add a vertex to temporary polygon ```submitPolygonVertex```
    - p = add new polygon ```submitPolygon```
    - k = add a vertex to temporary line ```submitPolylineVertex```
    - l = add new polyline ```submitPolyline```
    - n = save current frame and go to next frame ```submitNextFrame```
    - e = save an empty frame and go to next frame ```submitEmptyFrame```
    - t = toggle *map click trigger* ```checkboxTriggerOnClick```
    - y = change *map click trigger* key ```submitChangeTriggerOnClick```
    - z = undo last addition, won't work for edit ```submitUndo```
    - 1, 2, 3, 4, 5 = reduce circle radius 10.000, 2.000, 500, 100, 20 respectively
    - 6, 7, 8, 9, 0 = increase circle radius 20, 100, 500, 2.000, 10.000 respectively

### Map Click Trigger
- to make it easier to draw, user might want to:
    - just click on map,
    - then app should assume that user:
        - clicked on the map and also
        - click on another button
- this requirement is addressed with *map click trigger*, find it in ```Shortcut``` section
- how to use:
    - user check ```Trigger on click``` checkbox
    - user type / input button name that should be triggered when map clicked
- example:
    - *map click trigger* activated, and button name is ```submitMarker```
    - user click on any position in map
    - app automatically added a new marker in clicked position

### Edit Circle or Marker
- click on button in circle/marker table OR click on the circle/marker
- enter new value in circle/marker input form
- click ```Add to Frame``` button

### Save Drawings to File
- Save (download) JSON file representing current frame => press ```Save Current Frame to JSON```
    - Load: select JSON file in ```Load Frame from JSON``` html input
    - JSON string format: ```json
            {
                "markers":[
                    {
                        "coordinate":[52.520085797742546,13.37465286254883],
                        "label":"marker 0",
                        "icon":"red"
                    },
                    ..
                ],
                "circles":[
                    {
                        "coordinate_center":[52.51778776996722,13.400402069091797],
                        "radius":500,
                        "label":"circle 0",
                        "fillcolor":"green",
                        "linecolor":"white"
                    },
                    ..
                ],
                "polygons":[
                    {
                        "coordinates":[
                            ["52.50086222750018","13.37242126464844"],
                            ["52.51778776996722","13.355255126953125"],
                            ["52.50096672615167","13.32246780395508"],
                            ["52.50713170694858","13.354053497314455"]
                        ],
                        "label":"polygon 0",
                        "linecolor":"blue"
                    },
                    ..
                ],
                "polylines":[
                    {
                        "coordinates":[
                            ["52.516952093701605","13.310794830322267"],
                            ["52.52332372377514","13.345127105712892"],
                            ["52.52666584871098","13.370532989501955"],
                            ["52.51820560213962","13.39662551879883"]
                        ],
                        "label":"polyline 0",
                        "linecolor":"blue"
                    },
                    ..
                ],
            }
        ```
- Save (download) JSON file representing all frame (animation) => press ```Save Frame Animation to JSON```
    - Load: select JSON file in ```Load Animation from JSON``` html input
    - JSON string format: ```[ frame, frame, frame ]``` (array of frame)

## View Control
- to navigate the map, enter desired center coordinate in ```control_center_x```, and ```control_center_y```
- to zoom the map, enter desired zoom level in ```control_zoom```
- html input ```control_center_x```, ```control_center_y```, and ```control_zoom``` will show current coordinate and zoom when map event occured



# NOT IMPLEMENTED YET
- delete marker / circle / polyline / polygon
- edit polyline / polygon
- friendly UI
- visible status from map view
- responsive or adjusting map size to display size
