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

- Intuition

<script src="http://www.gliffy.com/diagramEmbed.js" type="text/javascript"> </script>
<script type="text/javascript"> gliffy_did = "6296169"; embedGliffy(); </script>


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
# Dictionary
DICT = {A: "A", B: "B", CRUISE: "CRUISE", STAND: "STAND"}
```

- Optimization
```python
def optimize(states, actions, R, T):
    epsilon = 0.0001; gamma = 0.8; max_iters = 100
    V = {}; V2 = {}
    logs = {};
    for s in states:
        logs[s] = {}
        for a in actions:
            logs[s][a] = []
        
    for s in states:
        V[s] = 0
        V2[s] = 0
    for iteration in range(max_iters):
        for s in states:
            value_candidates = []
            for a in actions:
                value = R[a][s] + gamma * sum(T[a][s][s2]*V[s2] for s2 in states)
                value_candidates.append(value)
                logs[s][a].append(value)
            V2[s] =max(value_candidates)
        if max(abs(V2[s] - V[s]) for s in states) < epsilon:
            return V2, logs
        else:
            V = V2; V2 = {}
    return V2, logs

def draw_table(states, actions, R, T, V):
    for s in states:
        for a in actions:
            value = R[a][s] + gamma * sum(T[a][s][s2]*V[s2] for s2 in states)
            print "State: %s Action: %s --> %f" % (DICT[s], DICT[a], value)

states = [A, B]
actions = [CRUISE, STAND]
optimized_V, logs = optimize(states, actions, R, T)
print "Iterations:", len(logs[A][STAND])
draw_table(states, actions, R, T, optimized_V)
```

> Iterations: 56
> 
> State: A Action: CRUISE --> 74.907603
> 
> State: A Action: STAND --> 80.789182
> 
> State: B Action: CRUISE --> 101.118129
> 
> State: B Action: STAND --> 94.236550

```
from matplotlib import *
x_axis = range(1, 1 + len(logs[A][STAND]))
for s in states:
    for a in actions:
        plot(x_axis, logs[s][a], label="State %s, Action %s" % (DICT[s], DICT[a]))
pyplot.legend(loc=4)
show()
```

> ![screen shot 2014-10-10 at 13 02 44](https://cloud.githubusercontent.com/assets/1029280/4587759/4fe661dc-5032-11e4-8e88-e0dc5476ef9c.png)

- Conclusion

After optimization, the best action for state A is STAND, for B is CRUISE