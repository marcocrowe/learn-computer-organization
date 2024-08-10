
# Exam Paper: Digital Electronics (TRON06029) 2023


## QUESTION 3: Minimised Boolean expression. [TOTAL MARKS: 33.33]

Determine the conical form of the setup using Karnaugh Map for the truth
tables of various 3 input TTL chips shown below.

| A | B | C | y |
|---|---|---|---|
| 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 1 |
| 0 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 |
| 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 1 |
| 0 | 1 | 1 | 1 |
| 1 | 1 | 1 | 1 |

## Answer 3.A

Construct the Karnaugh Map for the truth table above.

| A | B | C | Y= (???)                        | y |
|---|---|---|---------------------------------|---|
| 0 | 0 | 0 |                                 | 0 |
| 1 | 0 | 0 | ${A}.\overline{B}.\overline{C}$ | 1 |
| 0 | 1 | 0 | ${\overline{A}}.B.\overline{C}$ | 1 |
| 1 | 1 | 1 | ${A}.B.C$                       | 1 |
| 0 | 0 | 1 |                                 | 0 |
| 1 | 0 | 1 | $A.\overline{B}.C$              | 1 |
| 0 | 1 | 1 | $\overline{A}.B.C$              | 1 |
| 1 | 1 | 1 | $A.B.C$                         | 1 |

| A\BC | 00                            | 01                            | 11                 | 10                            |
|------|-------------------------------|-------------------------------|--------------------|-------------------------------|
| 0    |                               | $\overline{A}.B.\overline{C}$ | $\overline{A}.B.C$ | $\overline{A}.B.\overline{C}$ |
| 1    | $A.\overline{B}.\overline{C}$ | $A.\overline{B}.C$            | $A.B.C$            |                               |

| A\BC | 00 | 01 | 11 | 10 |
|------|----|----|----|----|
| 0    |    | 1  | 1  | 1  |
| 1    | 1  | 1  | 1  |    |

Group 1:

| A\BC | 00 | 01  | 11  | 10 |
|------|----|-----|-----|----|
| 0    |    | `1` | `1` | 1  |
| 1    | 1  | `1` | `1` |    |

C is 1 and does not change in this group so the equation for this group is $C$.

Group 2:

| A\BC | 00 | 01 | 11 | 10  |
|------|----|----|----|-----|
| 0    |    | 1  | 1  | `1` |
| 1    | 1  | 1  | 1  |     |

No variable changes in this group so the equation for this group is $\overline{A}.B.\overline{C}$.

Group 3:

| A\BC | 00 | 01 | 11 | 10  |
|------|----|----|----|-----|
| 0    |    | 1  | 1  | 1 |
| 1    | `1`  | 1  | 1  |     |

No variable changes in this group so the equation for this group is $A.\overline{B}.\overline{C}$.

Combining the three groups we get the minimized equation as:

$$\boxed{Y = C + \overline{A}.B.\overline{C} + A.\overline{B}.\overline{C}}$$

---
