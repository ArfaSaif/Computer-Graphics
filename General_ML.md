** Saving Optimizer States**

- momentum vector or other history tracking properties
- For example, the Adam optimizer tracks moving averages of the gradient and squared gradient. If you start training a model without restoring these data, the optimizer will operate differently. The updates will be different, so the optimizer will proceed along a different trajectory.
- that every GPU must maintain a copy of all the optimizer states (roughly 2–3x the number of model parameters) and also all the forward and backward activations.

** Memory Consumption **
- Memory in neural networks is required to store input data, weight parameters and activations as an input propagates through the network. In training, activations from a forward pass must be retained until they can be used to calculate the error gradients in the backwards pass. As an example, the 50-layer ResNet network has ~26 million weight parameters and computes ~16 million activations in the forward pass. If you use a 32-bit floating-point value to store each weight and activation this would give a total storage requirement of 168 MB. By using a lower precision value to store these weights and activations we could halve or even quarter this storage requirement.
