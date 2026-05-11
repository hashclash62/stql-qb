## Unit 2: Testing Techniques

| Q.No. | Question |
|-------|----------|
| 1 | Given a system with multiple modules, demonstrate how Top-down and Bottom-up Integration Testing would be performed. |
| 2 | A wholesaler sells printer cartridges. The minimum order quantity is 5. There is a 20% discount for orders of 100 or more printer cartridges. You have been asked to prepare test cases using various values for the number of printer cartridges ordered. Which of the following groups contain three test inputs that would be generated using Boundary Value Analysis? |
| 3 | Compare black box and white box testing. |
| 4 | Given a web application, apply Random Testing to generate test inputs and identify possible defects. |
| 5 | Apply Equivalence Class Partitioning (ECP) and Boundary Value Analysis (BVA) to design test cases for a system that accepts age between 18 and 60. Justify your test cases. |
| 6 | Apply Black Box Testing techniques (ECP, BVA) to test an online registration form and derive test cases. |
| 7 | Apply white box testing approach with example. |
| 8 | Analyze Experience-based testing techniques with examples. |
| 9 | Examine the Structure-based (white-box) testing techniques. |
| 10 | Apply all testing levels and explain their purpose with examples. |
| 11 | Apply Decision Table Testing to a real-world system and construct a decision table to derive effective test cases. |
| 12 | Evaluate the situations where Regression Testing is required and explain its significance. |
| 13 | Compare re-testing and regression testing. |
| 14 | Given a Software Requirement Specification (SRS) of a given application, apply Requirement-Based Testing to design relevant test cases and ensure requirement coverage. |
| 16 | Analyze and differentiate between Black-box, White-box, and Gray-box testing, and justify when each should be used. |
| 17 | Below is a simple example showing the decision statement with compound predicate: `if (age < 65 and married == true) { Do X. Do Y } Else Do Z`. Which testing technique will you select to write test cases for: 1) Simple decision coverage, 2) Condition coverage, 3) Decision-condition coverage. |
| 18 | Given a software module, apply static testing and structural testing techniques to identify defects and demonstrate how each method contributes to software quality. |
| 19 | Suppose a program allows a user to search for a part name in a specific group of part records. The user inputs the record number believed to hold the part, and the part name to search for. The program informs the user if the record number is within the legal range (1–1000). If not, an error message "record number is out of range" is issued. If within range and the part is found, it returns "part found," else "part not found." Identify input and output conditions (causes and effects). Draw a cause-and-effect graph and a decision table. Generate a set of test inputs and expected outputs. |
| 20 | Draw control flow graph for the code given below. Clearly label each node linked to its corresponding statement. Calculate cyclomatic complexity. How can this value be used to measure testability? Describe how cyclomatic complexity number and the flow graph can be used to design white box tests covering all branches. **Code:** `Module foo() /* a[] and b[] are global variables */ Begin Int i, x Read(x) While(i<x) do begin a[i] = b[i] * x if a[i] > 50 then Print("array a is over the limit"); else Print("OK") i = i + 1 End Print("end of nonsense"); End.` |
| 21 | For the following looping construct, describe the set of tests you would develop based on the number of loop iterations in accordance with loop testing criteria: `for (i = 0; i < 50; i++) { text_box[i] = value[i]; full = full–1; }` |
| 22 | A programmer using a mutation analysis tool finds that 35 mutants have been generated for program module A. Using a test set, she finds 29 dead mutants and 2 equivalent mutants. What is the mutation score (MS) for module A? Is her test set mutation adequate? Should she develop additional test cases? Justify. |
| 23 | During data flow testing, you observe that certain variables are defined but never used, while others are used without being initialized. How would you modify your testing strategy to detect and prevent such issues early in the development lifecycle? |
| 24 | Draw a state transition diagram for a simple stack machine. Assume the stack holds n data items where n is a small positive number. It has operations "push" and "pop" that cause the stack pointer to increment or decrement, respectively. The stack can enter states such as "full" (n items) and "empty" (no items). Popping from empty or pushing on full causes a transition to an error state. Based on your diagram, develop a set of black box test cases covering key state transitions. |
| 25 | Design test cases for the binary search code below using Data Flow testing. Write a table for each variable separately and select input data to cover all Def-Use Paths: `int binsearch(int x, int v[], int n) { int low, high, mid; low = 0; high = n-1; while (low <= high) { mid = (low+high)/2; if (x < v[mid]) high = mid - 1; else if (x > v[mid]) low = mid + 1; else return mid; } return -1; }` |
| 26 | Given a Java program, apply JUnit testing and demonstrate how test cases are designed and executed, highlighting key features of JUnit test cases. |
| 27 | Write JUnit test cases for the following code to achieve 90% code coverage: `public class SelectionSort { public static void selectionSort(int[] arr) { if (arr == null \|\| arr.length <= 1) { return; } int n = arr.length; for (int i = 0; i < n - 1; i++) { int minIndex = i; for (int j = i + 1; j < n; j++) { if (arr[j] < arr[minIndex]) { minIndex = j; } } int temp = arr[minIndex]; arr[minIndex] = arr[i]; arr[i] = temp; } } }` |
| 28 | Apply JUnit annotations to design and execute test cases for a Java program. |
| 29 | A module allows a user to enter a new widget. The input specification states that a widget identifier should consist of 3–15 alphanumeric characters of which the first two must be letters. Three conditions apply: (i) must consist of alphanumeric characters, (ii) total characters between 3 and 15, (iii) first two characters must be letters. Write test cases using Equivalence Class Partitioning and Boundary Value Analysis. |
| 30 | Analyze Cause–Effect Graphing and derive test cases for any given applications like online payment/ATM/Login page. |
| 31 | Apply Cause–Effect Graphing technique to a login system or decision-based application and derive test cases from the cause–effect graph. |
| 32 | Analyze Cause–Effect Graphing and derive test cases for a given scenario like an online shopping discount system. |
| 33 | Apply Mutation Testing to a given program and demonstrate how mutants are created and killed using test cases. Explain with a suitable example. |
| 34 | Justify the use of Mutation Testing over traditional testing techniques. |

---
