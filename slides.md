---
# try also 'default' to start simple
# theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Seminar
info: |
  Seminar
# apply UnoCSS classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
# transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
---

## ASSUMPTIONS OF LINEAR PROGRAMMING

<div class="mt-12 py-1" hover:bg="white op-10">
  Zhao Zhiyu
</div>

<!--
Hello everyone. My name is Zhao Zhiyu.
My research is about helping robots find the best path in a busy warehouse.
-->

---
layout: 'default'
---

# Assumption 1: Proportionality

### Definition
*   The contribution of each activity ($x_j$) to the objective function ($Z$) is proportional to its level (e.g., $c_j x_j$).
*   The contribution of each activity to each constraint is also proportional to its level (e.g., $a_{ij} x_j$).

### Implication
*   The exponent of any variable in the objective function or constraints must be **1**.
*   This means no non-linear terms like $x^2$, $\sqrt{x}$, or $x_1 x_2$.
*   This is the "Linear" part of **Linear** Programming.

### Example (Wyndor Glass Co.)
*   Assume profit for Product 1 is $3x_1$.
*   If $x_1 = 1$ (1 batch), then Profit = **$3k**.
*   If $x_1 = 2$ (2 batches), then Profit = **$6k**.
*   The profit ($6k$) is exactly **twice** the profit for 1 batch ($3k$), satisfying the assumption.

---
layout: 'default'
---

# When is Proportionality Violated?

The assumption is violated when the marginal contribution (profit or cost) of an activity changes.

### 1. Start-up Costs
*   **Description:** A fixed cost is incurred as soon as an activity begins ($x_1 > 0$).
*   **Example:** The profit function becomes $3x_1 - 1$ (if $x_1 > 0$), but is 0 if $x_1 = 0$.

### 2. Economies of Scale (Increasing Returns)
*   **Description:** Efficiency increases as the activity level grows (e.g., bulk discounts, learning curves), increasing the profit margin per unit.

### 3. Diminishing Marginal Returns
*   **Description:** Costs rise as the activity level increases (e.g., needing more advertising or price cuts to sell more), decreasing the profit margin per unit.

<br>

### What If It's Violated?
*   **For Start-up Costs:** Use **Mixed-Integer Programming (MIP)**.
*   **For Changing Marginal Returns:** Use **Non-Linear Programming (NLP)**.

---
layout: 'default'
---

## Assumption 2: Additivity

### Definition
*   Every function in an LP model (objective or constraint) must be the sum of the individual contributions from each activity.

### Implication
*   This assumption rules out any **cross-product terms** (terms involving the product of two or more variables, such as $x_1 x_2$).

### Violation Examples (Objective Function)
*   **Case 1: Complementary Products**
    *   Joint promotion (e.g., shared advertising) makes total profit *greater* than the sum of individual profits.
    *   Example: $Z = 3x_1 + 5x_2 + x_1 x_2$

*   **Case 2: Competing Products**
    *   Products compete for resources (e.g., production line changeover time) making total profit *less* than the sum of individual profits.
    *   Example: $Z = 3x_1 + 5x_2 - x_1 x_2$

### What If It's Violated?
*   The model will contain non-linear terms and must be solved using **Non-Linear Programming (NLP)**.

---
layout: 'default'
---

# Assumption 3: Divisibility

### Definition
*   Decision variables are allowed to take any value, including non-integer (fractional) values, that satisfies the constraints.
*   Assumes that activities can be run at fractional levels.

### Example (Wyndor Glass Co.)
*   The decision variables represent **production rates** (e.g., number of batches produced *per week*).
*   A production rate can be fractional (e.g., $x_1 = 2.5$ batches/week).
*   Therefore, the assumption holds in this context.

### What If It's Violated?
*   This occurs if some or all decision variables *must* be integers (e.g., you cannot build 0.5 airplanes or assign 0.5 employees).
*   The model becomes an **Integer Programming (IP)** model.

---
layout: 'default'
---

# Assumption 4: Certainty

### Definition
* All parameter values in the model—objective function coefficients ($c_j$), constraint coefficients ($a_{ij}$), and right-hand-side values ($b_i$)—are assumed to be known, exact constants.

### Reality
* In practice, this assumption is rarely met perfectly.
* LP models often use predictions about the future, which inherently involves uncertainty.

### How to Handle?
* After finding a solution, it is crucial to perform **Sensitivity Analysis**.
* This analysis identifies "sensitive parameters"—those whose values cannot change without changing the optimal solution.
* If uncertainty is very high, other methods may be required.

---
layout: 'default'
---

# The Assumptions in Perspective

*   **Models are Idealizations, Not Reality**
    *   Assumptions are necessary to make the problem **tractable** (solvable).

*   **Minor Violations are Common**
    *   In practice, assumptions are rarely met perfectly, which is often acceptable.

*   **The Goal is "Reasonable Approximation"**
    *   The model's predictions just need to correlate well with the real world.

*   **Serious Violations Require New Models**
    *   If assumptions are badly broken, LP is not the right tool.
    *   Consider using Non-Linear or Integer Programming instead.

---
layout: 'default'
---

<div style="transform: scale(0.57); top: -240px; position: relative;">

```python
import gurobipy as gp
from gurobipy import GRB

costs = {
    'Shift_1': 170, 'Shift_2': 160, 'Shift_3': 175, 'Shift_4': 180, 'Shift_5': 195
}

min_needed = {
    (6, 8): 48, (8, 10): 79, (10, 12): 65, (12, 14): 87, (14, 16): 64,
    (16, 18): 73, (18, 20): 82, (20, 22): 43, (22, 24): 52, (0, 6): 15
}

shift_coverage = {
    'Shift_1': [(6, 8), (8, 10), (10, 12), (12, 14)],
    'Shift_2': [(8, 10), (10, 12), (12, 14), (14, 16)],
    'Shift_3': [(12, 14), (14, 16), (16, 18), (18, 20)],
    'Shift_4': [(16, 18), (18, 20), (20, 22), (22, 24)],
    'Shift_5': [(22, 24), (0, 6)]
}

m = gp.Model("PersonnelScheduling")

shifts = list(costs.keys())
x = m.addVars(shifts, vtype=GRB.INTEGER, name="agents")

m.setObjective(gp.quicksum(costs[j] * x[j] for j in shifts), GRB.MINIMIZE)

for (start, end), needed in min_needed.items():
    covering_shifts = []
    for shift, intervals in shift_coverage.items():
        if (start, end) in intervals:
            covering_shifts.append(shift)
    
    m.addConstr(
        gp.quicksum(x[j] for j in covering_shifts) >= needed, 
        name=f"Time_{start}_{end}"
    )

m.optimize()

print(f"cost: ${m.ObjVal:.2f}")
for j in shifts:
    if x[j].X > 0.001:
        print(f"  {j}: {int(x[j].X)}")

# cost: $30610.00
#   Shift_1: 48
#   Shift_2: 31
#   Shift_3: 39
#   Shift_4: 43
#   Shift_5: 15
```

</div>

---
layout: 'default'
---

<div style="transform: scale(0.6); top: -180px; position: relative;">

```python
import gurobipy as gp
from gurobipy import GRB

lanes, costs, capacities = gp.multidict({
    ('F1', 'F2'): (2, 10),
    ('F1', 'DC'): (4, float('inf')),
    ('F1', 'W1'): (9, float('inf')),
    ('F2', 'DC'): (3, float('inf')),
    ('DC', 'W2'): (1, 80),
    ('W1', 'W2'): (3, float('inf')),
    ('W2', 'W1'): (2, float('inf'))
})

demand = {
    'F1': 50, 'F2': 40, 'DC': 0, 'W1': -30, 'W2': -60
}

nodes = list(demand.keys())

m = gp.Model("DistributionNetwork")

x = m.addVars(lanes, obj=costs, ub=capacities, name="ship")

m.ModelSense = GRB.MINIMIZE

m.addConstrs(
    (x.sum(i, '*') - x.sum('*', i) == demand[i] for i in nodes),
    name="NetFlow"
)

m.optimize()

print(f"cost: ${m.ObjVal * 100:.2f}")
for i, j in lanes:
    if x[i, j].X > 0.001:
        print(f"  {i} -> {j}: {x[i, j].X} ")

# cost: $49000.00
  # F1 -> DC: 40.0
  # F1 -> W1: 10.0
  # F2 -> DC: 40.0
  # DC -> W2: 80.0
  # W2 -> W1: 20.0

```
</div>