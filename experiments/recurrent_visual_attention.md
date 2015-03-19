
# Recurrent visual attention model
(Experiment notes)

### Solve zero-gradient problem for gaussian pdf function in theano
#### (2015/3/19)

Consider sampled position as a constant in T.grad.

Runs with theano 0.6.

```python
_tanh = nnprocessors.build_activation("tanh")

wl = theano.shared(np.array([[0.2,0.3], [0.1,0.3]], dtype="float32"))
h_t = T.constant(np.array([0.1,0.2]))
l_t = _tanh(T.dot(h_t, wl))
sampled_l_t = _sample_gaussian(l_t, T.constant(np.array([[0.1,0],[0,0.1]]), dtype="float32"))
sampled_pdf = _multi_gaussian_pdf(sampled_l_t, l_t)

g = T.grad(T.log(sampled_pdf), wl, known_grads={sampled_l_t: theano.gradient.DisconnectedType()()})

f = theano.function([], [l_t, sampled_pdf, g])
f()
```

### REINFORCE learning for the policy of location network
#### (2015/3/19)

In the paper, the policy is defined as multivariate gaussian pdf of position.

Then the REINFORCE algorithm learns the gradient of this log probability wrt. weight of location network

This never worked in my experimental setting, instead, it seems the following simple gradient can make REINFORCE work.

$$ \nabla_{\theta}{l_t} $$