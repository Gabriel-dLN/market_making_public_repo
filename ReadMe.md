# Automated Market Making on Kalshi soccer games

This repository presents the motivations and results of my project.

There are, for now, two main parts:
- Simulation Framework
- Market Making Algorithm Research


# Concepts
Soccer games have 3 possible outcomes within the 90 minutes of the game: team 1 wins, team 2 wins, or it's a draw. Each outcome is called a "market".


Let's take an example:

<p align="center">
	<img src="images/psg_che.png" alt="PSG vs Chelsea" width="15%">
</p>

At the time I'm writing this, the best bid/ask prices are:
| Market | Bid | Ask |
|--------|-----|-----|
| PSG    | 50  | 51  |
| CHE    | 26  | 27  |
| TIE    | 24  | 25  |

There are 2 different ways to make the spread on these markets:
- You sell PSG wins at 51¢, buy PSG wins at 50¢ and you immediately earn 1¢ - ignoring fees for now.
- You sell PSG wins for 51¢, Chelsea wins at 27¢ and Tie at 25¢, you now have $1.03. At the end of the game, you will owe $1 because Kalshi markets settle at $1 if the bet was correct, and you earn 3¢ at settlement. This is one way to earn sort of a "3D" spread.




# Visualizing the makets

Let's look at the game between Atletico Madrid and Real Madrid that started at 7pm on January 8th 2026.


<p align="center">
    <img src="images/atm_rma_summary.png" alt="ATM vs RMA summary" width="40%">
</p>

This graph below shows the evolution of the price of the "Real Madrid is going to win" contract. You can see the price jumps when goals get scored.

![ATM vs RMA time series](images/atm_rma_time_series.png)

To understand the graph better, we can zoom:

![ATM vs RMA time series zoomed](images/atm_rma_time_series_zoomed.png)

The sudden jump and fall is due to the 2 goals that happened at the 55th and 58th minutes.


# Simulation Framework

I built a high-fidelity simulation engine that allows:

- To record Kalshi markets' order books and trades by connecting to the exchange's websocket streams and deliver it to a well organized a data pipeline.
- To replay a game and plug a market making algorithm that interacts with the order books, taking into account the latency of sending and receiving quotes / trade events.

The second point was by far the most challenging one.



# Approach

Market making during a soccer game requires premium subscriptions to professional data providers like Opta, ESPN or Sportradar, and can cost up to tens of thousand of dollars. Without it, it is very challenging to do anything without taking too many risks as you'll constantly have stale information compared to the hedge funds that are designated market makers.

That's why I chose to focus on the period before soccer games start, that way I can play on equal terms with other market participants.


# Some strategies' results





WOL MUN

Aiming have it ready to trade with real money before the 2026 FIFA World Cup.











# Appendix
This project is for research purposes only.
