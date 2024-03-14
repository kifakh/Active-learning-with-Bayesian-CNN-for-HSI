# Hyperspectral Image Classification using Active Learning and Bayesian CNN (BALD)

This repository contains Python code for the classification of Hyperspectral Images (HSI) using Active Learning (AL) and Bayesian Convolutional Neural Networks (CNN) with the Bayesian Active Learning by Disagreement (BALD) acquisition function. The project focuses on leveraging AL techniques to select informative samples for annotation from a pool of unlabeled data, while utilizing Bayesian CNNs to provide uncertainty estimates in the classification process. The dataset used for experimentation is the Indian Pines University dataset.

## Active Learning (AL)

In AL, the learner iteratively selects samples from an unlabeled pool based on an acquisition function, with the goal of minimizing the posterior entropy and selecting samples that would be highly informative if their labels were known. The BALD acquisition function measures the model uncertainty regarding the output and the expected conditional uncertainty, penalizing parameter uncertainty caused by inherent noise and rewarding data points with high output entropy.

## Bayesian CNN with BALD

The Bayesian CNN implementation uses dropout after each parameter layer to yield the expected class probabilities. Monte Carlo dropout samples are generated at test time to approximate the posterior distribution. The Dropout BALD acquisition function is computed using Monte Carlo samples of predicted class probabilities, where the AL selects samples based on the predicted information gain.

## Acquisition Function

The acquisition function is formulated as:

U(x) = H[1/k ∑(p(y_i | x_i))] - 1/k ∑(H(p(y_i, x_i)))

Where:
- H[1/k ∑(p(y_i | x_i))] measures the entropy of the average predicted probability, selecting locations where the model's average output is most uncertain.
- 1/k ∑(H(p(y_i, x_i))) seeks points where the average uncertainty is low.


## Conclusion

This project demonstrates the application of Active Learning with Bayesian CNN using the BALD acquisition function for Hyperspectral Image Classification. By selecting informative samples for annotation and providing uncertainty estimates, the approach enhances classification performance and enables more informed decision-making in remote sensing applications.


