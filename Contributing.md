# Intoduction
## Project Name: GuessGame for numbers
A "Guess the Number" game, often implemented as a simple interactive program, is a classic game where the computer selects a random number within a specified range, and the player tries to guess what that number is. The game provides feedback on each guess, indicating whether the actual number is higher or lower than the player's guess, helping the player narrow down the possible options based on previous guesses. The game continues until the player guesses the number correctly or exhausts a certain number of attempts.
### Key Feaures
*Random Number Generation: The core of the game is the computer's ability to select a random number within a specified range (e.g., 1 to 100). This introduces unpredictability and makes each game session unique.

*User Interaction: Players interact with the game by inputting guesses. This straightforward form of interaction is easy to understand and accessible to players of all ages.

*Immediate Feedback: After each guess, the game provides immediate feedback, informing the player whether their guess was too high, too low, or correct. This feedback loop is crucial for keeping the player engaged and guiding them toward the correct answer.

*Win Condition: The game clearly defines its win condition - guessing the correct number. Achieving this goal gives the player a sense of accomplishment.

*Attempt Tracking: The game can track the number of attempts a player makes, offering additional challenges (e.g., trying to guess the number in the fewest attempts possible) and facilitating a scoring system.

*Difficulty Levels: By adjusting parameters such as the range of the random number or the number of allowed attempts, the game can offer varying levels of difficulty, making it accessible for beginners and still challenging for advanced players.

*Replayability: Due to its random nature and the ability to adjust difficulty, the game has high replay value. Players can try to improve their performance in subsequent rounds.

*Learning Tool: For programming students, the game serves as an excellent learning tool for understanding basic concepts such as loops, conditionals, variable handling, and user input/output.

*Extendability: While simple at its core, the game can be extended with additional features such as leaderboards, multiplayer modes, hints, or time limits, allowing for more complex gameplay and learning opportunities.

*Portability: The game can be implemented in virtually any programming language and runs on a wide range of platforms, from web pages to desktop applications, making it widely accessible.
### Link
https://github.com/Aawofeso/aawofesoguess-game
### Summary of issues examined
I worked on the isssue which was ensuring that thr number inputed had to be in the range of the game difficulty selected
### Detailed discussion of issues contributed to
I worked on the issues ensuring that the number entered by the player was within the appropriate range for the selected difficulty level in the guessing number game. I wanted to allow players to choose from easy, medium, and hard levels, each with its own range of numbers to guess from. Ensuring players didn't enter numbers outside these specified ranges was crucial to keeping the game fair. 
#### Code Showing changes made to implement solution to issue
HTML
```html
<button id="gbtn" class="btn btn-danger text-uppercase">Guess</button>
                    <div class="warning text-white" id="warningText"></div>
```
CSS
```css
/* Guess button disabled state */
#gbtn[disabled]
{
    color: #ccc;
}
```
JAVASCRIPT
```Javascript
// add listener to input field 
    document.getElementById('gno').addEventListener('blur', function() {
        validateInput();
      });

    /* validate range according to level */ 
    function validateInput() {
        var inputNumber = parseInt(document.getElementById('gno').value);
        var selectedLevel = getSelectedLevel();
        //alert(selectedLevel+" - "+inputNumber);
    
        if (isNaN(inputNumber)) {
          displayWarning("Please enter a valid number");
        } else if (selectedLevel === 0 && (inputNumber < 0 || inputNumber > 1)) {
          displayWarning("For Easy level, enter a number between 0 and 1");
        } else if (selectedLevel === 1 && (inputNumber < 0 || inputNumber > 100)) {
          displayWarning("For Medium level, enter a number between 0 and 100");
        } else if (selectedLevel === 3 && (inputNumber < 0 || inputNumber > 1000)) {
          displayWarning("For Hard level, enter a number between 0 and 1000");
        } else {
          hideWarning();
          enableSubmitButton();
        }
      }
      // Get selected level
      function getSelectedLevel() {
        var levelRadios = document.getElementsByName('radio');
        
        for (var i = 0; i < levelRadios.length; i++) {
          if (levelRadios[i].checked) {
            return parseInt(levelRadios[i].value);
          }
        }
        return -1; // No level selected
        
      }

      function displayWarning(message) {
        var warningText = document.getElementById('warningText');
        warningText.innerHTML = message;
        warningText.style.display = 'block';
        disableSubmitButton();
      }
      function hideWarning() {
        document.getElementById('warningText').style.display = 'none';
      }

      function enableSubmitButton()
      {
        document.getElementById('gbtn').disabled = false;
      }
      function disableSubmitButton()
      {
         document.getElementById('gbtn').disabled = true;
      }
```
### Reflection
I had to figure out how to set the correct range for each difficulty level and display helpful messages to players if they entered a number outside that range. By addressing these issues, I ensured the game ran smoothly and remained enjoyable to play, regardless of the difficulty level chosen by the players.
