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

<div class="mxgraph" style="position:relative;overflow:hidden;width:361px;height:91px;"><div style="width:1px;height:1px;overflow:hidden;">xVRNk5swDP01HDvDR0qTa7Jp99JTDnt2sQBPDWKMSSC/PjbIcbw0O7OX7Qnryfp4TzJRdmjGX4p19W/kIKM05mOUvURpmuQ/EvOxyLQg2zhfgEoJTpc8cBJXIDAmdBAc+uCiRpRadCFYYNtCoQOsRBmW6Fjl0nvgVDC5Rt8E1zW1nFLLFn8FUdWuTJLvFk+vJ5eDQ8kGqb/NkPFZd8NcLmI1xou5ofjpnd2xNujoitgEgILeS0VsBbVFNf6g4qACSIr276Ns2dGMTiGaQHtqxgNIOz43mSXs5xPvXS0FbVD6WQCpcWZyoNb7kvW8XGl4qYWGU8cKa1/MYlEgKA1us9bFPSWzjYANaDVZrRfvd9KA9tCZFz/nxMlUP8w4J4yRbtU9sSdqDsT137yz/8k73YXEt19IfLNiCNw8ODJR6RorbJk8enSvcGg52ATmTeyLQZ1ng3jb+I+FMOVwULOCfuU0UxXQrXkaa7kUSKbFOcz+CfLG9C9p9j38EbPjDQ==</div></div>



<script type="text/javascript" src="https:/a/www.draw.io/embed.js"></script>


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

