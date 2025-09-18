# ILBAI-LightUpSolver

A solver for the **LightUp (Akari)** puzzle, utilizing constraint-based logic and a custom grid representation.

## Overview

This project implements a solver for the **LightUp** puzzle (also known as Akari). It enforces all game rules and outputs a visual solution. Compatible with grids generated from [Simon Tatham’s LightUp game](https://www.chiark.greenend.org.uk/~sgtatham/puzzles/doc/lightup.html#lightup).

## Game Rules (Quick Reference)

For full details, see the [official rules](https://www.chiark.greenend.org.uk/~sgtatham/puzzles/doc/lightup.html#lightup).

- All white cells must be illuminated.
- Lights illuminate cells in all four cardinal directions until a black cell blocks the path.
- Black cells with numbers specify how many adjacent lights they require.
- No two lights may illuminate each other.
- Lights can only be placed on white cells.

Test grids are compatible with the online version, allowing verification via embedded links.

## Grid Format

The puzzle grid is represented as a 2D NumPy array with the following values:

| Value | Meaning                      |
|-------|------------------------------|
| `-1`  | White cell (empty)           |
| `-2`  | Black cell (no number)       |
| `0-4` | Black cell with adjacent light count |

### Output Symbols

| Symbol  | Meaning                         |
|---------|---------------------------------|
| `□`     | White cell                      |
| `■`     | Black cell (no number)          |
| `0-4`   | Black cell with number          |
| `★ `    |Light                            |
| `·`    | Illuminated cell (light beam)    |

The light placement array uses:

- `0` = no light at `[i][j]`
- `1` = light placed at `[i][j]`

#### WARNING: DO NOT install "z3" as this is a deprecated AWS package

- This program was tested and run on miniconda 3 and python version 3.11.4 
- It utilizes dowloaded modules of z3, numpy, os, and time
  - All required modules are either included with python or can be dowloaded by running the [installation.py](installation.py) file we have included

Or if you are familiar with "pip" installing modules please run:
```pip install z3-solver numpy```

If you wish to uninstall these packages later, please run ```pip uninstall z3-solver numpy``` or just run [uninstall.py](uninstall.py)

## How to run
1. To run this program, run main.py
2. You should see a prompt in the terminal asking which file number you would like to run
3. Select a prompt and you will see the solver run through the steps to generate a solution to the game
4. You can verify the correctness of the solution through the online link provided at the end of the program

## Creating your own test cases
In order to create yout own test cases, you can create a txt file in the [grids](grids/) folder, from which the program will dynamically read it in and let you run as a test.

The txt file follows the following format:   
- For the array of {} fill in using the numbers from the [key for the grid array](#an-overview-of-some-important-variable-values)  provided above 
- Feel free to add more rows or columns, just ensure that it is rectangular 
- For the seed link, right click on link to puzzle by seed and copy
- For the game id link, right click on link to puzzle by game ID and copy
- Links for the seeds and game id can be found [here](https://www.chiark.greenend.org.uk/~sgtatham/puzzles/js/lightup.html)

#### Disclaimer: It is recommended that you generate a custom-grid with your specifications on the website provided above, copy it using the format below and then press solve to verify with our programs output.

      seed: {insert seed link}
      game_id: {insert game id link}

      {},{},{},{},{},{},{}
      {},{},{},{},{},{},{}
      {},{},{},{},{},{},{}
      {},{},{},{},{},{},{}
      {},{},{},{},{},{},{}
      {},{},{},{},{},{},{}
      {},{},{},{},{},{},{}

Here is a filled out example file below:

      seed: https://www.chiark.greenend.org.uk/~sgtatham/puzzles/js/lightup.html#7x7b20s4d2%23951739128355234
      game_id: https://www.chiark.greenend.org.uk/~sgtatham/puzzles/js/lightup.html#7x7:cBg2c01aBb1e1bBa01cBg0c

      -1,-1,-1,-2,-1,-1,-1
      -1,-1,-1,-1,2,-1,-1
      -1,0,1,-1,-2,-1,-1
      1,-1,-1,-1,-1,-1,1
      -1,-1,-2,-1,-1,-1,-1
      -1,-1,-2,-1,-1,-1,-1
      -1,-1,-1,0,-1,-1,-1

