** Saving Optimizer States**

- momentum vector or other history tracking properties
- For example, the Adam optimizer tracks moving averages of the gradient and squared gradient. If you start training a model without restoring these data, the optimizer will operate differently. The updates will be different, so the optimizer will proceed along a different trajectory.
- that every GPU must maintain a copy of all the optimizer states (roughly 2–3x the number of model parameters) and also all the forward and backward activations.
