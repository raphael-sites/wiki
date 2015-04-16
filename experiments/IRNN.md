# A Simple Way to Initialize Recurrent Networks of Rectified Linear Units

[Original paper](http://arxiv.org/abs/1504.00941)

# Key idea

Initializing recurrent weight matrix in RNN with identity matrix, and using ReLU for activation

# Experiment notes

The empirical results are able to reproduce but not easy. The training process is highly unstable.

For the toy problem, it turns out the optimization algorithm will first find a local optima. Obviously, returning 1 should be a good choice if the network failed to learn the knowledge about how to compute the sum. May be better to avoid this kind of consistent mean.

At some point, the optimization algorithm will find a super-steep slope gives huge gradient. Gradient clipping is not a final solution.

# Some tricks to make the training more stable (slightly)

- Bound the identity weight matrix to [0, 0.99]
- Learning rate decay