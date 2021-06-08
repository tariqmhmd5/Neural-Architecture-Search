Introduction

In this Repository, we are going to use an evolutionary algorithm for selecting the best
architecture of a neural network.

Part 1: Implementation

Data Loaders

Neuroevolution for NAS

1. we are interested in implementing a convolutional neural network
of the following form:

Conv2d → f(.) → Pooling → Flatten → Linear 1 → f(.) → Linear 2 → Softmax

However, we allow different choices in each building block:

	● Conv2d:

		○ Number of filters: 8, 16, 32

		○ kernel=(3,3), stride=1, padding=1 OR kernel=(5,5), stride=1,padding=2
	● f(.):

		○ ReLU OR sigmoid OR tanh OR softplus OR ELU

	● Pooling:

		○ 2x2 OR Identity

		○ Average OR Maximum

	● Linear 1:

		○ Number of neurons: 10, 20, 30, 40, 50, 60, 70, 80, 90, 100

	Altogether, there are 4500 possible configurations.

2. Implement an evolutionary algorithm for NAS:
	a. Think of appropriate mutation, recombination, and selection for chosen representation.

	b. Modify the objective function (i.e., classification error, ClassError) by adding a penalty for the number of weights in the CNN:
		
		Objective = ClassError + λ * Np/Nmax

	where Np denotes the number of weights of a model and Nmax is a number of weights of the largest possible neural network in the search space. Take λ = 0. 01.

	c. Each candidate network is trained for a couple of epochs (e.g., up to 10) in order to avoid potential problems with learning times.
	
	5. Evaluate the best-performing candidate network on the test set.					