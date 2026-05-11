# Chapter 5: Regression Testing, Re-testing, and JUnit

---

## Re-testing vs Regression Testing (Q12, Q13)

These two are closely related but serve different purposes. This is a classic exam question.

### Re-testing

**What it is:** Running a test that *previously failed* to verify that the specific defect it found has now been fixed.

*Analogy:* You reported a pothole on your street. After the road crew repairs it, you drive over the exact same spot to confirm it's fixed. That's re-testing — checking the same thing that was broken.

**Key characteristics:**
- Targets a *specific known defect*
- Uses the *same test case* that originally found the defect
- Done after a developer reports a fix
- Only checks the fixed issue — doesn't look elsewhere

### Regression Testing

**What it is:** Running a *broader set of tests* after any code change to ensure that the change didn't accidentally break something that was previously working.

*Analogy:* After repairing the pothole, you drive the entire street — not just the patched spot — to make sure the repair work didn't create new cracks elsewhere.

**Key characteristics:**
- Broader scope — covers existing working functionality
- Triggered by any code change (bug fix, new feature, refactoring)
- Uses the full regression test suite (or a selected subset)
- Looks for *newly introduced* defects, not the original one

### Side-by-Side Comparison (Q13)

| Aspect | Re-testing | Regression Testing |
|--------|-----------|-------------------|
| **Purpose** | Confirm a specific defect is fixed | Ensure fix didn't break other things |
| **Scope** | Narrow — one specific test case | Broad — many test cases |
| **Trigger** | Defect marked as "Fixed" | Any code change |
| **Test cases used** | The original failing test | Full/selected regression suite |
| **What it finds** | Whether the fix worked | New defects introduced by the change |
| **Who does it** | Tester (after developer fixes) | Tester (after any code change) |

### When is Regression Testing Required? (Q12)

- After **bug fixes** — the fix might have side effects
- After **new feature additions** — new code might interact badly with existing code
- After **code refactoring** — restructured code might change behaviour
- After **performance optimisation** — might change functional behaviour accidentally
- After **configuration changes** — different settings might expose existing bugs
- Before **major releases** — full regression pass to ensure stability

---

## JUnit Testing (Q26, Q27, Q28)

### What is JUnit?

JUnit is the standard **automated unit testing framework for Java**. It lets you write small, focused test methods that verify the behaviour of individual units of code (methods, classes). Tests run automatically and report pass/fail.

*Analogy:* JUnit is like a quality checkpoint at a factory assembly line — after each component is assembled, it's automatically checked against a checklist before moving to the next station.

---

## JUnit Annotations (Q28)

Annotations are the building blocks of JUnit test classes. Each tells JUnit *when* and *how* to run a method.

| Annotation | Purpose | When it runs |
|-----------|---------|-------------|
| `@Test` | Marks a method as a test case | Runs each test |
| `@Before` | Runs *before each* test method | Setup per test (create fresh objects) |
| `@After` | Runs *after each* test method | Teardown per test (close connections) |
| `@BeforeClass` | Runs *once before all* tests in the class | One-time setup (e.g., start server) |
| `@AfterClass` | Runs *once after all* tests in the class | One-time teardown |
| `@Ignore` | Skips this test | Never (unless un-ignored) |
| `@Test(expected = Exception.class)` | Test expects an exception to be thrown | Runs, expects exception |
| `@Test(timeout = 1000)` | Test must complete within 1000ms | Fails if too slow |

---

## JUnit Assertions

Assertions are how you verify expected behaviour:

| Assertion | What it checks |
|-----------|---------------|
| `assertEquals(expected, actual)` | Two values are equal |
| `assertNotEquals(a, b)` | Two values are not equal |
| `assertTrue(condition)` | Condition is true |
| `assertFalse(condition)` | Condition is false |
| `assertNull(object)` | Object is null |
| `assertNotNull(object)` | Object is not null |
| `assertArrayEquals(arr1, arr2)` | Arrays have same content |
| `assertThrows(Exception.class, () -> ...)` | Code block throws the expected exception (JUnit 5) |

---

## JUnit Test Structure Example (Q26)

```java
import org.junit.*;
import static org.junit.Assert.*;

public class BankAccountTest {

    private BankAccount account;  // Object to test

    @BeforeClass
    public static void setUpClass() {
        // Runs once: e.g., connect to test DB
        System.out.println("Starting BankAccount tests");
    }

    @Before
    public void setUp() {
        // Runs before each test: fresh account with balance 1000
        account = new BankAccount(1000);
    }

    @Test
    public void testDeposit_validAmount_increasesBalance() {
        account.deposit(500);
        assertEquals(1500, account.getBalance());
    }

    @Test
    public void testWithdraw_validAmount_decreasesBalance() {
        account.withdraw(300);
        assertEquals(700, account.getBalance());
    }

    @Test(expected = IllegalArgumentException.class)
    public void testWithdraw_negativeAmount_throwsException() {
        account.withdraw(-100);  // Should throw exception
    }

    @Test
    public void testWithdraw_moreThanBalance_throwsException() {
        assertThrows(InsufficientFundsException.class, () -> {
            account.withdraw(2000);
        });
    }

    @After
    public void tearDown() {
        account = null;  // Clean up after each test
    }

    @AfterClass
    public static void tearDownClass() {
        System.out.println("All BankAccount tests complete");
    }
}
```

---

## JUnit for SelectionSort — 90% Coverage (Q27)

```java
public class SelectionSortTest {

    @Test
    public void testSort_normalArray_sortedCorrectly() {
        int[] input = {64, 25, 12, 22, 11};
        int[] expected = {11, 12, 22, 25, 64};
        SelectionSort.selectionSort(input);
        assertArrayEquals(expected, input);
    }

    @Test
    public void testSort_alreadySorted_remainsSorted() {
        int[] input = {1, 2, 3, 4, 5};
        int[] expected = {1, 2, 3, 4, 5};
        SelectionSort.selectionSort(input);
        assertArrayEquals(expected, input);
    }

    @Test
    public void testSort_reverseOrder_sortedCorrectly() {
        int[] input = {5, 4, 3, 2, 1};
        int[] expected = {1, 2, 3, 4, 5};
        SelectionSort.selectionSort(input);
        assertArrayEquals(expected, input);
    }

    @Test
    public void testSort_singleElement_noChange() {
        int[] input = {42};
        int[] expected = {42};
        SelectionSort.selectionSort(input);
        assertArrayEquals(expected, input);
    }

    @Test
    public void testSort_nullArray_noException() {
        // Tests the null check branch: if (arr == null || arr.length <= 1)
        SelectionSort.selectionSort(null);  // Should return without error
    }

    @Test
    public void testSort_emptyArray_noException() {
        // Tests arr.length <= 1 branch
        int[] input = {};
        SelectionSort.selectionSort(input);
        assertArrayEquals(new int[]{}, input);
    }

    @Test
    public void testSort_duplicateElements_sortedCorrectly() {
        int[] input = {3, 1, 3, 2, 1};
        int[] expected = {1, 1, 2, 3, 3};
        SelectionSort.selectionSort(input);
        assertArrayEquals(expected, input);
    }
}
```

**Coverage analysis:**
- `testSort_nullArray_noException` → covers `arr == null` branch
- `testSort_emptyArray_noException` → covers `arr.length <= 1` branch
- `testSort_normalArray_sortedCorrectly` → covers main sort logic, inner loop, swap
- `testSort_alreadySorted_remainsSorted` → covers case where `minIndex == i` (no swap needed)
- Together: 90%+ branch coverage achieved

---

## Naming Convention for JUnit Tests

A good test method name follows: `testMethodName_condition_expectedBehaviour`

Examples:
- `testDeposit_negativeAmount_throwsException` ✅
- `testSort_emptyArray_returnsEmpty` ✅
- `test1` ❌ — not descriptive

Good names make test failure reports immediately clear: you know *what failed* without reading the test body.

---

## Quick Summary

- **Re-testing:** Run the *same failed test* after a fix to confirm the specific defect is resolved
- **Regression testing:** Run a *broader test suite* after any change to catch newly introduced defects
- Regression testing is triggered by: bug fixes, new features, refactoring, configuration changes
- **JUnit** is Java's standard unit testing framework
- Core annotations: `@Test`, `@Before`, `@After`, `@BeforeClass`, `@AfterClass`
- Assertions verify expected vs actual: `assertEquals`, `assertTrue`, `assertThrows`, etc.
- To achieve high coverage: write separate tests for each branch (null, empty, normal, edge cases)
- Test method naming: `testMethod_condition_expectedResult` makes failures self-documenting
