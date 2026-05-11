# Chapter 6: Automated Test Generation — Random Testing and Property-Based Testing

## The Analogy Before the Definition

### Random Testing Analogy
Imagine testing a vending machine by pressing random buttons in random combinations and seeing what breaks. You didn't plan which buttons to press — you just hammered it randomly. Sometimes you find bugs in combinations no human tester would have thought to try.

### Property-Based Testing Analogy
Now imagine instead of pressing random buttons, you define a **property**: "No matter what sequence of buttons I press, the machine should never dispense a product without receiving payment first." You then let the computer generate thousands of random sequences and check if the property holds for all of them.

Property-based testing is smarter random testing — you define the rule that must always hold, and the tool generates diverse inputs to break it.

---

## Random Testing

### What it is
Random testing generates inputs **randomly** from the valid input domain and runs the system with them. No specific test design — pure random.

### How it works
1. Define the input domain (e.g., integers from -1000 to 1000)
2. Generate N random inputs from that domain
3. Execute the function with each input
4. Compare output to oracle (expected value) or check for crashes/exceptions

### Where it's useful
- **Stress testing** — bombard the system with random inputs to find crashes
- **Negative testing** — random invalid inputs to check error handling
- **Security testing** (fuzzing) — random malformed inputs to find vulnerabilities
- **Large input domains** — when the domain is so large that structured testing can't cover it

### Limitations
- No guarantee of hitting critical boundary values
- May waste effort on redundant similar inputs
- Without an oracle, hard to know if output is correct
- Coverage is not targeted — might miss important paths

### Example — Calculator Random Testing
```python
import random

for _ in range(10000):
    a = random.randint(-1000, 1000)
    b = random.randint(-1000, 1000)
    result = calculator.add(a, b)
    assert result == a + b  # oracle: we know the right answer
```
This runs 10,000 random test cases. If any assertion fails, we found a bug.

---

## Property-Based Testing (PBT)

### What it is
Instead of specifying exact input-output pairs, you specify **properties** that must always be true — and the tool generates hundreds/thousands of random inputs to try to violate those properties.

The most famous PBT library is **QuickCheck** (Haskell). Java has **jqwik**, Python has **Hypothesis**.

### Core idea
```
For ALL valid inputs x:
    property(f(x)) must hold true
```

### How it works
1. Define a property (a universal statement about your function)
2. Tool generates random inputs (integers, strings, lists — whatever you specify)
3. Tool runs your function with each input and checks the property
4. If the property is violated, tool **shrinks** the input to the simplest failing case
5. You get a minimal failing example, not a random huge one

### Good Properties to Define

| Function | Property Example |
|----------|-----------------|
| `sort(list)` | Result has same length as input |
| `sort(list)` | Result is sorted (each element ≤ next) |
| `sort(list)` | Result contains the same elements as input |
| `add(a, b)` | Commutative: `add(a, b) == add(b, a)` |
| `reverse(list)` | Idempotent: `reverse(reverse(list)) == list` |
| `encode(decode(x))` | Round-trip: `encode(decode(x)) == x` |

### PBT Example in Java (using jqwik)
```java
@Property
void sortedListIsSorted(@ForAll List<Integer> list) {
    List<Integer> sorted = MySort.sort(list);
    for (int i = 0; i < sorted.size() - 1; i++) {
        assertThat(sorted.get(i)).isLessThanOrEqualTo(sorted.get(i + 1));
    }
}
```
The framework generates hundreds of random lists and checks the property holds for each.

---

## Property-Based Testing for Real-Time Systems (Q5, Q27, Q28, Q31)

Real-time systems have **timing constraints** — they must respond within a deadline, or the response is as good as wrong (late airbag = no airbag).

### Why PBT is valuable for Real-Time Systems
- Input conditions change rapidly and unpredictably
- Exhaustive manual testing of all timing combinations is impossible
- Properties can express timing constraints formally

### Real-Time Traffic Control System Example (Q27)

> "A real-time traffic control system must maintain timing constraints under varying inputs."

**Properties to test:**
1. `For all valid input sequences: green_light_duration >= MIN_GREEN (30 seconds)`
2. `For all states: never two perpendicular roads are green simultaneously`
3. `For all sequences: total cycle time is between 60 and 120 seconds`
4. `For all emergency vehicle signals: green light clears within 5 seconds`

PBT generates thousands of random traffic scenarios (vehicle counts, pedestrian requests, emergency signals) and checks all these properties hold.

```
Property violated: Emergency signal received at T=0, green light cleared at T=8 seconds
Shrunk minimal failing case: Single emergency signal with no other vehicles
```

→ Bug found: emergency response takes 8 seconds instead of ≤5 seconds.

### Banking Transaction System Example (Q31)

> "A real-time banking transaction system must ensure correctness under random transaction sequences."

**Properties to test:**
1. `For any sequence of deposits and withdrawals: balance ≥ 0` (can't go below zero without overdraft)
2. `For any transaction: balance_after = balance_before + amount` (no money lost)
3. `For concurrent transactions: total money in system is conserved`
4. `For any failed transaction: account balance unchanged`

```java
@Property
void balanceNeverGoesNegative(
    @ForAll @Positive double initialBalance,
    @ForAll List<Double> withdrawals
) {
    Account account = new Account(initialBalance);
    for (double w : withdrawals) {
        if (w <= account.getBalance()) {
            account.withdraw(w);
        }
    }
    assertThat(account.getBalance()).isGreaterThanOrEqualTo(0);
}
```

---

## Random Testing vs Property-Based Testing (Q28, Q30)

| | Random Testing | Property-Based Testing |
|-|---------------|----------------------|
| Input | Randomly generated | Randomly generated |
| Oracle | Predefined expected output per input | A property that must hold for all inputs |
| Goal | Find crashes, errors, unexpected behaviour | Prove a property holds universally |
| Failure output | "Input X crashed the system" | "Minimal input that violates property" (shrinking) |
| Complexity | Simple to implement | Requires defining good properties |
| Effectiveness | Good for finding unexpected failures | Better for finding logical invariant violations |
| Use in real-time | Stress testing, fuzzing | Validating timing constraints, safety properties |

### Why both are used in real-time systems
- **Random testing** finds unexpected crashes and edge cases in timing logic
- **PBT** validates that invariants (timing constraints, safety properties) are never violated regardless of input sequence

---

## Regression Testing Automation (Q7, Q29)

Automated regression testing is one of the highest-ROI uses of test automation.

### How automated regression works in real projects:
1. Test suite covers all stable functionality
2. Every time a developer commits code → CI pipeline runs the regression suite
3. Results in < 10 minutes (fast feedback)
4. Any test failure → developer is notified immediately
5. Build is blocked from merging if tests fail

**Automation improves regression because:**
- Manual regression of 500 test cases takes days → automated in minutes
- No human fatigue — consistent execution
- Can run at 2am, every night (nightly regression)
- Catches regressions that manual testing would miss (the "it used to work" problem)

---

## Quick Summary

| Concept | One-liner |
|---------|-----------|
| Random testing | Generate random inputs, check for crashes/errors |
| Property-based testing | Define a universal property, auto-generate inputs to try to break it |
| Shrinking | PBT tool reduces a failing input to the smallest possible case |
| Real-time system property | A constraint that must always hold (e.g., response ≤ 5 seconds) |
| PBT advantage over random | Finds logical invariant violations, not just crashes |
| Automated regression | Full test suite runs on every code commit via CI pipeline |
