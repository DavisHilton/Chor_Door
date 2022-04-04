WalkThrough Video: https://www.youtube.com/watch?v=0SSMeWJVyBI
BUILDING INTERACTIVE JAVASCRIPT WEBSITES
Chore Door
In this project, you will use your knowledge of JavaScript and the DOM to complete Chore Door, a single-page interactive game built with JavaScript. Before we start, let’s take a look at what your game will look like by the end of the project. Play a few rounds and see how you fare against the ChoreBot. Your goal is to open all of the doors without running into ChoreBot. If you manage to avoid ChoreBot until you open the last door, you win!

If you get stuck during this project or would like to see an experienced developer work through it, click “Get Unstuck“ to see a project walkthrough video.

Tasks
0/20 Complete
Mark the tasks as complete by checking them off
Getting Started
1.
Take a moment to familiarize yourself with the existing code in index.html, style.css, and script.js.

Note that you’ll complete the functionality for the Chore Door game one step at a time in script.js.


Hint
Notice that all of the CSS and HTML has been provided for you to allow you to focus on just the JavaScript of the web app. You will also notice that the script.js file is not completely empty. The code for detecting and responding to click events for each of the door images has been provided for you—you will learn more about event listeners in the near future!

2.
Let’s start by accessing the elements of the door images. At the top of script.js, create a variable called doorImage1 and set it to the HTML element with the id of door1 .


Hint
In order to access HTML elements in JavaScript, remember to reference the document keyword first. Then, use the .getElementById() method to select an HTML element by its id.

3.
There are three doors in the game! Let’s do the same for the other door images.

Create a variable called doorImage2 and set it to the HTML element with the id of door2. Then, create another variable called doorImage3 and set it to the HTML element with id of door3.


Hint
Remember to pass the id of the HTML element as a string for the argument of the .getElementById() method.

4.
We also need to access the orange div that says “Good luck!” located under the doors on the webpage. Below the variables containing the door images, create a variable called startButton and set it to the HTML element with the id of start.

We will be manipulating this div in a future task to display the game result.


Hint
Make sure that these variables are defined at the top of script.js. We will be referencing these HTML elements throughout our code.

Checking Doors
5.
Now that we have access to the HTML elements we need to manipulate, let’s build some game logic.

First, we will create a function to check if the door that the player clicked on is closed. This is to make sure that clicking on already opened doors will not affect the progress of the game.

Below all the variable declarations, create a function called isClicked that takes the parameter of door.


Hint
You can define the function using the function keyword or using an arrow function expression. The syntax for creating a function using the arrow function expression is as follows:

const newFunction = (param) => {
  // Function code
}
6.
Inside the isClicked() function, create a conditional that checks if the src property of door is equal to closedDoorPath. If the condition is truthy, return true. Otherwise, return false.


Hint
Create an if…else statement to check if door.src is equal to (===) closedDoorPath. You can use the return keyword inside the conditional statements to return appropriate boolean values.

7.
Next, we will create another function that checks if the player clicked on the Chore Door! The logic will be similar to the isClicked() function.

Create a function called isBot that takes door as its parameter. Inside the function, create a conditional statement that checks if the src property of door is equal to botDoorPath. If the conditional is truthy, return true.


Hint
Refer back to our code for the isClicked() function. The isBot() function should look very similar.

Writing Play and Game Over Logic
8.
Let’s continue writing our game logic.

Create a function to display a game over message depending on whether the player has won or lost. Create a function called gameOver that takes status as its parameter.


Hint
You can define the function using the function keyword or using an arrow function expression. The syntax for creating a function using the arrow function expression is as follows:

const newFunction = (param) => {
  // Function code
}
9.
Inside the gameOver() function, write a conditional statement that checks if status is equal to 'win'.

If the conditional statement evaluates to a truthy value, set the content of the startButton element to 'You win! Play again?'. If the condition is falsy, set it to 'Game over! Play again?'.


Hint
Remember that you can reference the innerHTML property to get and set the content of an HTML element.

10.
As the last line of the gameOver() function block, set currentlyPlaying to false. This will allow our start button to be triggered again for another round of Chore Door.


Hint
Make sure that this is the last line of the gameOver() function block.

11.
Using the three functions we’ve created so far, we will write the logic for progressing the game.

Create a function called playDoor that takes door as its parameter. Inside the function, decrement numClosedDoors by one. This will decrease the value of the numClosedDoors variable by one every time a door is opened.


Hint
You can decrement a numeric value by one by using the decrement operator (--).

12.
Below where we decremented the numClosedDoors variable, create a conditional statement that checks if numClosedDoors equals 0. This will mean that the player has successfully avoided the ChoreBot! If the conditional evaluates to true, call gameOver() with the argument of 'win'.


Hint
Create an if conditional statement to check whether numClosedDoors is equal to (===) 0.

13.
Let’s add another condition after the if block. Check if calling the isBot() function with the argument of door returns true. If so, run gameOver() with no argument.


Hint
You can add another condition after the initial if block using the else if keyword.

Call isBot(door) as the condition of the else if statement. If isBot(door) returns true, the conditional statement (gameOver()) will run.

Choosing a Random Chore Door
14.
What good is this game if you know where the ChoreBot is always hiding?

Create a function called randomChoreDoorGenerator. Inside the function, create a variable called choreDoor, and set it to a random integer between 0 and numClosedDoors.

We will use this function to randomize which door ChoreBot will hide behind.


Hint
To generate a random integer between 0 and numClosedDoors, we can use two Math methods: Math.floor() and Math.random().

Your choreDoor variable should be set to an expression similar to the following:

Math.floor(Math.random() * numClosedDoors));
In the above expression:

The Math.random() function generates a decimal number between 0 and 1.
The numClosedDoors variable is used as a multiplier with the Math.random() function to generate a decimal number between 0 and numClosedDoors.
The Math.floor() function rounds down any decimal value to the closest whole number.
15.
Now that the randomChoreDoorGenerator() function randomly generates one of three possible values (0, 1, or 2), it’s time to write the logic that assigns where the ChoreBot will hide based on each outcome.

First, create an if conditional to check if choreDoor equals 0. If the condition is true, set openDoor1 to botDoorPath (the ChoreBot will hide in the first door!), openDoor2 to beachDoorPath, and openDoor3 to spaceDoorPath.


Hint
Create an if conditional to check whether choorDoor is equal to (===) 0.

16.
Add an else if statement to our previous if statement to check if choreDoor equals 1. If the condition is true, set openDoor1 to beachDoorPath, openDoor2 to botDoorPath (the ChoreBot will hide in the second door!), and openDoor3 to spaceDoorPath.


Hint
Add an else if statement at the end of the if statement. Make sure that the ChoreBot is hiding in the second door!

17.
Lastly, add an else statement to our previous else if statement. Inside the else conditional block, set openDoor1 to beachDoorPath, openDoor2 to spaceDoorPath, and openDoor3 to botDoorPath (the ChoreBot will hide in the third door!).


Hint
Add an else statement at the end of the else if statement. Make sure that the ChoreBot is hiding in the third door!

Starting the Game
18.
Just one more piece of game logic to add to get the game started!

Create a function called startRound at the bottom of script.js. Inside the function, set the src properties of doorImage1, doorImage2, and doorImage3 as closedDoorPath. We want to make sure that all the doors are closed at the start of the game.


Hint
The startRound() function doesn’t take any parameters. Make sure to set doorImage1.src, doorImage2.src and doorImage3.src to closedDoorPath.

19.
We’ve got some more variables to reset to ensure that players can start with a fresh slate. Set numClosedDoors back to 3, currentlyPlaying to true, and the content of startButton element to 'Good Luck!'.

Lastly, run the randomChoreDoorGenerator() function as the last line of the startRound() function block.


Hint
Remember that you can set and get the content of an HTML element using the innerHTML property.

20.
Our game logic is complete. One last thing to do to get the game started—call the startRound() function as the last line of script.js.

Click the “Save” button to run the game. Can you avoid the ChoreBot?


Hint
Make sure to call startRound() as the last line of script.js.