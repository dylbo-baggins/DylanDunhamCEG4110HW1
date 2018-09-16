# DylanDunhamCEG4110HW1
# What this is
This is a simple android application that has a writing activity that randomly changes the color of text and displays the color value. There is also the drawing activity where a user can draw with their finger with any color and save the drawing as an image on their phone.

# Special Deployment
There is no special deployment, just make sure that the app has its one storage permission in your app settings.

# Instructions for use:
Below is the main menu. From here you can pick the writing or drawing activity by selecting the appropriate button. 


![alt text](https://github.com/dylbo-baggins/DylanDunhamCEG4110HW1/blob/master/mainmenu.PNG)


Next is the write activity. Users can tap on the text field to write something with the android keyboard. Then if they tap the change color button, the text will change color and the color values will be displayed below the button. Taping the return button returns to the main menu.


![alt text](https://github.com/dylbo-baggins/DylanDunhamCEG4110HW1/blob/master/writeactivity.PNG)


Finally, there is the draw activity. The user can draw images on the canvas which is located below the buttons on the top of the screen by dragging their finger on it. Tapping the color select button will pull up a color select screen to choose a new color. Tapping the clear button will clear the canvas. If the app has permission, tapping the save button will save the image into a new album created by the app and should be viewable by the native android gallery viewer. Taping the return button returns to the main menu.


![alt text](https://github.com/dylbo-baggins/DylanDunhamCEG4110HW1/blob/master/drawactivity.PNG)


# Design
The project is made up of 5 classes, the MainMenu, writeActivity, randomColor, drawActivity, and the drawCanvas classes. The main concept of the design was to keep with object orientated design. Separating out the app's layouts from the majority of their functionality allows for later re-use or easy updates. This is seen in that the randomColor class that gives all the information for the writeActivity, but it is not tied to the activity. This promotes reuse of the class if any of its functionality is needed in the future. This is also seen in the drawCanvas class. All the functions such as saving, drawing, color selecting, all but clearing the canvas are within the object itself. Also, all the settings of the paint object that actually creating the drawing on screen are availble via getters and setters. For example, this will be useful in the future if brush size or turning anti-aliasing off are desired functionality of the program. Finally, having a main menu itself promotes object orientated design, because it allows for more activities to be easily added to the app later, rather than having the two required activities go directly to eachother. Please see the simple design outlne below.


![alt text](https://github.com/dylbo-baggins/DylanDunhamCEG4110HW1/blob/master/SimpleDesignScheme.png)


## MainMenu Class
#### Variables: none
#### Methods: void onCreate, void startWriteActivity, void startDrawActivity
The MainMenu class extends the AppCompatActivity in the android library. It has no variables, and has only 3 methods. onCreate, startWrite, startDraw. onCreate takes a Bundle object and creates the Main Menu screen of the app. startWrite creates an intent from the current view and then starts the Write Activity. The startDraw method takes the current view, creates a new intent, and starts the Draw activity.

## writeActivity Class
#### Variables: randomColor rColor
#### Methods: void onCreate, void returnToMM, void textRandomColor
The writeActivity class has one variable, a randomColor object, rColor. It has 3 methods. The onCreate method, which takes a Bundle object and creates the writeActivity. The returnToMM which takes the current view, creates an intent of the MainMenu, then begins the transition to the MainMenu. The last method is the textRandomColor which takes the current view and requests a new random color from the rColor variable and sets a text field in the activity with the color info and changes the write in text field color to that colr.

## randomColor Class
#### Variables: Random randomValue, int color, int red, int green, int blue, String hex, String hexR, String hexG, String hexB
#### Methods: public randomColor, public void newColor(), getRed, getGreen, getBlue, getHex, getHexR, getHexG, getHexB, getColor
This class holds an android color value and can generate a new one with the newColor method. It can also send the variables of the object with the get functions.

## drawActivity
#### Variables: static final int MY_WRITE, int defaultColor, drawCanvas thisCanvas, boolean saveOn
#### Methods: void onCreate, void returnToMM, void colorSelect, void clear, void onRequestPermissionsResult
This class extends AppCompatActivity and sets up the draw activity and provides methods for the buttons. It also asks for writing to external storage permissions if not granted and will run the media scanner on the saved picture from the drawCanvas so it is viewable by other android apps. The returnToMM is a function for the back button to return to the Main Menu activity. The clear function remakes the drawCanvas which clears the image on screen. The colorSelect function displays the AmbilWarna dialog for selecting color for the user and sets the drawCanvas color to that selected color. The save method calls the drawCanvas's save method and then runs the media scanner on the saved file. The onCreate creates teh activity and checks and requests for the storage permission.

## drawCanvas
#### Variables:
#### Methods: 


