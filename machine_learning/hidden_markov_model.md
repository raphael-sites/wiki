Hidden Markov Model (HMM)
===

> Some parts in this note are from following slide:
> http://www.cs.cmu.edu/~aarti/Class/10701/slides/Lecture17.pdf

<i class="icon-file"></i> [**Codes for this note**](http://nbviewer.ipython.org/github/zomux/notebook/blob/master/Hidden%20Markov%20Model.ipynb)

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

Backward Algorithm
---
**Decoding problem**

![screen shot 2014-10-10 at 17 15 28](https://cloud.githubusercontent.com/assets/1029280/4589583/a9064264-5055-11e4-8b24-c5c9684cfffa.png)

> Here, the joint probability is divided into two parts.

**Backward algorithm**

![screen shot 2014-10-10 at 17 15 44](https://cloud.githubusercontent.com/assets/1029280/4589584/a90a00f2-5055-11e4-81c6-eed4572ec0dd.png)

---

![screen shot 2014-10-10 at 17 15 52](https://cloud.githubusercontent.com/assets/1029280/4589582/a905c500-5055-11e4-9b9b-30c40ba604d8.png)

Viterbi Algorithm
---

**Decoding problem 2**

![screen shot 2014-10-10 at 17 55 13](https://cloud.githubusercontent.com/assets/1029280/4590038/2a7669fa-505b-11e4-97fe-2b42a2d5faad.png)

**Viterbi Decoding**

![screen shot 2014-10-10 at 17 55 18](https://cloud.githubusercontent.com/assets/1029280/4590040/2ad867e0-505b-11e4-9613-5b0577a80efb.png)

**￼Viterbi Algorithm**

![screen shot 2014-10-10 at 17 55 22](https://cloud.githubusercontent.com/assets/1029280/4590039/2a793644-505b-11e4-9143-36bb7a5453c9.png)

**￼Computational complexity**

![screen shot 2014-10-10 at 17 55 27](https://cloud.githubusercontent.com/assets/1029280/4590037/2a763642-505b-11e4-8745-26ad82a2e28b.png)
