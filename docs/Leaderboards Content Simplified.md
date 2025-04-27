# Leaderboard Metrics

## Per-Level Metrics

### Speed
**Description**: Time taken to finish the level  

**Calculation**:  

$\text{Speed} = \text{End Time} - \text{Start Time}$  

**Rules**:  
- Only valid if the final submitted code has no errors  
- Measured in seconds  
- Lower values are better  

### Accuracy  
**Description**: How many mistakes you made  

**Calculation**:  

$\text{Accuracy} = (\text{Correct Lines}) - (\text{Error Count})$  

**Rules**:  
- Counts all syntax and logic errors  
- Higher values are better  

### Efficiency  
**Description**: How clean your solution is  

**Calculation**:  

$\text{Efficiency} = \frac{\text{Enemy HP}}{\text{Tiles Used}}$  

**Rules**:  
- Only counts tiles in final submitted code  
- Higher values are better  

## Normalized Scores (0-100 Scale)

### Normalized Speed  
**Description**: How close you are to the world record  

**Calculation**:  

$\text{Normalized Speed} = 100 \times \frac{\text{Fastest Time}}{\text{Your Time}}$  

**Rules**:  
- 100 = world record  
- 50 = twice as slow as record  

### Normalized Accuracy  
**Description**: How close you are to perfect accuracy  

**Calculation**:  

$\text{Normalized Accuracy} = 100 \times \frac{\text{Your Accuracy}}{\text{Best Accuracy}}$  

### Normalized Efficiency  
**Description**: How close you are to the most efficient solution  

**Calculation**:  

$\text{Normalized Efficiency} = 100 \times \frac{\text{Your Efficiency}}{\text{Best Efficiency}}$  

## Mastery Scores
Every mastery is just an average of Scores.

### Concept Mastery  
**Description**: Your average skill in a programming topic  

**Calculation**:  

$\text{Concept Mastery} = \frac{\text{Sum of Normalized Scores}}{3 \times \text{Number of Levels}}$  

**Rules**:  
- Includes Speed, Accuracy and Efficiency  
- Max 100 points per level  

### Grand Mastery  
**Description**: Your overall coding skill  

**Calculation**:  

$\text{Grand Mastery} = \frac{\text{Sum of Concept Masteries}}{\text{Number of Concepts}}$

## Leaderboard Types

1. **Level Leaderboards**  
   - Ranks players on specific levels  
   - Uses: $\text{Normalized Speed}$, $\text{Normalized Accuracy}$, $\text{Normalized Efficiency}$  

1. **Concept Leaderboards**
   - Ranks players by programming topic  
   - Uses: $\text{Concept Mastery}$  

3. **Global Leaderboard**  
   - Ranks overall player skill  
   - Uses: $\text{Grand Mastery}$  