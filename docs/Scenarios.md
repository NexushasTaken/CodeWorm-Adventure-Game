# Variables & Data Types

## Making a Scenario
for players to be able to retain what they have learned, a multiple scenarios for each Concept is a must.
for instance, **Variables & Data Types** has many different data types, each data type must be one or more scenario scenario, see Scenario #1 and Scenario #2 below, these #1 and #2 Scenarios focused on *Integer Data Types*.

Template:
```
**Enemy Name**: <name>
**Enemy HP**: <hp>
**Player HP**: <hp>
**Objective**: <objective>

### Rules:
- rule 1
  rule 1 explanation
  rule 1 explanation
- rule 2
  rule 2 explanation
  rule 2 explanation
```

## Syntax Error Penalties:
| Error Type  | Enemy Attack Formula               |
| ----------- | ---------------------------------- |
| SyntaxError | `base_damage +  (2 * error_count)` |
| NameError   | `base_damage + name.length`        |
| TypeError   | `base_damage * 4`                  |
| Exception   | `base_damage + enemy_hp // 4`      |

## Scenario #1: Integer Basics  
**Enemy Name**: `NullInt`  
**Enemy HP**: 50  
**Player HP**: 100  
**Objective**: Assign integers to `attack` to deplete enemy HP.  

### Rules:
- **Valid Attack** (`attack < 25`):  
  Deals damage equal to `attack` value.  
  Enemy cannot counterattack.  
- **Overpowered** (`attack > 25`):  
  Player is "distracted" (too large to handle).  
  Enemy counterattacks for `attack` damage.  
- **Ineffective** (`25 ≤ attack ≤ 50`):  
  No damage (enemy blocks).  

---

## Scenario #2: Fibonacci Sequence  
**Enemy Name**: `FiboNull`  
**Enemy HP**: 60
**Player HP**: 100  
**Objective**: Assign Fibonacci numbers to `attack` to unlock bonus damage.  

### Rules:  
- **Attack Formula**: `(c * n) + 1`  
  - `c` = Current Fibonacci value (e.g., `1, 1, 2, 3, 5...`).  
  - `n` = Sequence position (starts at 1).  
- **Example**:  
  - Turn 1: `attack = 1` -> `(1*1)+1 = 2` damage.  
  - Turn 2: `attack = 1` -> `(1*2)+1 = 3` damage.  
  - Turn 3: `attack = 2` -> `(2*3)+1 = 7` damage.  
- **Penalty**:  
  - Non-Fibonacci number → Enemy counterattacks for `attack` damage.  
