# TieUi Documentation

## Introduction to TieUi
TieUi is a revolutionary Python module that allows users to craft frontend interfaces directly from Python without delving into HTML or other web-specific technologies. By leveraging the power of material-ui components, developers can quickly and efficiently create web apps in a purely Pythonic way and have them hosted without any hassles.

## Getting Started
The first step is to go on: [https://tieui.app/](https://tieui.app/) and click on get started, this will open the webapp. There you need to register and create a new account, or simply log in

### Web App
Install using pip

```sh
pip install tieui
```

#### First Application
After logging in on the dashboard you will be prompted a message, learn about the plans or get started. 
##### Plans
Having a plan has lots of perks, so if you have one thank you for trusting us! you can now create whatever app name you want and click on Get Started.
##### Free Version
You can also simply just click on "Create App With Free Name" and you will also be able to start developing! you just wont have some of the benefits.


You can copy the appName from your page once you have clicked the button.

##### Sample First Application Code:
We are going to build a simple quoting app. The user will be able to enter values and get a pricing for the service, 
```python
from tieui import TieUi

# Initializing the App
tie = TieUi(appName="YOUR_APP_NAME") # You can get the app name from the message on your application after you have added your fitst application

tie.add(tie.label({"label": "Hello World", "variant": "h6", "color": "black"})) # Label with the result of the calculation

tie.publish() # Publishing the application
```

Now you can open a new terminal and run the file by simply running:

```sh
python3 your_file_name.py
```


### Desktop Container
> Install Node: You can follow the Guidelines [here](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)

> Install Electron: 

```sh
npm i -g electron
```
Install the module using pip
```sh
pip install tieui
``` 
#### First Application
##### Sample First Application Code:
```python
from tieui import TieUi

tie = TieUi(isLocal=True) # This is the only part that changes

tie.add(tie.label({"label": "Hello World", "variant": "h6", "color": "black"})) # Label with the result of the calculation

tie.publish() # Publishing the application
```

Now you can open a new terminal and run the file by simply running:

```sh
python3 your_file_name.py
```

If it is the first time, you will have to log in, after that you will have to stop the application and run it again.
You can stop the application by simply 
```
ctr + C
```

# Common Function
## Add
 This function will allow you to add components to your page. Each add is a new component in the page

```python
from tieui import TieUi

# Initializing the App
tie = TieUi(appName="YOUR_APP_NAME")

tie.add(YOUR_COMPONENT_HERE)
```

## publish
 This function will publish your application to be viewed in the appName you specified

```python
from tieui import TieUi

# Initializing the App
tie = TieUi(appName="YOUR_APP_NAME")

tie.publish()
```

## Update
 This function will re-render your application, typically used when there is a change in your app caused by an user action

```python
from tieui import TieUi

# Initializing the App
tie = TieUi(appName="YOUR_APP_NAME")

tie.publish()
```

## liveUpdate
 This function will re-render your application, typically used when there are changes occurring automatically without user action

```python
from tieui import TieUi

# Initializing the App
tie = TieUi(appName="YOUR_APP_NAME")

tie.publish()
```


# Component Library
## Text Box
The TextField wrapper component is a complete form control including a label, input, and help text. It comes with three variants: outlined (default), filled, and standard.
### Props
The TextBox component is highly customizable and accepts the following props:

``label (PropTypes.string):`` The label displayed above the input field, providing context or guidance for the user.

``value (PropTypes.string):`` The current value of the input field. You can set this value to control the input field programmatically.

``placeholder (PropTypes.string):`` An optional placeholder text displayed within the input field when it is empty.

``disabled (PropTypes.bool):`` If set to true, the input field will be disabled and cannot be edited by the user.

``required (PropTypes.bool):`` If set to true, the input field is marked as required, indicating that the user must provide input.

``error (PropTypes.bool):`` If set to true, the input field is visually marked as having an error.

``helperText (PropTypes.string):`` A helper text displayed below the input field to provide additional information or error messages.

``variant (PropTypes.string):`` Specifies the input field's appearance style, such as "outlined" or "filled."

### Callback Returns
The callback returns a json object with the key name: value. See example below. 

### Example
```python
from tieui import TieUi

# Initializing the App
tie = TieUi(appName="YOUR_APP_NAME")

def handle_text_input_change(item):
    global text_input_value
    new_value = item.get("value", "")
    text_input_value = new_value

tie.add(tie.textBox({"id": "unique-id-1","label": "A Float R", "variant": "outlined"},handle_text_input_change))
```
## Select
The Select component is a versatile dropdown selection component integrated into your Python application using the TieUi library. It allows users to choose from a list of options and is commonly used for various selection tasks.

### Props
The Select component accepts the following props:

``label (PropTypes.string):`` The label displayed above the dropdown, providing context or guidance for the user.

``value (PropTypes.string or PropTypes.number):`` The current selected value of the dropdown. You can set this value to control the selected option programmatically.

``disabled (PropTypes.bool):`` If set to true, the dropdown will be disabled and cannot be interacted with by the user.

``required (PropTypes.bool):`` If set to true, the dropdown is marked as required, indicating that the user must make a selection.

``error (PropTypes.bool):`` If set to true, the dropdown is visually marked as having an error.

``helperText (PropTypes.string):`` A helper text displayed below the dropdown to provide additional information or error messages.

``variant (PropTypes.string):`` Specifies the dropdown's appearance style, such as "outlined" or "filled."

``options (PropTypes.array):`` An array of objects representing the options in the dropdown. Each object should have the following structure:

&nbsp;&nbsp;&nbsp;&nbsp;``value (string or number):`` The value associated with the option.

&nbsp;&nbsp;&nbsp;&nbsp;``label (string):`` The label or display text for the option.

### Callback Returns
The callback returns a json object with the the selected element key. See example below. 
```json
    {'componentId': 'select1', 'value': "SOME SELECTED ELEMENT"}
```

### Example
```python
from tieui import TieUi

# Initializing the App
tie = TieUi(appName="YOUR_APP_NAME")

def handle_select_change(item):
    print(item.get("value", ''))
    tie.update()

tie.add(tie.select({
    "id": "unique-id-3",  # Replace with a unique identifier
    "options": options,  # List of selectable options
    "label": "Select label",
    "variant": "outlined",  # Variant of the select component
    "value": "option1"  # Provide a default value that matches one of the available options
}, handle_select_change))
```

## Button
The Button component is a versatile button element integrated into your Python application using the TieUi library. It allows users to trigger actions, submit forms, or perform various interactive tasks. This documentation provides information on how to use the Button component with props similar to the Material-UI Button component.
### Props
The Button component accepts the following props:

``children (PropTypes.node):`` The content displayed within the button, which can include text, icons, or other elements.

``variant (PropTypes.string):`` Specifies the button's appearance style, such as "contained," "outlined," or "text."

``color (PropTypes.string):`` Specifies the button's color scheme, such as "primary," "secondary," or "default."

``disabled (PropTypes.bool):`` If set to true, the button will be disabled and cannot be clicked by the user.

``size (PropTypes.string):`` Specifies the button's size, such as "small," "medium," or "large."

``startIcon (PropTypes.node):`` An icon or element displayed before the button's label or content.

``endIcon (PropTypes.node):`` An icon or element displayed after the button's label or content.

``href (PropTypes.string):`` If provided, the button will act as an anchor element and navigate to the specified URL when clicked.

``target (PropTypes.string):`` Specifies where to open the URL if the href prop is used. Values can be "_self," "_blank," "_parent," or "_top."

### Callback Returns
Returns when a click occured, value is undefined

### Example
```python
def custom_button_callback_handler(item):
    print("CUSTOM")
    tie.update()
tie.add(tie.button({"id": "unique-id-3", "label": "Add Numbers", "variant": "outlined"}, custom_button_callback_handler))
```

## Bar Chart

### Props
The `BarChart` component accepts the following props:

- `chartSeries` (`PropTypes.array.isRequired`): An array of data series objects to be displayed on the bar chart. Each data series object should have the following structure:
  - `name` (string): The name or label for the series.
  - `data` (array): An array of data points for the series. Each data point should be a numerical value.
  - `color` (string): The color of the series bars on the chart.

- `categories` (`PropTypes.array.isRequired`): An array of x-axis categories or labels. These categories represent the values on the x-axis of the bar chart.

- `title` (`PropTypes.string.isRequired`): The title of the bar chart.

- `syncButtonLabel` (`PropTypes.string.isRequired`): The label for the synchronization button, which is not used in your provided code.

- `overviewButtonLabel` (`PropTypes.string.isRequired`): The label for the overview button, which is not used in your provided code.
### Callback Returns
No callbacks this is just a visualization componet

### Example
```python

chartSeries = [
  {
    "name": "Series 1",
    "data": [10, 41, 35, 51, 49, 62, 69, 91, 148],
  },
]

categories = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep']


bar_chart_settings = {
    "title": "Moisture Sensor Data Over Time",
    "chartSeries": chartSeries,
    "categories": categories,
    "syncButtonLabel": "Sync Data",
    "overviewButtonLabel": "View Overview"
}
bar_chart_component = tie.barChart(bar_chart_settings)
tie.add(bar_chart_component)
```
## Line Chart

### Props
The `LineChart` component accepts the following props:

- `chartSeries (PropTypes.array.isRequired)`: An array of data series objects to be displayed on the line chart. Each data series object should have the following structure:

- `name (string):` The name or label for the series.
- `data (array):` An array of data points for the series. Each data point should be an object with x and y values.
- `color (string):` The color of the series line on the chart.
- `categories (PropTypes.array.isRequired)`: An array of x-axis categories or labels. These categories represent the values on the x-axis of the line chart.

- `title (PropTypes.string.isRequired):` The title of the line chart.

- `syncButtonLabel (PropTypes.string.isRequired):` The label for the synchronization button, which is not used in your provided code.

- `overviewButtonLabel (PropTypes.string.isRequired):` The label for the overview button, which is not used in your provided code.

### Callback Returns
No callbacks this is just a visualization componet
### Example
```python
y_data =  [11,12,90,78,33,55,90]
x_data = [0,1,2,3,4,5,6,7,8]

line_chart_settings = {
    "title": "Moisture Sensor Data Over Time",
    "chartSeries": [
        {"name": "Moisture Level", "data": y_data, "color": "#0077B6", 'categories': x_data },
    ],
    "categories": x_data
}
line_chart_component = tie.lineChart(line_chart_settings)
tie.add(line_chart_component)
```

## Label
The Label component is a simple text label element integrated into your Python application using the TieUi library. It is used to display text or provide descriptions, context, or instructions within your application's user interface.

### Props
The Label component is straightforward and accepts the following props:

- `text (PropTypes.string.isRequired):` The text content to be displayed by the label. This prop is required.

- `variant (PropTypes.string):` Specifies the label's appearance style or variant, such as "standard" or "outlined." (Defaults to "standard" if not specified)

- `color (PropTypes.string):` Specifies the label's text color or style, such as "primary," "secondary," or a custom color code. (Defaults to the default text color if not specified)

- `align (PropTypes.string):` Specifies the alignment of the label's text, such as "left," "center," or "right." (Defaults to "left" if not specified)

- `display (PropTypes.string):` Specifies how the label is displayed, such as "block" or "inline." (Defaults to "block" if not specified)
### Callback Returns
No callbacks this is just a visualization componet

### Example
```python
tie.add(tie.label({"label": "Result: ", "variant": "h6", "color": "black"}))
```

## Checkbox
The Checkbox component is a user interface element integrated into your Python application using the TieUi library. It provides a way for users to select or deselect options, make choices, or toggle a binary state.

### Props
The Checkbox component accepts the following props, including those for <FormGroup> and <FormControlLabel> components to enhance functionality:

- `label (PropTypes.string):` The label or text displayed next to the checkbox, providing context or description for the checkbox.

- `checked (PropTypes.bool):` A boolean value indicating whether the checkbox is checked (selected) or unchecked (deselected).

- `disabled (PropTypes.bool):` If set to true, the checkbox will be disabled and cannot be interacted with by the user.

- `FormGroupProps (PropTypes.object):`

   - `row (PropTypes.bool):` A boolean value indicating whether the form group should be displayed in a row layout. If set to true, checkboxes within the form group will be displayed horizontally.
- `FormControlLabelProps (PropTypes.object):`

   -` labelPlacement (PropTypes.string):` Specifies the placement of the label in relation to the checkbox. Values can be "start," "end," "top," or "bottom," determining whether the label appears before or after the checkbox.

### Callback Returns
Returns if the checkbox is selected or not
```json
{'componentId': 'checkbox5', 'value': True}
```
### Example
```python
def handle_checkbox_change(item):
    print(item)

tie.add(tie.checkbox({"label": "Result: "}, handle_checkbox_change))
tie.add(tie.checkbox({"label": "Result: ", "labelPlacement": "bottom"}, handle_checkbox_change))
```
## Slider
The Slider component is a user interface element integrated into your Python application using the TieUi library. It allows users to select a value within a range by dragging a slider thumb along a track. The Slider component provides a way to input numeric values or adjust settings interactively.

### Props
The Slider component accepts the following props:

- `value (PropTypes.number):` The current value of the slider. This value represents the selected position of the slider thumb along the track.

- `min (PropTypes.number):` The minimum value allowed for the slider. Users cannot select a value lower than this minimum.

- `max (PropTypes.number):` The maximum value allowed for the slider. Users cannot select a value higher than this maximum. 

- `step (PropTypes.number):` The step size or increment by which the slider value changes when users interact with it. For example, if step is set to 1, the slider moves in increments of 1.

- `disabled (PropTypes.bool):` If set to true, the slider will be disabled and cannot be interacted with by the user.

- `marks (PropTypes.array):` An array of mark values to display along the track. Each mark value should be a number within the range of the slider. Marks can serve as reference points or labels.

-` valueLabelDisplay (PropTypes.string):` Specifies when to display the value label associated with the slider. Possible values are "on," "off," "auto," or "always." "On" displays the label when the user interacts with the slider, "off" never displays it, "auto" displays it when interacting or keyboard-focused, and "always" always displays it.

### Callback Returns
Will return the current step:
```json
{'componentId': 'slider7', 'value': 15}
```

### Example
```python
def handle_slider_change(item):
    print(item)
tie.add(tie.slider({"min": 5, "max": 30, "step": 1}, handle_slider_change))
```


## Switch
The Switch component is a UI element that allows users to toggle between two states, typically representing binary choices like on/off or true/false.

### Props
The Switch component accepts the following props:

checked (PropTypes.bool): A boolean value indicating whether the switch is in the "on" state (true) or "off" state (false).
disabled (PropTypes.bool): If set to true, the switch will be disabled and cannot be interacted with by the user.

FormGroupProps (PropTypes.object):

row (PropTypes.bool):
A boolean value indicating whether the form group should be displayed in a row layout. If set to true, checkboxes within the form group will be displayed horizontally.
FormControlLabelProps (PropTypes.object):

labelPlacement (PropTypes.string):
Specifies the placement of the label in relation to the checkbox. Values can be "start," "end," "top," or "bottom," determining whether the label appears before or after the checkbox.

### Callback Returns
A callback function that is triggered when the user interacts with the switch, toggling its state. It receives the updated checked state as an argument.
```json
{'componentId': 'switch8', 'value': True Or False}
```
### Example
```python
def handle_switch_change(item):
    print(item)
tie.add(tie.switch({"label": "Result: "}, handle_switch_change))
```
## Chip
The Chip component is a versatile UI element used to represent tags, input chips, or other small actionable elements. It's commonly used in filtering systems, as tags for categorization, or as a way to display small pieces of information interactively.


### Props
The Chip component accepts the following props:

- `label (PropTypes.string):` A string representing the content of the chip.
- `color (PropTypes.string):` Defines the color of the chip. Acceptable values are 'default', 'primary', 'secondary', and 'error'.
- `size (PropTypes.string):` Sets the size of the chip. Valid values are 'small', 'medium', and 'large'.
- `variant (PropTypes.string):` Determines the style of the chip. Choices include 'filled', 'outlined'.
- `onDelete (PropTypes.func):` A callback function triggered when the delete icon is clicked. Only relevant if the deleteIcon prop is provided.
- `icon (PropTypes.element):` An element placed as an icon at the start of the chip.
- `deleteIcon (PropTypes.element):` A custom delete icon element. Displays only if the onDelete function is provided.
- `disabled (PropTypes.bool):` If true, the chip will be disabled and not interactive.
- `onClick (PropTypes.func):` A callback function that is triggered when the chip is clicked.
### Callback Returns
```json
{
  'componentId': 'chip123',
  'event': 'click' Or 'delete'
}
```
### Example
```python
def handle_chip_clicked(item):
    val = item.get("value", "")
    if (val == "delete"):
        print("chip deleted")
    else:
        print("chip Clicked")

tie.add(tie.chip({"label": "Result: "}, handle_chip_clicked))
tie.add(tie.chip({"label": "Result: ", "variant": "outlined"}, handle_chip_clicked))
```
## Progress
The Progress component is a visual indicator used to show that a process is in progress. It typically appears as a circular animation.

### Props
The CircularProgress component accepts the following props:

- `color (PropTypes.string):` The color of the circular progress indicator.
- `size (PropTypes.number):` The size of the circular progress indicator.
- `thickness (PropTypes.number):` The thickness of the circular progress indicator's stroke.
### Callback Returns
No callbacks this is just a visualization componet

### Example
```python
tie.add(tie.progress({"color": "success"}))
```


## Tabs
The Tab component is typically used in tabbed user interfaces to switch between different sections or views of content. They contain different components inside.

### Props
The Tab component accepts the following props:

- `label (PropTypes.string):` The label or text displayed on the tab.
- `tab (PropTypes.Array):` array of object with:
    - ` label:` the label of the tab
    - `value:` the value of the tab
    - `components:` a list of components inside

### Callback Returns
Components inside the tab have callbacks but not the tabs themselves
### Example
```python

tab1_components = [
    tie.label({"label": "Content for Tab 1", "variant": "body1"}),
    tie.chip({"label": "Result: "}, handle_chip_clicked),
    tie.select({
        "id": "unique-id-3",  # Replace with a unique identifier
        "options": [
    {"label": "Option 1", "value": "option1"},
    {"label": "Option 2", "value": "option2"},
    {"label": "Option 3", "value": "option3"},
],  # List of selectable options
        "label": "Select label",
        "variant": "outlined",  # Variant of the select component
        "value": "option1"  # Provide a default value that matches one of the available options
    }, handle_select_change)
]

tab2_components = [
    tie.label({"label": "Content for Tab 2", "variant": "body1"}),
    tie.button({"id": "unique-id-qw3", "label": "Add Numbers", "variant": "outlined"}, handle_update)
]

tabs_settings = {
    "value": 0,  # default active tab index
    "tab": [
        {"label": "Tab 1", "value": "tab1", "components": tab1_components},
        {"label": "Tab 2", "value": "tab2", "components": tab2_components},
        # ... more tabs if needed
    ]
}

tie.add(tie.tabs(tabs_settings))
```
## Links
The Link component is used to create hyperlinks or anchor tags that allow users to navigate to external or internal web pages.

### Props
The Link component accepts the following props:

- `href (PropTypes.string):` The URL to which the link will navigate.
- `target (PropTypes.string):` The target window or frame for the link, e.g., "_blank" for opening in a new tab.
- `rel (PropTypes.string):` The relationship of the linked resource, e.g., "noopener" for security best practices.
- `underline (PropTypes.string):` The underline prop can be used to set the underline behavior. The default is always.

### Callback Returns
No callback options as it only redirects 
### Example
```python
tie.add(tie.links({"href": "https://tieui.app", "underline":"hover", "label": "underline hover"}))
```
## Alerts
The Alert component is used to display notifications, warnings, or messages to the user. It can have different severity levels such as success, info, warning, or error.

### Props
The Alert component accepts the following props:

- severity (PropTypes.string): The severity level of the alert, e.g., "success," "info," "warning," "error."
- icon (PropTypes.node): An optional icon to display alongside the alert message.
- onClose (PropTypes.func): A callback function that is triggered when the user closes the alert.
- variant: filled, and outlined.

### Callback Returns
No callback options
### Example
```python
tie.add(tie.alerts({"severity": "error", "label": "This is an error alert — check it out!"}))
```

## Data Grid
The DataGrid component is a versatile table/grid component integrated into your Python application using the TieUi library. It is designed to display structured data in a tabular format, allowing users to view, interact with, and manipulate data efficiently.

### Props
The DataGrid component offers extensive customization options and accepts the following props:

- `columns (PropTypes.array.isRequired):` An array of column definitions that determine the structure and behavior of the data grid. Each column definition should be an object with the 

- `field (string):` The field name or key in the data object that the column represents.

- `headerName (string):` The header text displayed at the top of the column.

- `width (number):` The width of the column in pixels.

- `sortable (bool):` If set to true, the column can be sorted by clicking on the column header.

- `filterable (bool):` If set to true, a filter input is provided for the column to filter data based on its values.

- `resizable (bool):` If set to true, the column can be resized by dragging its edge.

- `renderCell (function):` A custom function to render the content of the cell. It receives the cell value and the row data as arguments.

- `rows (PropTypes.array.isRequired):` An array of data objects representing the rows to be displayed in the data grid. Each data object should have properties corresponding to the - column fields defined in the columns prop.

- `pageSize (PropTypes.number):` The number of rows to display per page. If not specified, all rows are displayed on a single page.

- `pagination (PropTypes.bool):` If set to true, pagination controls are displayed, allowing users to navigate through multiple pages of data.

### Callback Returns
No callbacks
### Example
```python
data_grid_component = tie.dataGrid(
    {
        "rows": [
            {
                "id": 1,
                "column1": "Value 1",
            }
        ],
        "columns": [
            {
                "field": "column1",
                "headerName": "Column 1",
                "width": 150,
            }
        ],
        "options": {},  # Add any options you need for the DataGrid
    }
)
tie.add(data_grid_component)
```

## Image List
Comming soon
### Props
Comming soon
### Callback Returns
Comming soon
### Example
Comming soon

# CODE EXAMPLES
To view examples you can find our github repo here: [https://github.com/tieUi-app/public-examples](https://github.com/tieUi-app/public-examples)