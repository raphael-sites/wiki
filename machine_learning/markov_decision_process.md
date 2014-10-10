Markov Decision Process (MDP)
===

> Some parts of this page are from the slides of Stanford NLU Course.

Definition
---
![](https://cloud.githubusercontent.com/assets/1029280/4573167/530c9348-4f8f-11e4-9b7a-003ab91985fb.png)

Example
---

![](https://cloud.githubusercontent.com/assets/1029280/4573183/950d2050-4f8f-11e4-8e47-a195d1459d5a.png)

------

Optimization
---

![](https://cloud.githubusercontent.com/assets/1029280/4573220/120bd506-4f90-11e4-9f27-b9f00b6fc3dd.png)

![screen shot 2014-10-10 at 11 02 39](https://cloud.githubusercontent.com/assets/1029280/4586936/802b3f18-5021-11e4-8c38-07028a25eb71.png)


Simple Implementation
---

- Problem setting
```python
# States
A = 1
B = 2
CRUISE = 3
STAND = 4
# Transactions
T = {}
T[CRUISE] = {
    A: {A: 0.9, B: 0.1}, 
    B: {A: 0.1, B: 0.9}
}
T[STAND] = {
    A: {A: 0.4, B: 0.6}, 
    B: {A: 0.6, B: 0.4}
}
# Rewards
R = {
    CRUISE: {A: 8, B: 20}, 
    STAND: {A: 5, B: 22}
}
```

- Optimization
```python
def optimize(states, actions, R, T):
    epsilon = 0.0001; gamma = 0.8; max_iters = 100
    V = {}; V2 = {}
    logs = {};
    for s in states:
        logs[s] = []
    for s in states:
        V[s] = 0
        V2[s] = 0
    for iteration in range(max_iters):
        for s in states:
            V2[s] = max(R[a][s] + gamma * sum(T[a][s][s2]*V[s2] for s2 in states) for a in actions)
            logs[s].append(V2[s])
        if max(abs(V2[s] - V[s]) for s in states) < epsilon:
            return V2, logs
        else:
            V = V2; V2 = {}
            

states = [A, B]
actions = [CRUISE, STAND]
optimized_V, logs = optimize(states, actions, R, T)
print "optimized values:", optimized_V
print "iterations:", len(logs[A])
```

> optimized values: {1: 72.36809701684, 2: 92.10493912210316}
> 
> iterations: 56

```
from matplotlib import *
x_axis = range(1, 1 + len(logs[A]))
for s in states:
    plot(x_axis, logs[s], label="State %d" % s)
pyplot.legend(loc=4)
show()
```
> ![screen shot 2014-10-10 at 11 29 52](https://cloud.githubusercontent.com/assets/1029280/4587119/4f3f6c72-5025-11e4-908a-490d185142cc.png)
