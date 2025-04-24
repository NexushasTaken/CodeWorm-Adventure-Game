# CodeWorm: Coding Adventure

---

## Game Overview

**CodeWorm** is a tile-based coding RPG that teaches programming through turn-based combat and story-driven levels. Players write code by connecting syntax tiles, solve challenges, and battle enemies based on core programming concepts.

---

## Game Mechanics

### Tile-Based Coding System

#### Windows

- **Tile-Window**: Acts like a virtual keyboard containing code tiles.
- **Code-Window**: Functions as the code editor where tiles are connected to write code.

#### Tile Connection Rules

- Each level provides a limited set of tiles based on the current concept.
- When a new programming concept is introduced, its related tiles are **unlocked**.
- Unlocked tiles appear in the Tile-Window starting in levels that follow the concept's introduction.
- Clicking a tile moves it into the Code-Window:
  - If the Code-Window is empty, it becomes the first tile.
  - If not, it connects to the last tile in sequence.

#### Example

In early levels:
- Level 1: Introduces **Variables** and **Data Types**.
- Level 5: Introduces **Math Operators**.

Each concept is followed by several levels (practice, challenge, or story-based) that reinforce that concept.

---

## Turn-Based Gameplay

### Code Execution

- Players click the **Run** button to execute their connected tiles.
- Errors and warnings are shown in the Output-Window.
- Valid code triggers effects based on the level’s scenario:
  - Correct code might **damage an enemy**, **buff the player**, or **solve a puzzle**.
- Invalid code results in **enemy attacks**.

### Turn Order

- The game is **turn-based**, and the **player always moves first**.
- Player and enemy both have **health points (HP)**.
- Reaching 0 HP resets the current level's state, including connected tiles.

---

## Story and Level Design

### Level Types

Each level is centered around a **programming concept** and includes:

- **Story Context**
- **Unique Challenges**
- **Entities** (either Enemies or Allies)

#### Entities

- **Enemies**: Represent coding challenges.
  - Each enemy's behavior is tied to the concept of the level.
  - Example: In Level 1 (Variables), the enemy is a Slime. The player revives by assigning `health = 100`, which hurts the Slime.
- **Allies**: Introduce new concepts and provide guidance.
- **Bosses**: Require solving advanced problems (e.g. algorithms, data structures).

---

## Feedback and Error Handling

### Real-Time Analysis

- Tile connection is **not** turn-based — players can connect or remove tiles freely.
- A built-in code analyzer (like a compiler) checks syntax instantly and displays feedback.

### Help System

1. **Hints & Tips**
   - Offers suggestions for fixing syntax errors.
   - Inspired by Rust’s Error ID system.

2. **Real-Time Error Messages**
   - Displays messages during tile connections to guide the player toward correct syntax.

---

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

---

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

---

## Online Features (Supabase)

### Achievements & Milestones

Players unlock:
- Cosmetic skins
- Titles
- Trophies

Earned by:
- Finishing levels
- Mastering concepts
- Solving difficult problems

### Leaderboards

Ranks players globally by:
- Speed
- Accuracy
- Coding efficiency

### Account System

- **Authentication**: Players can register accounts.
- **Data Sync**: Progress, unlocks, and settings are saved to the cloud.
- **Cross-Device Access**: Play on PC, phone, or tablet — progress stays synced.

### Player Profiles

Each player has a profile showing:
- Achievements
- Ranking
- Concept Mastery
- Fastest level times
- Total code written

---

## Main UI Design
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/Main UI Design - Dark.png">
  <source media="(prefers-color-scheme: light)" srcset="assets/Main UI Design - Light.png">
  <img alt="Shows a black logo in light color mode and a white one in dark color mode." src="assets/Main UI Design - Dark.png">
</picture>