# Game Document

## Game Mechanics

### Tile-Based Coding System

#### Windows

- **Tile-Window**: Acts like a virtual keyboard containing code tiles.
- **Code-Window**: Functions as the code editor where tiles are connected to write code.

#### Tile Connection Rules

- Each level provides a limited set of tiles based on the current concept.
- When a new programming concept is introduced, its related tiles are **unlocked**.
- Unlocked tiles appear in the Tile-Window starting in levels that follow the concept's introduction.
- Unlocked tiles will remain unlocked and available for the rest of the game.
- Clicking a tile moves it into the Code-Window:
  - If the Code-Window is empty, it becomes the first tile.
  - If not, it connects to the last tile in sequence.

#### Example

In early levels:

- Level 1: Introduces **Variables** and **Data Types**.
- Level 5: Introduces **Math Operators**.

Each concept is followed by several levels (practice, challenge, or story-based) that reinforce that concept.

#### A lot of Tiles

By the player concept progression, tiles will be a lot and hard to track of, find specific tiles.
by adding **Searching** functionality, player can find a specific tile for a syntax easily.
the **Searching** will be implemented as **Fuzzy finder**.

## Turn-Based Gameplay

### Code Execution

- Players click the **Run** button to execute their connected tiles.
- Errors and warnings are shown in the Output-Window.
- Valid code triggers effects based on the level’s scenario:
  - Correct code might **damage an enemy**, **buff the player**, or **solve a puzzle**.
- Invalid code results in **enemy attacks**.

#### Invalid Code AKA Exceptions

Exceptions will be used as an action for the enemy to attack the player.

There are already predefined exceptions in Python, including runtime errors and compile/interpreter time errors.
SyntaxError is one example of an exception.

#### Successull Code Execution

Python concepts to define an action for the player to attack the enemy.

Different concepts will be used to calculate the overall value of the defined values for each concept, such as if-else, variables, loops, and so on.
The thing is, calculating the overall value of each concept might result in an overkill or instant kill offensive attack on the enemy.

So, we can do the opposite: the more concepts used in the code, the less overall offensive damage will be inflicted on the enemy.

### Turn Order

- The game is **turn-based**, and the **player always moves first**.
- The enemy will take turn after the player runs their code.
- Player and enemy both have **health points (HP)**.
- Reaching 0 HP resets the current level's state, including connected tiles.

## Story and Level Design

### Level Types

Each level is centered around a **programming concept** and includes:

- **Story Context**
- **Unique Challenges**
- **Entities** (either Enemies or Allies)

#### Entities

- **Allies**: Introduce new concepts and provide guidance.
- **Enemies**: Represent coding challenges.
- **Bosses**: Require solving problems (e.g. algorithms, data structures).

## Feedback and Error Handling

### Analysis

- Tile connection is **not** turn-based — players can connect or remove tiles freely, much like can do with typing codes with keyboard.
- A built-in code analyzer (like a compiler) checks syntax and displays feedback, after a brief pause of the user(without doing any modification to code).

  The Analyzer will be execute after 1.5 seconds of user inactivity.

### Help System

1. **Hints & Tips**
   - Offers suggestions for fixing syntax errors.
   - Inspired by Rust’s Error ID system.

2. **Real-Time Error Messages**
   - Displays messages during tile connections to guide the player toward correct syntax.

## Progression Features

### Battle Boosters

Boosters help players during combat:

- **Player Resurrection** – Revives the player if defeated.
- **Syntax Shield** – Blocks damage from failed code runs.

### Enhanced Coding Speed

To avoid tedious tile placement, players unlock **tile compression** after mastering concepts:

#### Example: Tile Merging

Before compression:

`if` - `__name__` - `=` - `=` - `"` - `__main__` - `"` - `:` - *newline* - `Indent`

After compression:

`if` - `__name__ == "__main__":` - *newline* - `Indent`

> After a string quote (`"`), the next tile behaves like string content.

This speeds up code writing in later levels.

This function will be applied after the Player becomes proficient on using a specific syntax.
> so if the player becomes proficient on using/making strings, the compression will be applied to `"`.

## Tracking and Analytics

### Concept Mastery Reports

Tracks player understanding of:

- Variables
- If-statements
- Loops
- Other core concepts

Players earn "mastery" after repeated correct usage or challenge completion.

### Level Completion Tracking

Logs:

- Completed levels
- Encountered enemies
- Collected items
- Player-written code

## Online Features (Supabase)

### Achievements & Milestones

Players skins which can be earned by:

- Completing concepts
- Completing levels
- Earning achievements

### Leaderboards

Ranks players based on coding performance.

#### Leaderboard Types

1. **Level Leaderboards** – Rank players by speed, accuracy, and efficiency on each level.
2. **Concept Leaderboards** – Rank players based on how well they perform in specific programming concepts.
3. **Global Leaderboard** – Ranks overall coding skill across the entire game.

### Account System

- **Authentication**: Players can register accounts
- **Data Sync**: Progress, unlocks, and settings saved online
- **Multiple Device Access**: Play on multiple Phones — progress stays synced

### Player Profiles

Each profile includes:

- Achievements
- Ranking (per level, per concept, global)
- Concept Mastery
- Fastest level times
- Total code written
