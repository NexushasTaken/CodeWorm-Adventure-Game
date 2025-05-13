# Scenarios

## Variables & Data Types

### Making a Scenario

For players to retain what they've learned, multiple scenarios for each concept are essential. Each data type should have one or more dedicated scenarios.

Template:

```markdown
**Enemy Name**: <name>

**Enemy HP**: <hp>

**Base Damage**: <damage>

**Player HP**: <hp>

#### Description

<Objective and brief overview>

**Rules**:

- General rules governing the scenario

**Valid Attacks**:

- Conditions for successful attacks
- Damage calculation formula

**Penalties**:

- Consequences for invalid actions
- Enemy counterattack formulas

**Examples**:

- Sample inputs and expected outputs
```

## Integer

### Scenario #1: Integer Basics

**Enemy Name**: `NullInt`

**Enemy HP**: 50

**Base Damage**: 10

**Player HP**: 100

#### Description

Assign integers to `attack` to deplete enemy HP.

**Rules**:

- Each turn, assign an integer value to `attack`
- Values must differ from previous turns

**Valid Attacks**:

- Deals damage equal to `attack` value
- Valid when `attack <= 25`
- Enemy cannot counterattack on valid moves

**Penalties**:

- Overpowered (`attack > 25`): Enemy counterattacks for `base_damage + attack`
- Repeated value: Enemy counterattacks for `base_damage + attack`

**Examples**:

- Valid: `attack = 5` -> 5 damage
- Overpowered: `attack = 30` -> enemy counters for 40 damage
- Repeated: `attack = 5` (after previous 5) -> enemy counters for 15 damage

### Scenario #2: Fibonacci Sequence

**Enemy Name**: `FiboNull`

**Enemy HP**: 60

**Base Damage**: 10

**Player HP**: 100

#### Description

Assign Fibonacci numbers to `attack` to unlock bonus damage.

**Rules**:

- Must use Fibonacci sequence: 1, 1, 2, 3, 5...

**Valid Attacks**:
Damage formula: `(current_fib * position) + 1`

- `current_fib`: Current Fibonacci number
- `position`: Sequence position (starting at 1)

**Penalties**:

- Non-Fibonacci number: Enemy counterattacks for `attack` damage

**Examples**:

- Turn 1: `attack = 1` -> `(1*1)+1 = 2` damage
- Turn 2: `attack = 1` -> `(1*2)+1 = 3` damage
- Turn 3: `attack = 2` -> `(2*3)+1 = 7` damage
- Invalid: `attack = 4` -> enemy counters for 4 damage

## Float

### Scenario #3: Floating Point Precision

**Enemy Name**: `FloatFiend`

**Enemy HP**: 30

**Base Damage**: 10

**Player HP**: 30

#### Description

Assign accurate float values to control attack power.

**Rules**:

- Values must have ≤ 2 decimal places
- Must be within specified range

**Valid Attacks**:

- Damage: `attack * 10`
- Valid range: `0.5 <= attack <= 5.5`

**Penalties**:

- Out of range: Enemy counterattacks for `attack` damage
- Too precise (>2 decimals): Enemy counterattacks for `base_damage`

**Examples**:

- Valid: `attack = 1.25` -> 12.5 damage
- Invalid range: `attack = 6.0` -> enemy counters for 6 damage
- Too precise: `attack = 1.234` -> enemy counters for 10 damage

## Boolean

### Scenario #4: Boolean Trap Logic

**Enemy Name**: `TrueLie`

**Enemy HP**: 40

**Base Damage**: 10

**Player HP**: 50

#### Description

Assign correct boolean values based on enemy statements.

**Rules**:

- Enemy makes a statement each turn
- Determine if statement is true/false

**Valid Attacks**:
Damage formula: `(int(attack) + 1) * 10`

- `True` -> 20 damage
- `False` -> 10 damage

**Penalties**:

- Incorrect boolean: Enemy counterattacks for `base_damage + 5`

**Examples**:

1. "The sun is a planet." -> `attack = False` -> 10 damage
2. "Water boils at 100°C." -> `attack = True` -> 20 damage
3. Wrong answer -> enemy counters for 15 damage

## String

### Scenario #5: String Echo Fight

**Enemy Name**: `EchoLure`

**Enemy HP**: 40

**Base Damage**: 10

**Player HP**: 50

#### Description

Echo exact strings to damage enemy.

**Rules**:

- Must match case and spelling exactly

**Valid Attacks**:

- Damage: `len(word) * 2`

**Penalties**:

- Mismatch: Enemy counterattacks for `base_damage + len(word)`
- Empty string: Enemy counters for `base_damage`

**Examples**:

- Enemy: "hello" -> `word = "hello"` -> 10 damage
- Wrong case: `word = "Hello"` -> enemy counters for 15
- Empty: `word = ""` -> enemy counters for 10

## List

### Scenario #6: List Formation

**Enemy Name**: `SwarmBug`

**Enemy HP**: 60

**Base Damage**: 8

**Player HP**: 60

#### Description

Create lists with correct number of elements based on enemy's swarm count.

**Rules**:

- Must create a list named `targets`
- Elements can be any type

**Valid Attacks**:

- Damage: `len(targets) * 4`

**Penalties**:

- Wrong length: Enemy counterattacks for `base_damage + (2 * |expected - actual|)`
- Not a list: Enemy counterattacks for `base_damage + 5`

**Examples**:

1. "3 bugs!" -> `targets = [1,2,3]` -> 12 damage
2. "1 bug!" -> `targets = ['x']` -> 4 damage
3. Wrong length -> enemy counters based on difference

## Tuples

### Scenario #7: Tuple Lock Code

**Enemy Name**: `LockWorm`

**Enemy HP**: 50

**Base Damage**: 10

**Player HP**: 50

#### Description

Create sorted tuples to unlock enemy defenses.

**Rules**:

- Must create tuple named `code`
- Numbers must be in ascending order

**Valid Attacks**:

- Damage: `sum(code)`

**Penalties**:

- Unsorted: Enemy counterattacks for `base_damage + position_of_first_error`
- Not a tuple: Enemy counterattacks for `base_damage + 3`

**Examples**:

1. "7,2,5" -> `code = (2,5,7)` -> 14 damage
2. "3,3,1" -> `code = (1,3,3)` -> 7 damage
3. Unsorted -> enemy counters based on error position

## Dictionary

### Scenario #8: LetterCount Curse

**Enemy Name**: `GlyphGhoul`

**Enemy HP**: 50

**Base Damage**: 10

**Player HP**: 60

#### Description

Count letter frequencies in enemy's glyph strings.

**Rules**:

- Must create dictionary named `countmap`
- Keys: unique letters
- Values: occurrence counts

**Valid Attacks**:

- Damage: `sum(countmap.values()) * 2`

**Penalties**:

- Wrong counts: Enemy counterattacks for `sum(values)`
- Missing keys: +2 damage per missing key
- Wrong type: +5 damage

**Examples**:

1. "aabbcc" -> `countmap = {'a':2, 'b':2, 'c':2}` -> 12 damage
2. Missing 'b' -> enemy counters for sum + penalties
