# MP Neuron

## Overview

| Feature        | MP Neuron                                                    | Hebbian Neuron                                               | Oja's Rule (Normalised Hebbian)                              | Kohonen's Rule                                               |
| :------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| **Input**      | Binary (0 or 1)                                              | Binary or real                                               | Binary or real                                               | Real, Unlabelled                                             |
| **Weight**     | Fixed (1 or -1), no weight update                            | **Real**, random init, updated                               | Real, random init, **normalised**, updated                   | Real, updated, one output neuron's weights are updated at any instant |
| **Output**     | Binary (0 or 1), based on inhibitory inputs and threshold    | Binary or real, based on activation function                 | Binary or real                                               | Real (weighted sum)                                          |
| **Learning**   | No learning                                                  | Unsupervised.<br>Weights update: $w_i^{t+1} = w_i^t + \Delta w_i$, where $\Delta w_i = C a_i^t X^{t+1}$ | Unsupervised, Normalised.<br>Weights update: same as Hebb's rule. | Unsupervised, Competitive                                    |
| **Concepts**   | First mathematical model, "All-or-nothing" firing of neurons, logic gates, memory cell | "Fire together, wire together", weight divergence            | Normalisation, weight convergence (to the principal eigenvector of the input covariance matrix) | "Winner-takes-it-all", Self-Organising Map (SOM)             |
| **Activation** | Threshold function:<br>$X = 0$ if any inhibitory input is active or $S < \theta$<br/>$X = 1$ if $S \ge \theta$ | Activation function:<br>$X^{t+1} = 1$ if $S^t \ge \theta$<br/>$X^{t+1} = 0$ if $S^t < \theta$ | Same as Hebb's rule.                                         | N/A (Activation is implicit in the weighted sum calculation and the identification of the neuron with the highest weighted sum or smallest distance) |

- In the table above, $C$ is the learning rate, $x_i$ is the input value for the $i_{th}$ neuron, $y$ is the output of the neuron ($x$ and $y$ are vectors).
- $w_i$ represents the weight of the $i_{th}$ connection, $a_i$ is the $i_{th}$ input, $\theta$ is the neuron threshold value.
- $S$ is the weighted sum, $X$ is the output. $t$ is the time step.

## MP Neuron

### Geometric Interpretation Based on Linear Separability

- Number of **inputs** = number of dimensions.
- **Weights** form a vector perpendicular to the linear boundary.
- **Threshold** determines how far the boundary is from the origin.

### Logic Gates

- Cannot implement XOR.

### Memory Cell

- **Register cell**: single neuron with single input and with the weight and threshold both set to 1.
- **Memory cell**: Add a feedback loop and an inhibitory input to register cell.

## Hebb's Rule

### Weight Divergence

- Reflects the most important features of the average $\bar{a}$

## Oja's Rule

### Normalisation

- $w_i^{\text{norm}} = \frac{w_i}{\lVert w \rVert}$, where $\lVert w \rVert = \sqrt{w_1^2 + w_2^2 + \ldots + w_n^2}$
- Then check convergence criteria: $\max_{i} \limits |w_i^t - w_i^{t-1}| \leq \delta$

### Weight Convergence

- Convergence is achieved when the weight vector converges to the eigenvector corresponding to the largest eigenvalue of the input’s covariance matrix.

## Kohonen's Rule

### Steps

1. Find the winner: $S_j^t = \max(S_1^t, \dots, S_m^t) $
2. Update its weights: $w_{ji}^{t+1} = w_{ji}^t + \Delta w_{ji}^t$, where $\Delta w_{ji}^t = C(a_i^t - w_{ji}^t)$

### Self-Organising Map

- Core concept: not only update the winner, but also update its neighbours.
- $\Delta w_{ji}^t = C(a_i^t - w_{ji}^t)\theta(j,j^\ast)$, where $j^\ast$ is the index of the winner, and $\theta(j,j^\ast)$ is a restraint function due to the distance between $j$ and $j^\ast$.

