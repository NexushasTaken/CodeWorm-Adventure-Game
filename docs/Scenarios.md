# Scenarios

## Variables & Data Types

### Making a Scenario

for players to be able to retain what they have learned, a multiple scenarios for each Concept is a must.
for instance, **Variables & Data Types** has many different data types, each data type must be one or more scenario scenario, see Scenario #1 and Scenario #2 below, these #1 and #2 Scenarios focused on *Integer Data Types*.

Template:

```markdown
**Enemy Name**: <name>

**Enemy HP**: <hp>

**Player HP**: <hp>

**Objective**: <objective>

#### Rules:
- rule 1
  - rule 1 explanation
  - rule 1 explanation

- rule 2
  - rule 2 explanation
  - rule 2 explanation
```

### Syntax Error Penalties

Also considered as penalty if there is error in code; enemy will counterattack.

| Error Type  | Enemy Attack Formula               |
| ----------- | ---------------------------------- |
| SyntaxError | `base_damage +  (2 * error_count)` |
| NameError   | `base_damage + name.length`        |
| TypeError   | `base_damage * 4`                  |
| Exception   | `base_damage + enemy_hp // 4`      |

## Integer

### Scenario #1: Integer Basics

**Enemy Name**: `NullInt`

**Enemy HP**: 50

**Base Damage**: 10

**Player HP**: 100

**Objective**: Assign integers to `attack` to deplete enemy HP.

#### Rules

**Valid Attack**:

- Deals damage equal to `attack` value.
- Enemy cannot counterattack.
- Valid attack is`attack <= 25`

**Overpowered**:

- Player is "distracted" (too large to deal damage above 25).
- Enemy counterattacks for `attack` damage.

**Penalty**:

- `attack` value cannot be the same per turn.
- Enemy counterattacks for `attack` damage.

### Scenario #2: Fibonacci Sequence

**Enemy Name**: `FiboNull`

**Enemy HP**: 60

**Base Damage**: 10

**Player HP**: 100

**Objective**: Assign Fibonacci numbers to `attack` to unlock bonus damage.

#### Rules

**Attack Formula**: `(c * n) + 1`

- `c` = Current Fibonacci value (e.g., `1, 1, 2, 3, 5...`).
- `n` = Sequence position (starts at 1).

**Example**:

- Turn 1: `attack = 1` -> `(1*1)+1 = 2` damage.
- Turn 2: `attack = 1` -> `(1*2)+1 = 3` damage.
- Turn 3: `attack = 2` -> `(2*3)+1 = 7` damage.

**Penalty**:

- Non-Fibonacci number -> Enemy counterattacks for `attack` damage.

## Float

### Scenario #3: Floating Point Precision

**Enemy Name**: FloatFiend

**Enemy HP**: 30

**Base Damage**: 10

**Player HP**: 30

**Objective**: Assign accurate float values to control attack power.

#### Rules

**Valid Attack**:

- Damage formula `(attack * 10)`
- Valid value `0.5 <= attack <= 5.5`
- Too Precise: More than 2 decimal places

**Invalid Attack**:

- Enemy counterattacks for `attack` damage if it is not within the range.

**Penalty**:

- Enemy counterattacks for `attack` damage.

## Boolean

### Scenario #4: Boolean Trap Logic

**Enemy Name**: TrueLie

**Enemy HP**: 40

**Base Damage**: 10

**Player HP**: 50

**Objective**: Assign correct boolean values to `attack` based on the enemy's statements.

#### Rules

**Valid Attack**:
Enemy speaks a statement each turn.

- If the statement is **true**, `attack = True`
- If the statement is **false**, `attack = False`

**Attack Formula**:

- `True` ‐> 1
- `False` -> 0
- Damage = `(int(attack) + 1) * 10`

**Invalid Attack**:

- Incorrect boolean input is the same Attack Formula, but with the correct boolean value.
- correct answer: `True` ‐> 1
- correct answer: `False` -> 0
- Damage = `(int(attack) + 1) * 10`

**Penalty**:

- Enemy counterattacks for `base_damage + 5` if the answer is wrong
**Example Enemy Dialogues** (one per turn):

1. "The sun is a planet." -> `attack = False`
2. "Water boils at 100°C." -> `attack = True`
3. "Python is a type of snake and a programming language." -> `attack = True`
4. "2 is greater than 5." -> `attack = False`

## String

### Scenario #5: String Echo Fight

**Enemy Name**: EchoLure

**Enemy HP**: 40

**Base Damage**: 10

**Player HP**: 50

**Objective**: Assign the correct string to `word` that matches the enemy's required word.

#### Rules

**Valid Attack**:

- Enemy says a word.
- Set `word` to that exact word as a string.
- Example: Enemy says "hello" → `word = "hello"`
- Damage = `len(word) * 2`

**Invalid Attack**:

- Any mismatch in spelling and wrong case (e.g., "Hello" != "hello")
- Damage = `len(word)`

**Penalty**:

- Enemy counterattacks for `base_damage + len(word)`
- if `len(word) == 0`, enemy counterattacks with `base_damage`.

**Example Enemy Requests** (one per turn):

1. "Say hello!" → `word = "hello"`
2. "Call me Lure!" → `word = "Lure"`
3. "I like 'code'" → `word = "code"`
4. "Repeat: python" → `word = "python"`

## List

### Scenario #6: List Formation

**Enemy Name**: SwarmBug

**Enemy HP**: 60

**Base Damage**: 8

**Player HP**: 60

**Objective**: Create a list named `targets` with the correct number of enemies, elements can be any type of values.

#### Rules

**Valid Action**:

- Enemy says how many bugs are in the swarm.
- Create a list named `targets` with that many elements (any values are allowed).
- Example: "There are 3 bugs!" → `targets = [1, 2, 3]` or `targets = ['a', 'b', 'c']`
- Damage = `len(targets) * 4`

**Invalid Action**:

- If `targets` is not a list, or has wrong number of elements
- Damage = 0

**Penalty**:

- Enemy counterattacks for `base_damage + (2 * abs(correct - actual))`
- where `correct` = expected length, `actual` = your list length

**Example Enemy Dialogues**:

1. "There are 2 bugs!" → `targets = [0, 1]`
2. "Five of us are crawling!" → `targets = ['a', 'b', 'c', 'd', 'e']`
3. "Just one bug!" → `targets = ['x']`

## Tuples

### Scenario #7: Tuple Lock Code

**Enemy Name**: LockWorm

**Enemy HP**: 50

**Base Damage**: 10

**Player HP**: 50

**Objective**: Create a tuple named `code` with numbers in **ascending order** to unlock the enemy's weak point.

#### Rules

**Valid Action**:

- Enemy gives you a list of numbers (in random order).
- You must create a tuple `code` with those numbers sorted from smallest to largest.
- Example: Enemy says `4, 1, 3` → `code = (1, 3, 4)`

**Invalid Action**:

- If `code` is not a tuple, or values are not in order → no damage

**Penalty**:

- Enemy counterattacks for `base_damage + (incorrect element position)` if the tuple is incorrect

**Example Enemy Dialogues**:

1. "Unlock with 7, 2, and 5." → `code = (2, 5, 7)`
2. "My combo is 9, 4, 6." → `code = (4, 6, 9)`
3. "Try 3, 3, 1." → `code = (1, 3, 3)`

## Dictionary

### Scenario #8: LetterCount Curse

**Enemy Name**: GlyphGhoul

**Enemy HP**: 50

**Base Damage**: 10

**Player HP**: 60

**Objective**: Count each letter in the enemy's glyph curse and store the result in a dictionary named `countmap`.

#### Rules

**Enemy Action (each turn)**:

- Enemy speaks a random string of letters (e.g., `"aabbccaa"`, `"xyyzz"`, `"mmmnpq"`)

**Valid Action**:

- Create a dictionary `countmap` where:
  - **Key** = each unique letter
  - **Value** = number of times the letter appears
  - Damage = `sum(countmap.values()) * 2`

**Invalid Action**:

- Enemy Counterattacks by:
- Wrong counts: sum of values of the dictionary.
- Incorrect datatype: number of wrong data type.
- Missing key: number of missing key.

#### Example

**Enemy casts**: `"aabbccaa"`
**Player code**:

```python
countmap = {'a': 4, 'b': 2, 'c': 2}
```
