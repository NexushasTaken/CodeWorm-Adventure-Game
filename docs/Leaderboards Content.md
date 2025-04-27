# Leaderboard Metrics & Calculation
## Per Level Metrics

## 1. Definitions and Notation
### Speed (Time Attack)
Definitiion: Time taken to complete $s$.

Measurement:

$$T_{p,s} = t_{end} - t_{start}$$

Rules:
- No error occurs at the time of completion.

### Accuracy (Error-Free Runs)
Description: Tracks how cleanly a player solves a level (fewest mistakes).

Calculation:

```
Accuracy Score = (Total Lines Run) - (Total Errors)
```

### Code Efficiency (Optimal Solutions)
Description: Rewards solving levels with minimal code tiles.
Calculation:
```
Efficiency Score = (Enemy HP) / (Tiles Used)
```

## Overall Metrics
### Concept Mastery
Description: Evaluates a player’s skill across all levels in programming concept.
Calculation:
```
Mastery Score =  ((Sum of Speed Score) + (Sum of Accuracy Score) + (Sum of Efficiency Score)) / (3 * Scenarios Completed)
```

Sum of Score refers to the sum of scores across all levels.

### Grand Mastery
Description: Overall skill across ALL topics.
Calculation:
```
Grand Mastery = (Sum of Mastery Scores for ALL topics) / (Number of topics attempted)
```

$\hat{T}_{\text{Bob},s} = 100 \times \frac{\min(30, 45, 60)}{45} = 100 \times \frac{30}{45} = 66.7$