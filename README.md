# IsoelasticMNIST

## Description

This small project explores how the choice of loss function impacts the training and final evaluation metrics of simple Machine Learning model. 

Based on the results in [Statistical Games](https://arxiv.org/abs/2402.15892), the family of loss functions has been chosen to be the isoelastic loss (or utility) functions, inspired by their "naturality" and their ability to unify Bayesian and frequentist inference methods:

$$
u_\gamma(c) = 
\begin{cases}
\frac{c^{1-\gamma} - 1}{1-\gamma} & \text{if } \gamma \ne 1, \\
\log(c) & \text{if } \gamma = 1.
\end{cases}
$$

Where $`\gamma \ge 0`$ is the so called relative risk aversion parameter.

The [MNIST](https://www.tensorflow.org/datasets/catalog/mnist) dataset has been chosen as a simple and controlled benchmark for the experiments, and a small two-layer Neural Network has been used as the model architecture.

The main evaluation metric is the accuracy of the model on the test set.

## Results

### The optimality of the standard cross-entropy loss

Naturally the choice of the loss functions impacts learning and final performance. There is a wide plateau of good performance around the cross-entropy loss (which corresponds to $`\gamma = 1`$), but for higher and lower values of $`\gamma`$ learning can break down.

### Observations for the case of non-aligned training losses

For approximative learning algorithms, with finite compute it is sometimes better to chose a loss function that is not totally aligned with the true objective, because that provides better gradients for learning. The results show that isoelastic loss with $`\gamma \in  [0.5, 1.3]`$ gives similarly high accuracy as the cross-entropy loss. However, for higher and lower values of $`\gamma`$, the performance degrades – sometimes significantly.

Raw accuracy corresponds to isoelastic loss with $`\gamma \to 0`$, therefore this is a simple demonstartion where a training loss different from the true objective can lead to better performance – even if we compare the final result based on the final objective (accuracy).

## Short Video-summary

For a short (~3 min) video summary of the project in its early stage follow this Google Drive link: [ShortProjectPresentation.mp4](https://drive.google.com/file/d/1ggiQcoXYVd9lQKajdHN4FciZQN955b8_/view?usp=drive_link)


## Requirements

- Python 3.10+
- PyTorch 2.7+

## Related works, links, and resources

- [LossMNIST](https://github.com/BKHMSI/LossMNIST) project on GitHub
- [Statistical Games](https://github.com/Konczer/UncertaintyTheory/tree/main/StatisticalGames) project page on GitHub and the related [arXiv paper]((https://arxiv.org/abs/2402.15892))