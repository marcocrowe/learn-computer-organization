
# Karnaugh Maps

## Sample Exam K-Map Question (TOTAL MARKS: 25)

The Karnaugh map in Figure Q.2 below represents a logic function with 4 variables
DCBA. The original equation has 9 terms in it, as can be seen from the map.

| DC\BA | 00 | 01 | 11 | 10 |
|-------|----|----|----|----|
| 00    | 1  | 1  | 1  |    |
| 01    | 1  | 1  | 1  | 1  |
| 11    |    |    | 1  | 1  |
| 10    |    |    |    |    |

> Figure Q.2

### Question 2a (6 marks)

Write down the original Boolean equation that was used to fill the Karnaugh map in Figure Q.2 above.

$\overline{D}.\overline{C}.\overline{B}.\overline{A} +$
$\overline{D}.\overline{C}.\overline{B}.A +$
$\overline{D}.\overline{C}.B.A +$
$\overline{D}.C.\overline{BA}+$
$\overline{D}.C.\overline{B}A+$
$\overline{D}.C.B.A+$
$\overline{D}.C.B.\overline{A}+$
$D.C.B.A+$
$D.C.B.\overline{A}$


[6 Marks]

Q 2(b)
Copy the K-Map into your answer book. Draw the most suitable loops on your map.
[6 Marks]

*Group 1:*

| DC\BA | 00    | 01    | 11 | 10 |
|-------|-------|-------|----|----|
| 00    | *1* | *1* | 1  |    |
| 01    | *1* | *1* | 1  | 1  |
| 11    |       |       | 1  | 1  |
| 10    |       |       |    |    |

D is 0 and does not change in this group and B is 0 does not change in this group. The equation for this group is $\overline{D}.\overline{B}$.

*Group 2:*

| DC\BA | 00 | 01 | 11    | 10    |
|-------|----|----|-------|-------|
| 00    | 1  | 1  | 1     |       |
| 01    | 1  | 1  | ***1*** | **1** |
| 11    |    |    | ***1*** | **1** |
| 10    |    |    |       |       |

C is 1 and does not change in this group and B is 1 does not change in this group. The equation for this group is $C.B$

Group 3

| DC\BA | 00 | 01 | 11    | 10 |
|-------|----|----|-------|----|
| 00    | 1  | 1  | **1** |    |
| 01    | 1  | 1  | **1** | 1  |
| 11    |    |    | 1     | 1  |
| 10    |    |    |       |    |

D is 0 and does not change in this group and A and B are 1 and do not change in this group. The equation for this group is $\overline{D}.A.B$

Q2(c)
Write down the minimized equation.

$\overline{D}.\overline{B} + C.B + \overline{D}.A.B$

[6 Marks]

Q 2(d)
Use a 3 variable K-map to minimise the following function :-

$F = C.B.A + C.\overline{B}.A + C.\overline{B}.\overline{A} + \overline{C}.B.A + \overline{C}.\overline{B}.A$

| C/BA | 00 | 01 | 10 | 11 |
|------|----|----|----|----|
| 0    |    | 1  |    | 1  |
| 1    | 1  | 1  |    | 1  |

$F = BA + \overline{B}.A+ C.\overline{B}$
