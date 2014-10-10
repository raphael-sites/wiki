Hidden Markov Model (HMM)
===

> Some parts in this note are from following slide:
> http://www.cs.cmu.edu/~aarti/Class/10701/slides/Lecture17.pdf

Markov Assumption
---
Current observation only depends on past m observations

$$ p({\bf X}) = \prod_{i=1}^n p(X_n|X_{n-1}, ..., X_{n-m}) $$

![screen shot 2014-10-10 at 15 30 44](https://cloud.githubusercontent.com/assets/1029280/4588621/f13ea6de-5046-11e4-813b-64cb0dd43234.png)

Hidden Markov Models
---
![screen shot 2014-10-10 at 15 32 42](https://cloud.githubusercontent.com/assets/1029280/4588631/39ae7502-5047-11e4-9986-ce52a9e927e6.png)

---

![screen shot 2014-10-10 at 15 35 38](https://cloud.githubusercontent.com/assets/1029280/4588649/a49d9852-5047-11e4-897c-15b235795560.png)

---

![screen shot 2014-10-10 at 15 35 42](https://cloud.githubusercontent.com/assets/1029280/4588650/a5d5e3f0-5047-11e4-928c-e45caeb5edc4.png)

An example of HMM problem
---

A casino has two die

- fair
	- $ P(1) = P(2) = ... = P(6) = \frac{1}{6}$
- loaded
	- $ P(1) = P(2) = ... = P(5) = \frac{1}{10}$
	- $ P(6) = \frac{1}{2} $

![screen shot 2014-10-10 at 15 41 25](https://cloud.githubusercontent.com/assets/1029280/4588703/6f1c61b2-5048-11e4-99d4-6c403ba355c2.png)

**Observed sequence**
![screen shot 2014-10-10 at 15 45 34](https://cloud.githubusercontent.com/assets/1029280/4588738/0a083764-5049-11e4-8426-25ec1a846677.png)

**Hidden state transitions**
![screen shot 2014-10-10 at 15 45 37](https://cloud.githubusercontent.com/assets/1029280/4588739/0a124a10-5049-11e4-8fbe-d5bafe5a2d3d.png)

**HMM model**

![screen shot 2014-10-10 at 15 47 01](https://cloud.githubusercontent.com/assets/1029280/4588749/38bff36c-5049-11e4-8a20-b457719dea38.png)

**Solve problems**

![screen shot 2014-10-10 at 15 49 23](https://cloud.githubusercontent.com/assets/1029280/4588771/94ee74b0-5049-11e4-9bff-694ea4a7908f.png)

> In the learning problem, here $\theta$ should represents emission probabilities.

**Algorithms**

![screen shot 2014-10-10 at 15 53 33](https://cloud.githubusercontent.com/assets/1029280/4588798/1fffacb8-504a-11e4-8dd7-63ba832596a1.png)

Forward Algorithm
---
**Intuition**

<script src="http://www.gliffy.com/diagramEmbed.js" type="text/javascript"> </script><script type="text/javascript"> gliffy_did = "6296963"; embedGliffy(); </script>

**Evaluation problem**

![screen shot 2014-10-10 at 16 03 35](https://cloud.githubusercontent.com/assets/1029280/4588866/873bac6e-504b-11e4-9591-c31ae491b255.png)

**Forward probability**

![screen shot 2014-10-10 at 16 07 52](https://cloud.githubusercontent.com/assets/1029280/4588897/287b6600-504c-11e4-85b4-b4915084b0e0.png)

**Forward algorithm**

![screen shot 2014-10-10 at 16 07 58](https://cloud.githubusercontent.com/assets/1029280/4588898/28811604-504c-11e4-8423-9106db47c21c.png)

