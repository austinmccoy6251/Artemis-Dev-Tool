# Artemis GUI Engine

Artemis is a powerful cross-platform GUI engine which makes it **simple** and **fast** to build complex GUI's for your code base. 

The GUI development process is *frustrating*, *monotonous*, and *slow*. Even with the help of visual design tools such as Java Netbeans or Python QT's designer, it can still take hours to days to create simple GUI's for your code. 

Artemis solves this problem with its GUI engine, which allows you to build your GUI by drag-and-dropping prebuilt components which work out-of-box with no extra code. This completely eliminates all the boiler plate code that you used to have to write just to get your application to work. Artemis runs offline in your local browser, and the Artemis code module for your programming language allows you to connect to it and control it using our API.

# Official Documentation
The official documentation for Artemis is hosted on the [documentation section](https://www.artemisdevtool.com/guidebook/app/documentation/get-started/code-integration.html#full-example) our main website. This Github ReadMe will only contain a subset of that to demonstrate an overview of Artemis alongside a few troubleshooting tips.

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


# Tutorial: Building Artemis GUI for Python App
Below is a full example of using Artemis to build a graphical user interface for a simple Python application.

Case Study: [Building Artemis GUI for Python App](https://youtu.be/_TuejujFstw "Artemis Case Study")

![Tutorial Image](/Readme/images/tut.png)

# Troubleshooting

## Visual Designer
### Interface not saving
Please ensure that you press the "Save" button each time in the toolbar
### Elements not aligning to gridlines
Please ensure that your browser is set at 100% zoom. At the moment, if your zoom is different from 100% zoom, element alignment may fail.

## Python Code Integration
### Pip Installation is Failing
If you are using `pip install` or `pip3 install`, problems may sometimes occur. Instead use the following commands:
```sh
python -m pip install artemis_labs
python -m pip install artemis_labs --upgrade
```
### Python module not allowing me to use the latest features
Ensure your Python module is upgraded by entering into the terminal:
```sh
python -m pip install artemis_labs --upgrade
```
### Visual interface not updating
Please export the latest version of your website from the Artemis designer, place it next to your Python script, and ensure it is labeled exaclty `app.json`.

### Element callback not working
Please ensure that your Python code is setting a callback on the correct element name. Note that element names are **case-sensitive** and **must be unique**. If you capitalize your element name incorrectly, spell it incorrectly, or have two instances of your element name, issues may arise.
