# Leaderboard Metrics & Calculation
## Per Level Metrics

## Definitions and Notation
Let:
- $S$ = Set of all scenarios (levels).
- $C$ = Set of all concepts (e.g., Variables, Loops).
- $s \in S$ = A single scenario.
- $c \in C$ = A single concept.
- $P$ = Set of all players.
- $p \in P$ = A single player.

## Per-Scenario Metrics
For each player $p$ and scneario $s$, compute:

#### (a) Speed ($T_{p,s}$)

**Definition**: Time taken to complete $s$.

**Measurement**:

$$T_{p,s} = t_{end} - t_{start}$$

**Constraint**:
- $T_{p,s}$ is valid ony if the final submitted code executes without errors.

#### (b) Accuracy ($A_{p,s}$)
**Description**: Error-adjusted correctness

**Measurement**:

$$A_{p,s} = (\text{Total Lines Executed}) - (\text{Total Errors})$$

#### (c) Efficiency ($E_{p,s}$)
**Description**: Tile economy relative to enemy HP.

**Measurement**:

$$E_{p,s} = \frac{\text{Enemy HP}}{\text{Tiles Used}}$$

- **Tiles Used**: Count of tiles in the level completion.

## Normalization to \[0, 100\] Scale
To compare across scenarios, normalize each metric relative to the **best observed performance** in $s$:

#### (a) Normalized Speed ($\hat{T}_{p,s}$)

$$\hat{T}_{p,s} = 100 \times \frac{min_{q \in P} T_{q,s}}{T_{p,s}}$$

**Interpretation**:
- $\hat{T}_{p,s} = 100$ if $p$ holds the record for fastest $s$.
- $\hat{T}_{p,s} \rightarrow 0$ as $T_{p,s} \rightarrow \infty$

#### (b) Normalized Accuracy ($\hat{A}_{p,s}$)

$$\hat{A}_{p,s} = 100 \times \frac{A_{p,s}}{max_{q \in P} A_{q,s}}$$

**Interpretation**:
- $\hat{A}_{p,s} = 100$ if $p$ used the fewest tiles in $s$. 
- $\hat{A}_{p,s} \rightarrow 0$ if $p$ made errors in every line.

#### (c) Normalized Efficiency ($\hat{E}_{p,s}$)

$$\hat{E}_{p,s} = 100 \times \frac{E_{p,s}}{max_{q \in P} E_{q,s}}$$

**Interpretation**:
- $\hat{E}_{p,s} = 100$ if $p$ used the fewest tiles in $s$. 
- $\hat{E}_{p,s} \rightarrow 0$ as tiles used $\rightarrow \infty$. 

## Concept Mastery ($M_{p,c}$)
For each concept $c$, aggregate performance across all $s \in c$:

$$M_{p,c} = \frac{1}{3|S_c|}\sum_{s \in S_c}(\hat{T}_{p,s} + \hat{A}_{p,s} + \hat{E}_{p,s})$$

- $S_c$: Set of scenarios in concept $c$.
- $|S_c|$: Number of scenarios in $c$.
- **Range**: $M_{p,c} \in [0, 100]$

## Grand Mastery ($G_p$)
Aggregate across all concepts:

$$G_p = \frac{1}{|C_p|} \sum_{c \in C_p} M_{p,c}$$

- $C_p$: Concepts attemted by $p$.
- $|C_p|$: Number of concepts attemted.
- **Range**: $G_p \in [0, 100]$

## Leaderboard Ranking
Rank players by:

**Concept Leaderboards**: Sort $M_{p,c}$ in descending order for each $c$.

**Grand Leaderboards**: Sort $G_{p}$ in descending order.
