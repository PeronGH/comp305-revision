# MP Neuron

## Overview

| Feature        | MP Neuron                                                    | Hebbian Neuron                                          | Oja's Rule (Normalised Hebbian)                              | Kohonen's Rule                                               |
| :------------- | :----------------------------------------------------------- | :------------------------------------------------------ | :----------------------------------------------------------- | :----------------------------------------------------------- |
| **Input**      | Binary (0 or 1)                                              | Continuous                                              | Continuous                                                   | Continuous (Unlabelled)                                      |
| **Weight**     | Fixed (1 or -1)<br>no weight update                          | Arbitrary, updated                                      | Arbitrary, updated, normalised                               | Arbitrary, updated, one output neuron's weights are updated at any instant |
| **Output**     | Binary (0 or 1), based on inhibitory inputs and threshold    | Continuous, based on activation function (e.g., linear) | Continuous, based on activation function                     | Continuous, based on the weighted sum of each output neuron  |
| **Learning**   | No learning                                                  | Unsupervised: $\Delta w_i = Cx_iy$                      | Unsupervised, Normalised: $w_i^{t+1} = w_i^t + \Delta w_i^t$, where $\Delta w_i^t = C a_i^t X^{t+1} $ | Unsupervised, Competitive: $w_j^{t+1} = w_j^t + \Delta w_j^t$, where $\Delta w_j^t = C(a_i^t - w_{ji}^t)$ |
| **Concepts**   | First mathematical model, "All-or-nothing" firing of neurons, logic tables, no learning | "Fire together, wire together", weight divergence       | Weight convergence (to the principal eigenvector of the input covariance matrix) | Competitive learning, self-organising map (SOM), good for clustering and dimensionality reduction |
| **Activation** | Threshold function: $X = 1$ if $S \ge \theta$<br>$X = 0$ if $S < \theta$ | Linear or differentiable activation function            | Activation function: $x^{t+1} = g(s^t) = H(S^t - \theta)$<br>$x^{t+1} = 1$ if $S^t \ge \theta$<br>$x^{t+1} = 0$ if $S^t < \theta$ | N/A (Activation is implicit in the weighted sum calculation and the identification of the neuron with the highest weighted sum or smallest distance) |
| **Formula**    | Sum: $S = \sum_i w_i a_i $<br>Output:<br>$X = 0$ if any inhibitory input is active or $S < \theta$<br>$X = 1$ if $S \ge \theta$ | $\Delta w_i = Cx_iy$ (Update Rule)                      | Activation: $x^{t+1} = g(s^t) = H(S^t - \theta)$<br>$x^{t+1} = 1$ if $S^t \ge \theta$<br>$x^{t+1} = 0$ if $S^t < \theta$. Update: $w_i^{t+1} = w_i^t + \Delta w_i^t$ | Competition: $S_j^t = max(S_1^t, ..., S_m^t)$<br>Update: $w_{ji}^{t+1} = w_{ji}^t + \Delta w_{ji}^t$<br>Incremental: $\Delta w_{ji}^t = C(a_i^t - w_{ji}^t)$ |

- In the table above, $C$ is the learning rate, $x_i$ is the input value for the $i_{th}$ neuron, $y$ is the output of the neuron.
- $w_i$ represents the weight of the $i_{th}$ connection, $a_i$ is the $i_{th}$ input, $\theta$ is the neuron threshold value.
- $S$ is the weighted sum, $X$ is the output. $t$ is the time step.

## MP Neuron

### Geometric Interpretation Based on Linear Separability

- Number of **inputs** = number of dimensions
- **Weights** form a vector perpendicular to the linear boundary
- **Threshold** determines how far the boundary is from the origin
