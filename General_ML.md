** Saving Optimizer States**

- momentum vector or other history tracking properties
- For example, the Adam optimizer tracks moving averages of the gradient and squared gradient. If you start training a model without restoring these data, the optimizer will operate differently. The updates will be different, so the optimizer will proceed along a different trajectory.
