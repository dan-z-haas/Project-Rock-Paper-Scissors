# Project-Rock-Paper-Scissors

<!DOCTYPE html>
    <head>

    </head>
    <body>
        <script>
            
            function game() {
                do {
                    playRound();               
                } while (round<=5);
                gameOutcome()                
            }
            function playRound() {
                computerPlay();
                playerPlay();
                shoot(playerSelection,computerSelection);
            }
            //variables to set up game
            
            const R = "Rock"; P = "Paper"; S = "Scissors";
            let playerScore = 0, computerScore = 0, playerSelection=undefined, computerSelection=undefined, roundOutcome = undefined, round=1, winner = undefined, rand=undefined;
            
            // gameplay
            function computerPlay() {
                rand=Math.random()
                switch (true) { 
                    case rand <= (1/3):
                    computerSelection = R;
                    break;
                    case rand <= (2/3):
                    computerSelection = P;
                    break;
                    case rand <=1:
                    computerSelection = S;
                    break;
                }
            }
            function playerPlay() {
                playerSelection = capitalize(prompt("Which do you choose: Rock, Paper, or Scissors?"))    
            }
            
            function shoot(playerSelection, computerSelection) {
                switch (true) {
                    case playerSelection == computerSelection :
                        roundOutcome = "It's a tie because you both played the same thing."
                        break;
                    case playerSelection == R && computerSelection == P :
                        roundOutcome = "You lose! Paper beats Rock.";
                        computerScore++;
                        break;
                    case playerSelection == R && computerSelection == S :
                        roundOutcome = "You win! Rock beats Scissors.";
                        playerScore++;
                        break;
                    case playerSelection == P && computerSelection == R :
                        roundOutcome = "You win! Paper beats Rock.";
                        playerScore++;
                        break;
                    case playerSelection == P && computerSelection == S :
                        roundOutcome = "You lose! Scissors beats Paper.";
                        computerScore++;
                        break;
                    case playerSelection == S && computerSelection == R :
                        roundOutcome = "You lose! Rock beats Scissors.";
                        computerScore++;
                        break;
                    case playerSelection == S && computerSelection == P :
                        roundOutcome = "You win! Scissors beats Paper.";
                        playerScore++;
                        break;
                };
                alert("You chose " + playerSelection + ".  Your opponent chose " + computerSelection + ".  " + roundOutcome);
                alert("The score at the end of round " + round + " is " + playerScore + " - " + computerScore + ".");
                round++;
            }
            function gameOutcome() {
                outcomeMessage = playerScore<computerScore ? "You Lose!" : "YOU WIN!";
                alert("The final score is " + playerScore + " - " + computerScore + ".  "  + outcomeMessage);
            }
            //Features: Player may type in any case
            function capitalize(string) {
                let initial=string.slice(0,1);
                let afterInitial=string.slice(1);
                return initial.toUpperCase() + afterInitial.toLowerCase();
            }
        </script>
    </body>
</html>
