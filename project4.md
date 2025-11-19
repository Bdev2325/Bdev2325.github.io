[Back to Portfolio](./)

Project 4 Battleship
===============

-   **Class:** CSCI 235
-   **Grade:** 90 (A)
-   **Language(s):** C ++
-   **Source Code Repository:** [Source Code](https://github.com/Bdev2325/SeniorPortfolioSourceCode4/blob/main/README.md) 
    (Please [email me](mailto:bjcooper2@csustudent.net?subject=GitHub%20Access) to request access.)

## Project description

This project is a console-based implementation of the classic Battleship game, where a human player battles against an AI-controlled enemy fleet on a 10×10 grid. The game manages different ship types (Aircraft Carrier, Battleship, Submarine, Destroyer, and Patrol Boat) with distinct sizes and hit tracking, and ends when either the player’s or the enemy’s entire fleet has been sunk. The enemy uses a probability-based AI: it builds a probability matrix of likely ship positions using previous hits and misses, then chooses the next target from the highest-probability cells. This makes the computer significantly smarter than random guessing and provides a challenging single-player experience.

## How to Compile and Run the Program


Prerequisites

Make sure the following files are in the same folder:

Battleship.cpp
GameSpecs.hpp
EnemyAI.hpp

Step 1 – Compile

install g++ in you environment and run the following command:

```
g++ -std=c++17 Battleship.cpp -o battleship
```

This produces the executable file. The headers EnemyAI.hpp and GameSpecs.hpp are included directly by Battleship.cpp, 
so you only need to compile the Battleship.cpp file.

Step 2 – Execute the program

Execute the following command:

```
./battleship

```



## UI Design

The game runs entirely in the terminal and displays two grids side-by-side: the enemy’s fleet on the left and your fleet on the right. Rows are labeled A–J and columns 1–10. Your board shows your ships using letters (A, B, S, D, P), water as ., misses as ~, and hit ship tiles as lowercase letters (a, b, s, d, p). 

The enemy board normally hides ship positions: unknown tiles are shown as ., your misses as ~, and your successful hits as X. At the end of the game (or when showAll is enabled), the enemy’s full layout is revealed using the same symbol scheme as your board, with lowercase letters marking hit sections of ships. Input is coordinate-based (e.g., B2), and the game prints clear messages such as “Hit!”, “Miss.”, and “You sunk the enemy’s Battleship!” to keep the player informed of the game state.


[Back to Portfolio](./)
