# What is Cross-Entropy?

Cross entropy is a loss function that gives a glimpse into how well the learning process is progressing (lower numbers are better here). Cross-entropy gives us a way to express how different two probability distributions are. Values of the top multiplited by the a logarithms of the values of the bottom. element by element, then you sum all of the numbers across the whole vector. It has a minus sign  because the value are between 0 and 1. 

The training's objective is to make the cross entropy as small as possible, so you can tell if the learning is working by keeping an eye on whether the loss keeps trending downwards, ignoring the short-term noise.
