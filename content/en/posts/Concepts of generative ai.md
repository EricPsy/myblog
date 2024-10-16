---
title: "Some Concpets of Generative AI（Updating)"
date: 2024-10-15T06:45:57-07:10
author: He Chen
slug: first-post
draft: false
toc: true
categories:
  - Genarative AI
tags:
  - article
  - English

---

## Generative Fundamental

### Latent Space

> A compressed representation of data that the autoencoder creates in a simpler, smaller form, which captures the most important features needed to reconstruct or generate new data.

**Latent space decoding** refers to the process of reconstructing or generating data from the latent space representation. This concept is commonly used in deep learning, especially in generative models like autoencoders, GANs, and VAEs. In these models, data is first encoded into the latent space (compressed representation), and the decoding process involves transforming this compressed latent space back into a more understandable or usable form, such as an image or text.

So image we had just finished a wonderful trip and wanted to create a travel journal to recorder all the memorable moments. Its unrealistic to include all the photos in the journal due to the limited space in the book. However, we still want to capture all the special moments. One solution is to "code" the photos into simple descriptions, allowing us to  "decode" the momeries by reading these descriptions.

For example, by Reading the sentence " Great Ocean Road, viewing platform,London Bridge, blue sea, blue sky and white clouds. " we can recall the scene even if it's not exactly the same as the original.



### Parameters

**Parameters:** Parameters are the variables that the model learns during training. They are internal to the model and are adjusted through the learning process. In the context of neural networks, parameters typically include **weights** and **biases**.

- **Weights:** Weights are coefficients for the input data. They are used in calculations to determine the importance or influence of input variables on the model's output. In a neural network, each connection between neurons has an associated weight.

  > Weights can be ajusted. The adjustment of weights in a neural network is directly related to the backpropagation mechanism.

  - **Backpropagation** : backpropagation is the key algorithm that allow nerual networks to learn by adjusting their weights. The process involves computing the error (loss) between the predicted output and the actual target, and then using this error to update the weights through gradient descent.

  - **Gradient descent**: Gradient Descent is an optimization algorithm used to minimize the value of a function by iteratively adjusting its parameters (such as weights in machine learning models) in the direction of the steepest descent.

    > The gradient represents the direction and rate of the steepest increase of the function. To make it easier to understand, we can think of the **gradient** as the **derivative** in multiple dimensios, and the gradient is similar to the derivative: its sign indicates the direction of optimization. A **negative value** means the error is decreasing, while a **positive value** means the error is increasing. The magnitude of the **derivative** represents the speed of this ascent or descent. In other words, the larger the derivative, the faster the function value is changing.For the gradient, all the things are similar. 

- **Biases :** Biases are additional constants attached to neurons and are added to the weighted input before the activation function is applied. Biases ensure that even when all the inputs are zero, there can still be a non-zero output.

###  Hyperparameters

**Hyperparameters**: Hyperparameters, unlike parameters, are not learned from the data. They are more like settings or configurations for the learning process. They are set prior to the training process and remain constant during training. They are external to the model and are used to control the learning process.

- **Learning Rate** : The **learning rate** determines the step size for updating the model's parameters during each iteration. If the learning rate is too high, the model might overshoot the optimal solution; if the learning rate is too low, the model may converge very slowly or even get stuck in a local optimum.

- **Batch size**：The **batch size** determines how many training samples the model uses for each update. A larger batch size can make the training more stable, but it will consume more memory. A smaller batch size allows for faster updates, but it may lead to unstable gradient updates.

- **Epochs:** The **number of iterations (epochs)** refers to how many times the entire training dataset is used to train the model. The more epochs, the better the model's performance might become, but it's also important to prevent overfitting.

- **Regularization Parameters:** **Regularization parameters** (such as the coefficients for L1 and L2 regularization) are used to prevent the model from overfitting. They add a penalty term to the loss function based on the weights, controlling the complexity of the model.

- **Number of hidden layers and neurons**:  The number of hidden layers and the number of neurons in each layer determine the structural complexity of the neural network. More layers and neurons can make the model more powerful but can also increase the risk of overfitting.

- **Activation function**: The activation function determines the nonlinear transformation applied to each neuron's output. Common activation functions include ReLU, Sigmoid, and Tanh.

  - | **Activation Function** | **Formula**                              | **Output Range** | **Advantages**                                               | **Disadvantages**                                           | **Common Applications**                             |
    | ----------------------- | ---------------------------------------- | ---------------- | ------------------------------------------------------------ | ----------------------------------------------------------- | --------------------------------------------------- |
    | **ReLU**                | f(x)=max(0,x)                            | [0, ∞)           | Simple, efficient, avoids vanishing gradient in positive region | Can lead to "dead ReLU" problem where neurons stop learning | Deep networks, Convolutional Neural Networks (CNNs) |
    | **Sigmoid**             | f(x) = \frac{1}{1 + e^{-x}}              | (0, 1)           | Useful for probability outputs                               | Vanishing gradient, output not centered around zero         | Binary classification outputs                       |
    | **Tanh**                | f(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}} | (-1, 1)          | Zero-centered output, useful for symmetrical data            | Suffers from vanishing gradient issue                       | GANs, some hidden layers                            |

Since hyperparameters cannot be learned automatically through training, finding the right combination of hyperparameters relies on **tuning**.