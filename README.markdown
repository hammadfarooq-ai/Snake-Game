# Snake Game Documentation

This document describes a classic Snake game implemented using Python and the Pygame library. The game features a snake that moves around the screen, eats food to grow longer, and ends if it collides with itself or the screen boundaries.

## Overview

- **Objective**: Control the snake to eat food (green squares) to grow longer while avoiding collisions with the screen edges or the snake's own body.
- **Controls**:
  - Arrow keys (Left, Right, Up, Down) to change the snake's direction.
  - Press `Q` to quit or `C` to restart when the game is over.
- **Game Mechanics**:
  - The snake moves continuously in the current direction.
  - Eating food increases the snake's length and spawns new food at a random location.
  - The game ends if the snake hits the screen boundaries or collides with itself.
  - The game runs at a fixed speed (30 frames per second).

## Code Structure

The code is organized into several key components:

### 1. **Initialization**
- **Pygame Setup**: Initializes Pygame and sets up a display window of 800x600 pixels.
- **Colors**: Defines colors used in the game (white, yellow, blue, red, green, black).
- **Constants**:
  - `dis_width = 800`, `dis_height = 600`: Screen dimensions.
  - `snake_block = 10`: Size of the snake and food squares.
  - `snake_speed = 30`: Frames per second, controlling game speed.
- **Fonts**: Uses `SysFont` for rendering game-over messages and scores.

### 2. **Helper Functions**
- **`our_snake(snake_block, snake_list)`**:
  - Draws the snake on the screen by iterating through `snake_list` (a list of coordinates) and drawing a rectangle for each segment.
  - Each segment is a black square of size `snake_block`.
- **`message(msg, color)`**:
  - Renders a text message on the screen at a fixed position (`dis_width / 6`, `dis_height / 3`).
  - Used to display "You lost!" with options to quit or replay.

### 3. **Main Game Loop (`game_loop`)**
- **State Variables**:
  - `game_over`: Controls whether the game should exit.
  - `game_close`: Indicates if the game is in the "game over" state (showing the retry/quit prompt).
  - `x1`, `y1`: Snake's head position (starts at the center of the screen).
  - `x1_change`, `y1_change`: Movement offsets for the snake's head.
  - `snake_List`: List of coordinates representing the snake's body.
  - `Length_of_snake`: Tracks the snake's length (increases when food is eaten).
  - `foodx`, `foody`: Coordinates of the food, randomly placed on a 10x10 grid.
- **Game Logic**:
  - **Event Handling**: Processes `QUIT` events (to close the window) and `KEYDOWN` events (to change direction or handle game-over inputs).
  - **Movement**: Updates the snake's head position based on `x1_change` and `y1_change`.
  - **Collision Detection**:
    - Checks if the snake hits the screen boundaries (`x1`, `y1` outside `dis_width` or `dis_height`).
    - Checks if the snake's head collides with its body (head matches any segment in `snake_List`).
  - **Food Interaction**: If the snake's head reaches the food's position, the snake grows, and new food spawns.
  - **Rendering**: Clears the screen (filled with blue), draws the food (green square), draws the snake, and updates the display.
  - **Timing**: Uses `clock.tick(snake_speed)` to maintain consistent game speed.

### 4. **Game Over Handling**
- When `game_close` is `True`, the screen displays a "You lost!" message.
- Players can press `Q` to quit the game or `C` to restart by calling `game_loop()` again.

## How to Run
1. Ensure Python and Pygame are installed (`pip install pygame`).
2. Save the code in a `.py` file (e.g., `snake_game.py`).
3. Run the script using Python: `python snake_game.py`.
4. Use arrow keys to control the snake, and `Q` or `C` at the game-over screen.

## Limitations
- No score display or high-score tracking.
- Fixed snake speed and no difficulty levels.
- Basic collision detection (snake dies if it touches itself or the boundary).
- No pause functionality or menu system.

## Potential Improvements
- Add a score counter and display it on the screen.
- Implement increasing difficulty (e.g., speed increases as the snake grows).
- Add a start menu or pause feature.
- Include sound effects or background music.
- Add different types of food or obstacles for variety.