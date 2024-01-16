# Recreation of "Prisoner's Dilemma" inspired by Veritasium YouTube Channel

This is a repository inspired by the youtube video:

[![Veritasium_Video](http://img.youtube.com/vi/mScpHTIi-kM&ab_channel=Veritasium/0.jpg)](http://www.youtube.com/watch?v=mScpHTIi-kM&ab_channel=Veritasium "What The Prisoner's Dilemma Reveals About Life, The Universe, and Everything")


Where the goal is to recreate the Game described in the video where we create:

- 1v1 Game of Cooperation vs Exploitation
- 16 Different Players (Strategies)
- Tournament Set Up: Number of Matches
- Game Set Up: Number of Games per Match

And with this building blocks, we create different Game Styles as the one described in the game.

The repository, at the beginning will be a mix of jupyter notebooks with trials and errors and later, once things are created, then I'll arrange it into python files.

Full Disclosure, I'm using ChatGPT to help me build the code. 


16.01.2024 ------------
I wrote a new Game Class where we have a history vector initialized for each player, and variables to keep track of rounds played, rounds remaining as I think I will need them in the future:

:::python
class Game:
    def __init__(self, player1, player2, rounds=10):
        
        # Setting the numbers of rounds
        self.rounds = rounds

        # Setting the number of rounds left
        self.rounds_remaining = rounds

        # Setting the number of rounds remaining
        self.rounds_played = rounds - self.rounds_remaining

        # Creation of two players
        self.player1 = player1
        self.player2 = player2

        # Setting the decision tracking for each of the two players
        self.history_p1 = np.empty(self.rounds, dtype=object)
        self.history_p2 = np.empty(self.rounds, dtype=object)

        # Setting the scores for the two players
        self.scores = {"P1": 0, "P2": 0}
:::


And create a class of a player that recieves as input the player and opponent history.
:::python
class Player_Random:
    def __init__(self, player_history, opponent_history, rounds_remaining, rounds_played):
        choices = ["C", "D"]
        self.choice = choices[random.randint(0, 1)]
:::

I think the code might not be working well with more complex strategies but the logic that recieves as input a full history it makes sense. 
Probably it doesn't scale very well with a game round of 2,000,000,000 I have to limit the number of maximum rounds available. 
However, for a maximum of 200 I think is doable.



14.01.2024 ------------
I was able to create easily this scenario using ChatGPT:
#### First Trial
- Player0 = Random Choice
- Player1 = Always Cooperate
- Player2 = Always Exploit

However when I added a more "complex" player then I got errors because it the Game Class was not supporting them.
I'll try to explore it a bit more in the following Trials

