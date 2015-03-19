
# Recurrent visual attention model
(Experiment notes)

### REINFORCE learning for the policy of location network

(2015/3/19)
In the paper, the policy is defined as multivariate gaussian pdf of position.

Then the REINFORCE algorithm learns the gradient of this log probability wrt. weight of location network

This never worked in my experimental setting, instead, it seems the following simple gradient can make REINFORCE work.

$$ \nabla_{\theta}{l_t} $$