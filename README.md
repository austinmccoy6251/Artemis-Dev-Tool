# Artemis GUI Engine

Artemis is a powerful cross-platform GUI engine which makes it **simple** and **fast** to build complex GUI's for your code base. 

The GUI development process is *frustrating*, *monotonous*, and *slow*. Even with the help of visual design tools such as Java Netbeans or Python QT's designer, it can still take hours to days to create simple GUI's for your code. 

Artemis solves this problem with its GUI engine, which allows you to build your GUI by drag-and-dropping prebuilt components which work out-of-box with no extra code. This completely eliminates all the boiler plate code that you used to have to write just to get your application to work. Artemis runs offline in your local browser, and the Artemis code module for your programming language allows you to connect to it and control it using our API.
<br><br>

# How it works
## Step 1: Design your GUI
 Drag-and-drop prebuilt GUI components in our visual designer to assemble your GUI. Then, customize these components to your liking, and give each important component a unique name.
![Artemis Code](/Readme/images/process_p1.gif)

## Step 2: Integrate into your code
 Artemis code integration is designed to be simple and painless. 
 In just three lines of code, you can launch the Artemis GUI, place event listeners on components, and update the content of components.

![Artemis Code](/Readme/images/process_p2.gif)

## Step 3: Launch your codebase
 When your code base runs, Artemis will automatically spawn an offline browser with your GUI. Users may then interact with your codebase through the GUI as if it was designed in your native programming language  
![Artemis Code](/Readme/images/process_p3.gif)

<br>
# Features
Artemis is rapidly adding new and useful features to its platform. If you have features requests please contact the CEO personally at austinmccoy@artemisar.com. We welcome all ideas, and are working hard to make our platform the ideal tool for you.

Artemis currently supports the following features: Input, Text Area, Dropdown, Checkbox, Radio Button, Button, Heading, Image

<br><br>

# Python Code Documentation
## Setup and Installation
Run the following commands in your terminal to install our Python module using pip
```sh
python -m pip install artemis_labs
python -m pip install artemis_labs --upgrade
```


## Building your GUI
### ✏️ Step 1: Designing your GUI
Use the [Artemis visual design tool](https://artemisardesigner.com/login.html) to design a GUI for your application. See the section on "Artemis Design Tool" for more information on using the Artemis visual design tool.
<br>

### ✏️ Step 2: Downloading GUI design file
Once you have designed your GUI in the Artemis design tool, you need to export it as a JSON. You can do so by clicking the "Export" button at the top of the visual editor. This will download a JSON file upon clicking it. 
![Exported image](/Readme/images/export.png)
### ✏️ Step 3: Moving GUI design file next to Python script
Place the downloaded JSON file next to the Python script from which you will launch the Artemis GUI
![Bundle of code](/Readme/images/code_bundle.png)

<br>

## Integrate Artemis Into Codebase
### ✏️ Step 1: Importing Artemis Python module
Import the artemis code module using the following import statement
```python
from artemis_labs import artemis
```


### ✏️ Step 2: Launching GUI
Run the following command at the top of your code to launch the Artemis GUI
```python
app = artemis()
```

### ✏️ Step 3: Setting event listeners
To create an event listener on an component, write the code below, replacing `Event Type` with the chosen event type from the table below, the `Component Name` with the name you gave the GUI component in the visual designer, and the function you'd like to have called when the event occurs.
```python
app.on("Event Type", "Component Name", callback_function)
```

Example of setting callback on a button
```python
# Function which is called when the button 'run' is clicked
# This function extracts the state of the components named inputEmail
# and inputPwd, and it prints their values
@param state JSON object containing GUI state (passed by callback handler)
def printLoginInfo(state):
   email = state['inputEmail']
   pwd = state['inputPwd']

# Create callback which executes function runMyCode after component named 'run' 
# is clicked
app.on('click', 'run', runMyCode)
```

The following `Event Type` are supported at the moment by Artemis:
| `Event Type`      | `Event Description `|
| :---        |    :----:   |
| Click      | Button click       |



<hr/>

### ✏️ Step 4: Updating components
To update the content of a component, write the code below, replacing `Component Name` with the name you gave the GUI component in the visual designer, and `ComponentValue` with the content you'd like to update the element with (see below for acceptable values):
```python
app.update('Component Name', 'Component Value')
```


Example of updating component of type Text:
```python
# Update component named 'MyHeading" with text "New Title"
app.update('MyHeading', 'New Text')
```

Example of updating component of type Image / GIF:
```python
# Update component named MyPlot with image at path ./exportedMatPlotLibPlot.png
app.update('MyPlot', artemis.load_image('./exportedMatPlotLibPlot.png'))
```

The following `Component Value` are supported at the moment by Artemis:
| `Component Type`      | `Component Value Format `|
| :---        |    :----:   |
| Text / Numeric      | "value" |
| Image / GIF | artemis.load_image('image_path') |

<br>

# Visual Editor Documentation
## Summary
Artemis visual editor contains a number of prebuilt GUI components, and that list is growing rapidly. Below you will find descriptions of each prebuilt GUI component, the attributes that the visual editor allows you to customize about that component, the information that is included about that component when your code base queries or receives via callback the GUI state (see code information for explanation of GUI state), and the information about that component that can be updated from your code base.
## Text Input
Description: This is a single-line text input 
<summary>Clement Attributes:</summary> 
<ul>
<li>[Clement Name] Unique name of component</li>
<li>[Placeholder Text] Placeholder text for input</li>
<li>[Border Radius] Input box rounding</li>
<li>[Transparent Background] If input box is transparent</li>
</ul>
 </details>

Query Information (what the GUI state stores about this component): Contents of text input
```json
{
   "text-input" : "This is what the user typed in"
}
```

Update Information (what updating this component does to the GUI): Updates contents of text input
```python
app.update('text-input', 'new text input content')
```
