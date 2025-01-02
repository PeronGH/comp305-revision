# MP Neuron

## Overview

| Feature        | MP Neuron                                                    | Hebbian Neuron                                          | Oja's Rule (Normalised Hebbian)                              | Kohonen's Rule                                               |
| :------------- | :----------------------------------------------------------- | :------------------------------------------------------ | :----------------------------------------------------------- | :----------------------------------------------------------- |
| **Input**      | Binary (0 or 1)                                              | Can be continuous                                       | Continuous                                                   | Continuous (Unlabelled)                                      |
| **Weight**     | Fixed (1 or -1); no weight update                            | Arbitrary, updated                                      | Arbitrary, updated, normalised                               | Arbitrary, updated, one output neuron's weights are updated at any instant |
| **Output**     | Binary (0 or 1), based on threshold                          | Continuous, based on activation function (e.g., linear) | Continuous, based on activation function                     | Continuous, based on the weighted sum of each output neuron  |
| **Learning**   | No learning                                                  | Unsupervised: $ \Delta w_i = Cx_iy$                     | Unsupervised, Normalised: $w_i^{t+1} = w_i^t + \Delta w_i^t$, where $\Delta w_i^t = C a_i^t X^{t+1} $ | Unsupervised, Competitive:  $w_j^{t+1} = w_j^t + \Delta w_j^t$, where $\Delta w_j^t = C(a_i^t - w_{ji}^t)$ |
| **Concepts**   | First mathematical model, "All-or-nothing" firing of neurons, logic tables, no learning | "Fire together, wire together", weight divergence       | Weight convergence (to the principal eigenvector of the input covariance matrix) | Competitive learning, self-organising map (SOM), good for clustering and dimensionality reduction |
| **Activation** | Threshold function                                           | Linear or differentiable activation function            | Activation function $x^{t+1} = g(s^t) = H(S^t - \theta) = \begin{cases} 1, & S^t \ge \theta \\ 0, & S^t < \theta \end{cases}$ | N/A (Activation is implicit in the weighted sum calculation and the identification of the neuron with the highest weighted sum or smallest distance) |
| **Formula**    | $S = \sum_i w_i a_i $;<br>$X = \begin{cases} 1 & \text{if } S \ge \theta \\ 0 & \text{if } S < \theta \end{cases}$ | $ \Delta w_i = Cx_iy$ (Update Rule)                     | $x^{t+1} = g(s^t) = H(S^t - \theta) = \begin{cases} 1, & S^t \ge \theta \\ 0, & S^t < \theta \end{cases}$ (Activation);<br>$w_i^{t+1} = w_i^t + \Delta w_i^t$ (Update); | $S_j^t = max(S_1^t, ..., S_m^t)$ (Competition);<br>$w_{ji}^{t+1} = w_{ji}^t + \Delta w_{ji}^t$ (Update);<br>$\Delta w_{ji}^t = C(a_i^t - w_{ji}^t)$ (Incremental) |

*   In the table above, $C$ is the learning rate, $x_i$ is the input value for the $i_{th}$ neuron, $y$ is the output of the neuron.
*   $w_i$ represents the weight of the $i_{th}$ connection, $a_i$ is the $i_{th}$ input, $\theta$ is the neuron threshold value.
*   $S$ is the weighted sum, $X$ is the output. $t$ is the time step.
