# Perceptron

## Introduction

- Similar to a 2-layer Feedforward Neural Network
- Activation function for $j_{\text{th}}$ output:
  - $X_j = 1$ if $S_j \ge \theta$
  - $X_j = 0$ if $S_j < \theta$
- **Supervised** (error is calculated based on the network's output and the input label)

## Training

- **Dataset** $D$
  - The $k_{\text{th}}$ entry: $a_1^k, \cdots, a_n^k \rArr t_1^k \cdots t_m^k$ (input labels to output labels).

- **Steps**:
  1. Check convergence: $RMS \le \delta$.
     - $RMS = \sqrt{\frac{\sum_{k=1}^{r}\sum_{j=1}^{m}\left(e_{j}^{k}\right)^2}{rm}} = \sqrt{\frac{\sum_{k=1}^{r}\sum_{j=1}^{m}\left(t_{j}^{k} - X_{j}^{k}\right)^2}{rm}}$
       - $r$: the number of patterns in the data set.
       - $m$: the number of output neurons.
  2. Pick random entry from $D$.
  3. Insert $a_0=1$.
  4. For $i_{\text{th}}$ input and $j_{\text{th}}$ output, update their connection weight by $\Delta w_{ji} = Ce_ja_i$.
     - Where $e_j = t_j - Xj$ (difference between target label and actual output).
  5. Repeat from step 1.

### Convergence

- Converge when $D$ is linear separable.