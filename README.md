# Simulation Final Project

Course: ISYE 6644 Simulation
Student Name: Ray Echevarria
Project: Blackjack Simulation

Project Code Concept:
In this project the intent is to simulate many rounds of a Blackjack card game to better understand probability of outcomes for these games and test various strategies. Through many simulations there is an opportunity to collect data from the simulated rounds and analyze the game outcome probabilities from various angles. This also introduces opportunities to further refine some of the tested strategies. Additionally, the code's standard strategy is following the Blackjack strategy as laid out here https://bicyclecards.com/how-to-play/blackjack/. 

Project Code Contingencies and Considerations:
The provided code simulates a very simple round of a Blackjack game, in order to simplify the game while still maintaining the mechanics of the game, the following adjustments were made:
- The standard strategy for the simulation follows the rules laid out here: https://bicyclecards.com/how-to-play/blackjack/.
- This simulation does not incorporate monetary considerations, it instead purely looks at the outcomes of a game, Win, Lose, Draw.
- The standard strategy tested only utilizes 1 deck of cards, even though the code can handle multiple decks.
- The simulation only considers the dealer and one player .
- The simulation does not handle a double-down, this is because the simulation is intended to collect game outcomes and not monetary gains, doubling down is essentially the player hitting one last time and doubling their bets. 
- The simulation does not handle splits, this is because splits simply create another hand to play with which may change outcomes of a game, therefore splits are not considered.
- The simulation does not handle cases where either the player or the dealer starts with or ends up in a case where they have 2 or more A's in their hand. This opens up the logic to extensive decision making due to the fact that an A can count as a 1 or an 11. Because this case is a very rare instance it would not be counted in the simulation.

Various Tested Strategies:
- The first simulated strategy is the standard strategy for the simulation follows the rules laid out here: https://bicyclecards.com/how-to-play/blackjack/.
- The second change to the simulation was playing the standard strategy but instead of playing with 1 deck, playing with 6 decks.
- The third change to the simulation is deciding when to stop asking for more cards from the player's decision point of view, this strategy considers stopping after the player has reached a combination of cards totaling 16 or more.
- The third change to the simulation is deciding when to stop asking for more cards from the player's decision point of view, this strategy considers stopping after the player has reached a combination of cards totaling 18 or more.

Code Functionality Walk-through:
1. Dependencies are imported
2. Simulation counter is set to determine the number of simulations to run through
3. Before the code  starts running through the simulation the first occurrence is initializing empty arrays to capture data points
4. The code then starts going through the simulation where a fresh deck is initialized and empty player and dealer hands
5. The simulation then moves to deal the first card to the player, then the dealer's face-up card, then the player's second card and lastly the dealer's face-down card.
6. Once the cards are dealt the player begins to make their decision completely based on what the dealer's face-up card is showing. This is where the strategy as laid out in https://bicyclecards.com/how-to-play/blackjack/ gets implemented for decision making on the player's behalf. 
7. First the logic goes through determining whether there are A's in either the player's or dealer's hand since that triggers a special logic case. If there are no A's detected it goes through the regular strategy decision making. This is all handled within a while loop to determine that at least the minimum requirement is met, once it is met the decision making breaks out of the loop, otherwise it stays in the loop.
8. Next, the simulation evaluates how to handle a detected A in the player's hand while the dealer is not showing an A. It must then consider, within this logic, which is the optimal play based on the fact that an A can count as 1 or 11 so it is looking to meet the minimum requirements of the strategy which is reach at least 17 or having busted beyond 21.
9. Next, the simulation needs to handle the case where the player does not contain an A in their hand but the dealer is showing an A in their hand. This again relies on the standard strategy where a player must meet the minimum requirement and have at least a 17, other wise they must keep asking for cards until that logic is met.
10. The last case the simulation must handle is something that must be met due to the code's architecture, in which the dealer's face-down card is an A but their face-up card isn't. The player's decision in this instance doesn't change to the first decision walk-through [point 6-7] because the player at this point does not know what the dealer's face-down card is, this is what gives the dealer (or often referred to as the house) the upper hand in the game. This finalizes the possible decision making flows a player can make.
11. Once the player's decision making flows are finalized the dealer shows their face-down card and begins to make certain decisions based on the house rules, this is typically stopping the dealer from pulling cards once their card combinations is greater than or equal to 17. 
12. The way the simulation then handles the dealer's decision is simply based on whether or not they have an A in their entire hand. If they don't then they will draw cards until they have met the minimum requirement which is a combination equalling 17 if this has not yet been met. 
13. If an A is detected in the dealer's hand then it considers whether the A being worth 1 or 11 meets the minimum requirement, if not then it draws cards until the minimum requirement is met.
14. Anything more than what is laid out in this logic for both player and dealer would be a bust, meaning they went over the maximum card value allowed of 21.
15. The last logic pass-through the simulation must make is to determine the game outcome, once the outcome is decided the simulation stores the outcome in the initialized array as detailed in point 3.
16. Lastly, once the simulation has gone through the amount as specific in point 2 the stored data is formatted, converted to table format and saved as a CSV file. This will be used to perform the final analysis.
