# Number Guessing Game - Code review

## Introduction

Our code review is based on the project name \"Number guessing game\". It is a simple and interactive made of HTML (Hyper Text Markup Language), CSS (Cascading Style Sheet) and JS (JavaScript) that challenges the user to guess a number in a given chances. After each attempts the game provides a feedback of such as \"Too high\" or \"Too low\" after each attempt until the correct answer is found in the given chances. 

 This code review emphasizes on the structure and readability of the code, the logic used and the program flow control, input validation, replayability, user experience and the use of constants on the code. Our goal is to assess how well the code is organized and whether the code supports maintenance and follow the good programming practices.

  

### 1. Code Readability and Structure

The code is generally simple and easy to follow. The variables used on the code are relevant to their specific actions which improves readability. Also the indentation used on the program is consistent it follows good programming practices. The code is also separated in functions `checkGuess()`, `setGame()`, `resetGame()` which helps readability and makes the flow clear.

```javascript

// Constants for easy modification later

const MAX_VALUE = 100;

const MAX_ATTEMPTS = 10;

// Function to generate a random number

function generateRandomNumber(max) {

// Game variables

let randomNumber = generateRandomNumber(MAX_VALUE);

const guesses = document.querySelector(".guesses");

const lastResult = document.querySelector(".lastResult");

const lowOrHi = document.querySelector(".lowOrHi");

const guessSubmit = document.querySelector(".guessSubmit");

const guessField = document.querySelector(".guessField");

let guessCount = 1;

let resetButton;
}
//Function that checks the user's guess and gives feedback

function checkGuess() {

// Disables inputs and creates a reset button when the game ends
}
function setGameOver() {

// Resets all values and starts a new game
}
function resetGame() {

// Generate a new random number for the new game

randomNumber = generateRandomNumber(MAX_VALUE);
}
```

### 2. Code Logic and Flow

The positive side that we understand from the game code is that the game gives correct response to the user’s guesses as we can see from the following section of the JS code of the game:

- `if (userGuess === randomNumber)` — detects correct guess
- `if (guessCount === 10)` — ends game after 10 attempts
- `if (userGuess < randomNumber)` — guess is too low
- `if (userGuess > randomNumber)` — guess is too high

This helps for:

- Correct detection of too high, too low or correct
- The game to stop after 10 attempts, which prevents infinite loops.

#### There is no major logical weakness here in the code.

### 3. Input Validation

The major problem that we observed in the code under input validation is that the code doesn’t check whether the user entered a number inside the valid range (1-100).

**Example** - If the user enters value of 500 the game takes it as too high and responds “wrong” rather than telling the user to enter valid input.

To solve this problem we need to add the following **range validation** at the start of `checkGuess()` function:

```javascript
if (userGuess < 1 || userGuess > 100) {
  lastResult.textContent = "Please enter a number between 1 and 100.";
  lastResult.style.backgroundColor = "orange";
  guessField.value = "";
  guessField.focus();
  return;
}
```

Solving these issue helps to prevent invalid inputs from entering to the game flow

### 4. Replayability

The game allows for players to play again if they win or lose the game, this improves the level of user experience. Instead of refreshing the page everytime the game ends the game resets properly.

The function `setGameOver()` disables input fields and buttons when the game ends And the function a “Start new game” button appears allowing the player to restart without reloading the page. Then `resetGame()` function resets the guess count, message fields, input box, and regenerates a new random number thereby creating a new session of game for the player.

There is no major improvments the code need in this criterion but also our team has noticed that the “**Start new game**”button could be more styled to improve the user interface as shown below:
By adding this styling option on the css:

```css
.reset-btn {
  background-color: #4caf50;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  margin-top: 15px;
}
```

And since the button is created on the javascript side (dynamic) we need to link them with the css class as shown:

```javascript
resetButton.textContent = "Start new game";
resetButton.classList.add("reset-btn");
document.body.appendChild(resetButton);
```

### 5. User Experience
From the user experience view we found the game as good on informing the player that their guesses are too high/ too low or correct, and the game also displays clear message when the game is over and when they win. And the background color changes on result to make feedback visual by including the following JS code line:
```javascript
lastResult.style.backgroundColor = "green";
lastResult.style.backgroundColor = "red";
```
But there are some possible enhancements that we suggest to be included:

-	Show the number of attempts the user left. To do this we need to include the following JS code line into the guess-processing part:
```javascript
lowOrHi.textContent += ` — You have ${10 - guessCount} guesses remaining.`;
```

-	Showing the actual answer when the game ends. 

### 6. Use of Constants
The code works perfectly but it uses hardcoded values (also called magic numbers) such as:
```javascript
Math.random() * 100
if (guessCount === 10)
```
These numbers make the code less flexible if we want to change the guessing range of the numbers, so instead it’s better to define these numbers as constants to update them later on to improve maintainability.
```javascript
const MAX_VALUE = 100;
const MAX_ATTEMPTS = 10;
let randomNumber = Math.floor(Math.random() * MAX_VALUE) + 1;
```
### 7. Efficiency
When we observe the code efficiency there were no unnecessary loops, DOM lookups are stored in variables and the game logic runs only when it is needed which makes it more efficient. 

But we give minor suggestion that can be added, which is that instead of rebuilding the entire guess history string each time which uses the following JS code line:

```javascript
guesses.textContent ='${guesses.textContent} ${userGuess}' ;
```
We can use the following line to make it more clean and efficient:

```javascript
guesses.textContent += '${userGuess}';
;
```
## Conclusion
This code analysis for the "Number Guessing Game" project finds that the code is well-organized, easy to understand, and does exactly what it’s supposed to. The code also reflects good programming standards in terms of logical flow, use of functions, and optimization.

However, certain regions could improve the project. Input validation could use improvement when it comes to edge situations, while using constants instead of hard-coded values can improve flexibility. The project can also improve through small UX and interface modifications.

Such modifications will enable the code to be more maintainable, user-friendly, and easier to modify in the future. The project clearly reflects a strong understanding of HTML, CSS, and JavaScript basics in creating an interactive experience for users to enjoy.


# Group members:

##  &nbsp;&nbsp; &nbsp;&nbsp;Name&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;                                      ID. NO

1. Yeroson Bekele&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    	ETS1449/16
2. Yidnekachew Zerihun&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	&nbsp;&nbsp;	&nbsp;&nbsp;            	ETS1455/16
3. Yonas Begashaw&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;		&nbsp;&nbsp;	&nbsp;&nbsp;            	ETS1493/16
4. Yonas Demise	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;		                ETS1495/16
5. Yonas Zegeye&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;			                ETS1503/16
6. Yoseph Asrat&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;		                	ETS1535/16

