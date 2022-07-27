# Artemis GUI Engine

Artemis is a powerful cross-platform GUI engine which makes it **simple** and **fast** to build complex GUI's for your code base. 

The GUI development process is *frustrating*, *monotonous*, and *slow*. Even with the help of visual design tools such as Java Netbeans or Python QT's designer, it can still take hours to days to create simple GUI's for your code. 

Artemis solves this problem with its GUI engine, which allows you to build your GUI by drag-and-dropping prebuilt components which work out-of-box with no extra code. This completely eliminates all the boiler plate code that you used to have to write just to get your application to work. Artemis runs offline in your local browser, and the Artemis code module for your programming language allows you to connect to it and control it using our API.


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

# Python Example

## ✏️ Step 1: Building GUI
We navigate to the [Artemis visual design tool](https://artemisardesigner.com/login.html), and we use our drag and drop components to build the application below. We then download this design `app.json` by clicking the "Export" button at the top. We then place this next to our Python script.
![GUI Outline](/Readme/images/walkthrough_p1.png)

## ✏️ Step 2: Integrating Into Codebase

First, we import artemis by running the code
```python
from artemis_labs import artemis
```

We then define the function `runVisualizer` which takes in the GUI state with the param `state`:
```python
def runVisualizer(state):
   ...
```

Inside runVisualizer, we then extracts the value of the three inputs in our GUI `input-mean`, `input-std` and `input-samples`:
```python
def runVisualizer(state):

   # Unpack state
   mean = float(state['input-mean'])
   variance = float(state['input-std'])
   samples = int(state['input-samples'])
   ```

 We then call the function `generate_animated_normal` using these values as arguments, which generates a GIF displaying sampling from a normal distribution,
 and returns the path of the GIF
 ```python
 # Generate animated normal
 gif_path = generate_animated_normal(mean, variance, samples)
 ```

Finally, we update the image in the gui named `pdf` with this GIF and the text named 'header' with the text 'My Plot' by calling the code:
```python
# Update app
app.update('pdf', artemis.load_image(gif_path))
app.update('header', 'MyPlot')
```

Putting this together, we have the following script:

![GUI Outline](/Readme/images/walkthrough_p2.png)

## ✏️ Step 3: Launching the code
Now, we run the code from the terminal by typing:
```ssh
python code.py
```

And we observe a web browser appear running our GUI. We enter in some values, press run, and observe the code run as expected.
![GUI Result](/Readme/images/walkthrough_p3.gif)

# Visual Editor Documentation
## Getting Started
### ✏️ Step 1: Start your free trial
Visit the main website at https://www.artemisdevtool.com/, click "Start My Free Trial", and sign up for a free trial through our Gumroad link.
![Start Trial](/Readme/images/start_trial.png)

### ✏️ Step 2: Get your API KEY

Once you've signed up for a free trial, an email from `Artemis Labs <noreply@customers.gumroad.com>` should be sent to your email. This may take a few minutes. This email contains an `API_KEY` that you need to have on hand.
![API Key Email](/Readme/images/api_key_email.png)

### ✏️ Step 3: Create an account
Now, create an account for the Artemis visual design tool at https://artemisardesigner.com/signup.html

Once redirected to the login page, login, and then enter your `API_KEY` when prompted.
![API Key](/Readme/images/api_key.png)

### ✏️ Step 4: Create your first app
Once you activate your account, go ahead and click the "Create App" button to create your first app. Enter in your app name, and click "Create App"
![API Key](/Readme/images/create_app.png)

### ✏️ Step 5: Edit your first app
You should now see your app appear in your App Dashboard. Go ahead and click the edit button to edit this app
![API Key](/Readme/images/edit.png)

### ✏️ Step 6: Start editing
You should now be taken to the editor where you can edit away! Instructions for using the editor can be found below. When you're done, **make sure** to click the Save button at the top to save your changes
![API Key](/Readme/images/save.png)

### ✏️ Step 7: Test Launch
To test preview what your app will look like, go back to the app dashboard by clicking "Apps" in the top left corner, or pressing back, and then press the "Launch" button next to your app
![API Key](/Readme/images/launch.png)

## Artemis Visual Design Tool Guide
This guide is for using the Artemis visual design editor. Please read the above section to learn how to get to this point.


Underneat this website, create an account, and then login to get started! If you haven't already subscribed to Artemis, you will need to visit the main website at 
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
