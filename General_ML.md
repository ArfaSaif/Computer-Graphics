** Saving Optimizer States**

- momentum vector or other history tracking properties
- For example, the Adam optimizer tracks moving averages of the gradient and squared gradient. If you start training a model without restoring these data, the optimizer will operate differently. The updates will be different, so the optimizer will proceed along a different trajectory.
- that every GPU must maintain a copy of all the optimizer states (roughly 2–3x the number of model parameters) and also all the forward and backward activations.

** Memory Consumption **
- Memory in neural networks is required to store input data, weight parameters and activations as an input propagates through the network. In training, activations from a forward pass must be retained until they can be used to calculate the error gradients in the backwards pass. As an example, the 50-layer ResNet network has ~26 million weight parameters and computes ~16 million activations in the forward pass. If you use a 32-bit floating-point value to store each weight and activation this would give a total storage requirement of 168 MB. By using a lower precision value to store these weights and activations we could halve or even quarter this storage requirement.
- A greater memory challenge arises from GPUs' reliance on data being laid out as dense vectors so they can fill very wide single instruction multiple data (SIMD) compute engines, which they use to achieve high compute density. CPUs use similar wide vector units to deliver high-performance arithmetic. In GPUs the vector paths are typically 1024 bits wide, so GPUs using 32-bit floating-point data typically parallelise the training data up into a mini-batch of 32 samples, to create 1024-bit-wide data vectors. This mini-batch approach to synthesizing vector parallelism multiplies the number of activations by a factor of 32, growing the local storage requirement to over 2 GB.
- https://www.graphcore.ai/posts/why-is-so-much-memory-needed-for-deep-neural-networks#:~:text=Memory%20in%20neural%20networks%20is,gradients%20in%20the%20backwards%20pass.


** Data Sharding **
- In another method (distributed data parallel, DDP), each GPU trains on a subset of data, and gradients are synced across GPUs. This method also works across many machines (nodes). In this illustration, each GPU gets a subset of the data and initializes the model weights exactly the same across every GPU. Then after the backward pass, all gradients are synced and updated.
- However, this method still has the problem that every GPU must maintain a copy of all the optimizer states (roughly 2–3x the number of model parameters) and also all the forward and backward activations.
Sharded removes these redundancies. It works the same way as DDP except that all the overhead (gradients, optimizer state, etc) are calculated only for a portion of the full parameters and thus we remove the redundancy of storing the same gradient and optimizer states on all GPUs.
- So, each GPU stores only a subset of activations, optimizer parameters and gradient computations.




