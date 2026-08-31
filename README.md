# App Lab Chess

The world’s first fully functional chess app written in Code.org’s App Lab language.

This was easily my most ambitious App Lab project. I wrote all of the game logic myself, including piece movement, legal-move validation, check and checkmate detection, castling, en passant, pawn promotion, an undo button, and board flipping.

I built this in the summer after 10th grade, after taking AP Computer Science Principles.

## App Functionality

The app lets two players play chess locally by entering moves in coordinate notation.

For example:

```text
e2e4
```

The program converts the input into board coordinates, determines whether the move is legal, updates the board, and checks whether the move leaves the player's king in check.

The board can also be flipped so that either player can view the board from their perspective.

## Program Logic

### Moving Pieces

When a move is entered, the program first determines whether the piece can make that type of move.

For all pieces except the knight, because it is the only piece that can jump over other pieces, the program checks every square between the starting and ending positions to make sure the path is clear.

After a move is temporarily made, the program checks whether the player's king is under attack. If the move leaves the king in check, the board is restored and the move is rejected.

The board is represented as an 8×8 array and stores information about the current game state separately (see undo section for the full details).

### Checkmate

Checkmate detection was one of the more complicated parts of the project.

When a king is in check, the program searches through every piece belonging to that player and tests every possible destination square. Each possible move is temporarily applied to the board and checked to see whether the king would still be under attack.

If at least one legal escape exists, the position is not checkmate. If no legal move can remove the check, the game ends.

### Undo System

The app stores previous game states in `moveHistory`.

Each saved state contains:

* The board position
* Whose turn it is
* The en passant target
* Which pieces have moved
* Information about hidden pieces in the interface

Undoing a move restores the previous state and reconstructs the visual board.

## What I Didn't Implement

There are a few chess rules and features that I intentionally did not implement because they would be quite tedious to add:

* Stalemate
* Threefold repetition
* Other draw conditions
* Time controls
* Underpromotion

Pawn promotion is supported, but every promotion is automatically made into a queen.

So this is **not a complete chess implementation**. It is a playable two-player chess app covering nearly all of the core rules you would see in an actual game.

## Running the Project

### Through Code.org

**Currently maintained project with image fix:** https://studio.code.org/projects/applab/f57c3ad4-659c-4fe6-a96b-1db46230cf88

**Original project:** https://studio.code.org/projects/applab/ScFQU4H8pAZaFy_0r5LxuaGdpPbM21ZxdiKXDrelhDc

The original project is hosted on my high school Code.org account. The email address associated with that account was deleted after I graduated, so I can no longer access it.

### Running Locally

See Code.org's instructions for exporting App Lab projects: https://support.code.org/hc/en-us/articles/13211665878157-Exporting-Projects-from-App-Lab

As the guide states, **you cannot run the project by simply opening the `index.html` file**. Instead, you must run it using a testing server program.

## Other App Lab Projects

This repository originally contained a collection of smaller App Lab projects I made during my freshman and sophomore years of high school.

The chess project is by far the most ambitious of them, but links and/or code to the other projects exist in earlier commits as a record of what I was building at the time.

Other projects included:

* Vacation decision maker
* Create Task project
* Password manager apps
* Several smaller apps
