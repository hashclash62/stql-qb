# Chapter 1: Black Box Testing Techniques

---

## What is Black Box Testing?

Imagine you're testing a vending machine. You press buttons and put in money, but you can't open the machine to see the internal mechanics. You can only observe: "I pressed button B3, inserted ₹20, and the machine gave me a Pepsi." You're testing from the *outside* — purely based on inputs and expected outputs.

That's black box testing. The tester doesn't know or care about the internal code. They test based on the **specification** (what the software is supposed to do).

**When to use:** Functional testing, acceptance testing, any testing where you're validating behaviour against requirements without needing to read code.

---

## Technique 1: Random Testing (Q4)

**What it is:** Generating test inputs randomly from the valid input domain.

**When useful:** Early-stage testing, fuzz testing (security), discovering unexpected input combinations.

**Limitation:** Not very efficient — you might test the same inputs repeatedly or miss important boundaries.

**Web app example (Q4):**
For a registration form with name (string), age (integer), and email fields:
- Random names: "Alice", "XY", "", "a"×200 chars
- Random ages: 25, 0, -5, 999, 18, 60
- Random emails: "user@mail.com", "notanemail", "", "a@b.c"

Random testing might accidentally find that the app crashes on an empty name — but it's not systematic.

---

## Technique 2: Equivalence Class Partitioning (ECP)

### The Idea
Testing every possible input is impossible. But inputs that are treated the *same way* by the software can be grouped into **equivalence classes** — and you only need to test *one value* from each class.

Think of a nightclub bouncer. They have one rule: "You must be 18 or older." Every person under 18 gets the same treatment (rejected), and every person 18+ gets the same treatment (allowed in). The bouncer doesn't need to test every possible age — just one from each class.

### How to Apply ECP

**Step 1:** Identify all input conditions (rules, ranges, constraints).

**Step 2:** For each condition, identify:
- **Valid equivalence classes** — inputs the system should accept
- **Invalid equivalence classes** — inputs the system should reject

**Step 3:** Write one test case per class.

### ECP for Age 18–60 (Q5)

Input rule: Age must be between 18 and 60 (inclusive).

| Class | Description | Representative Value |
|-------|-------------|---------------------|
| **Valid EC1** | Age in range [18, 60] | 35 |
| **Invalid EC2** | Age below 18 | 10 |
| **Invalid EC3** | Age above 60 | 70 |
| **Invalid EC4** | Non-numeric input | "abc" |
| **Invalid EC5** | Negative value | -5 |

**Test cases:**
- TC1: age = 35 → Expected: Accepted ✅
- TC2: age = 10 → Expected: Rejected ❌
- TC3: age = 70 → Expected: Rejected ❌
- TC4: age = "abc" → Expected: Error/Rejected ❌
- TC5: age = -5 → Expected: Rejected ❌

### Widget Identifier Example (Q29)

Input rules:
1. 3–15 alphanumeric characters
2. First two must be letters

**Equivalence Classes:**

For length (3–15):
- Valid: length in [3, 15] — e.g., "AB3"
- Invalid: length < 3 — e.g., "A1"
- Invalid: length > 15 — e.g., "AB123456789012345" (16 chars)

For character type:
- Valid: all alphanumeric
- Invalid: contains special character — e.g., "AB@34"

For first two chars:
- Valid: both are letters — e.g., "AB123"
- Invalid: first char is digit — e.g., "1B123"
- Invalid: second char is digit — e.g., "A1BCD"

---

## Technique 3: Boundary Value Analysis (BVA)

### The Idea
Defects love to hide at **boundaries**. Developers often write `>` when they meant `>=`, or loop one iteration too many. BVA specifically tests the values *at*, *just below*, and *just above* every boundary.

*Real-world analogy:* Testing a bridge. The bridge is rated for 10 tonnes. You'd test at 9.9 tonnes, exactly 10 tonnes, and 10.1 tonnes — not just somewhere in the middle (like 5 tonnes).

### BVA Rule: For Each Boundary, Test 3 Values
- **Just below the boundary** (min - 1)
- **At the boundary** (min)
- **Just above the boundary** (min + 1)

...and the same for the upper boundary.

### BVA for Age 18–60 (Q5)

Boundaries are at 18 (lower) and 60 (upper).

| Test Case | Value | Expected | Why |
|-----------|-------|----------|-----|
| TC1 | 17 | Rejected | Just below lower boundary |
| TC2 | 18 | Accepted | At lower boundary |
| TC3 | 19 | Accepted | Just above lower boundary |
| TC4 | 59 | Accepted | Just below upper boundary |
| TC5 | 60 | Accepted | At upper boundary |
| TC6 | 61 | Rejected | Just above upper boundary |

### Printer Cartridge Example (Q2)

Rules: Minimum order = 5. Discount for orders ≥ 100.

Boundaries: 5 (lower valid), 100 (discount threshold)

| Boundary | Values to Test |
|----------|---------------|
| Lower bound (5) | 4, 5, 6 |
| Discount bound (100) | 99, 100, 101 |

The correct answer group would be: **{4, 5, 6}** or **{99, 100, 101}** (both are valid BVA groups).

### Widget Identifier BVA (Q29)

For length boundary [3, 15]:
- Test lengths: 2, 3, 4 (lower boundary)
- Test lengths: 14, 15, 16 (upper boundary)

---

## Technique 4: Decision Table Testing (Q11)

### The Idea
When a system's behaviour depends on multiple conditions *combined*, a decision table captures all possible combinations of conditions and the corresponding actions.

*Analogy:* A restaurant's "happy hour" policy: discount applies if it's Monday–Friday AND between 5–7pm AND the customer has a loyalty card. A decision table maps every combination to an outcome.

### Structure

```
             Rule 1  Rule 2  Rule 3  Rule 4
Conditions:
  Cond 1       Y       Y       N       N
  Cond 2       Y       N       Y       N
Actions:
  Action A     ✓       ✗       ✗       ✗
  Action B     ✗       ✓       ✓       ✗
```

Each **Rule** (column) is one test case.

### Online Shopping Discount System Example (Q32)

Conditions:
- C1: Customer is a member? (Y/N)
- C2: Order total ≥ ₹1000? (Y/N)
- C3: Coupon code entered? (Y/N)

Actions:
- A1: Apply 10% member discount
- A2: Apply 5% bulk discount
- A3: Apply coupon discount
- A4: No discount

| | R1 | R2 | R3 | R4 | R5 | R6 | R7 | R8 |
|-|----|----|----|----|----|----|----|----|
| C1 Member | Y | Y | Y | Y | N | N | N | N |
| C2 ≥₹1000 | Y | Y | N | N | Y | Y | N | N |
| C3 Coupon | Y | N | Y | N | Y | N | Y | N |
| A1 Member disc | ✓ | ✓ | ✓ | ✓ | - | - | - | - |
| A2 Bulk disc | ✓ | ✓ | - | - | ✓ | ✓ | - | - |
| A3 Coupon disc | ✓ | - | ✓ | - | ✓ | - | ✓ | - |
| A4 No discount | - | - | - | - | - | - | - | ✓ |

Each column = one test case. 8 rules = 8 test cases covering all combinations.

---

## Technique 5: Cause-Effect Graphing (Q19, Q30, Q31, Q32)

### The Idea
A structured way to convert a complex specification into a decision table, using a graph as an intermediate step. It identifies:
- **Causes:** Input conditions
- **Effects:** Output actions
- **Graph:** Shows relationships and constraints between causes and effects

### Steps to Apply

1. Identify all **causes** (input conditions) from the spec — label C1, C2, C3...
2. Identify all **effects** (output outcomes) — label E1, E2, E3...
3. Draw the **cause-effect graph** — connect causes to effects using logical operators (AND, OR, NOT)
4. Add **constraints** (if two causes can't both be true simultaneously — mutual exclusion)
5. Convert the graph to a **decision table**
6. Each column of the table = one test case

### Login System Example (Q31)

**Causes:**
- C1: Username is valid
- C2: Password is correct
- C3: Account is not locked

**Effects:**
- E1: Login successful
- E2: "Invalid username" message
- E3: "Wrong password" message
- E4: "Account locked" message

**Graph logic:**
- E1 = C1 AND C2 AND C3
- E2 = NOT C1
- E3 = C1 AND (NOT C2)
- E4 = C1 AND C2 AND (NOT C3)

**Decision table (partial):**

| | T1 | T2 | T3 | T4 |
|-|----|----|----|----|
| C1 Valid username | Y | N | Y | Y |
| C2 Correct password | Y | - | N | Y |
| C3 Not locked | Y | - | - | N |
| E1 Login success | ✓ | - | - | - |
| E2 Invalid username | - | ✓ | - | - |
| E3 Wrong password | - | - | ✓ | - |
| E4 Account locked | - | - | - | ✓ |

Each row = one test case with specific inputs and expected output.

---

## Technique 6: State Transition Testing (Q24)

### The Idea
Some systems behave differently depending on their **current state**. A state transition diagram models:
- **States:** The distinct modes the system can be in
- **Transitions:** The events that cause a state change
- **Actions:** What happens when a transition occurs

*Real analogy:* A traffic light. It has states (Red, Yellow, Green) and transitions (timer fires → change state). Testing means verifying all valid transitions work and all invalid transitions are handled.

### Stack Machine Example (Q24)

States:
- **Empty:** Stack has 0 items
- **Normal:** Stack has 1 to n-1 items
- **Full:** Stack has n items
- **Error:** Invalid operation attempted

Transitions:
```
Empty ──push──→ Normal ──push──→ Full
Empty ←──pop── Normal ←──pop── Full
Empty ──pop──→ Error
Full ──push──→ Error
Error ──reset──→ Empty
```

**Test cases based on state transitions:**

| TC | Initial State | Operation | Expected Next State | Expected Output |
|----|--------------|-----------|--------------------|----|
| T1 | Empty | Push(5) | Normal | Success |
| T2 | Normal | Push(3) | Normal/Full | Success |
| T3 | Full | Push(1) | Error | "Stack full" error |
| T4 | Normal | Pop() | Normal/Empty | Returns top value |
| T5 | Empty | Pop() | Error | "Stack empty" error |
| T6 | Error | Reset | Empty | System reset |

**Testing strategy:** Cover every state. Cover every valid transition. Cover every invalid transition (error cases).

---

## Quick Summary

- **Black box testing** = testing from the outside, based on specification, without seeing code
- **ECP:** Group inputs into equivalence classes; test one value per class
- **BVA:** Test values at boundaries (min-1, min, min+1, max-1, max, max+1)
- **Decision table:** Capture all condition-action combinations; each column = one test case
- **Cause-effect graphing:** Graph causes → effects → convert to decision table
- **State transition testing:** Draw states and transitions; test every valid and invalid transition
- BVA + ECP are almost always used together for thorough black box input testing
