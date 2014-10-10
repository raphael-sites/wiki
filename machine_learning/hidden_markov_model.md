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
