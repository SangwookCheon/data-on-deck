---
layout: post
title: ImageNet and the Development of Convolutional Neural Networks (CNN)
tags:
  - summary
  - ml
description:
published: true
---

*Research Paper Summarized:*

[ImageNet Classification with Deep Convolutional
Neural Networks](https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf) written by Alex Krizhevsky, Ilya Sutskever, and Geoffrey E. Hinton.

----

Today, we take near-perfect image recognition for granted. There are massive pre-trained models that keep on rolling based on new images added day by day. But where did it start?

Not long after scientists tackled the monumental challenge of identifying dogs and cats, using traditional fully-connected neural networks, researchers from the University of Toronto worked on a revolutionary model: Convolutional Neural Networks, or CNN for short. Many say that this was the turning point for deep learning.

The idea of convolutions was around for many decades, but this team enlivened the concept and showcased it to the public.

<!--break-->

The [research paper](https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf)they published caught two rabbits at the same time. First, they described the structure of CNN. Second, they broke the record in the ImageNet Large-Scale Visual Recognition Challenge (LSVRC).

 The ImageNet provided over 15 million real-life images of objects or animals, all labelled manually by humans. A picture of an umbrella would be labelled “umbrella.” There are more than 22,000 categories, and the challenge is to develop a model that can classify all images. When the model outputs one most-probably category, Top-1 error rate is calculated to quantify its accuracy. ImageNet also wants Top-5 error rate, which looks if any of the five best guesses from the model is correct.

# The Structure of CNN
After many trials and tweaks, the team showed the architecture of CNN that worked best.

## ReLU Activation Function
For many years, sigmoid or hyperbolic tangent (tanh) functions were popular choices when ‘activating’ the outputs of neurons. This team, however, decided to use a new method called Rectified Linear Units, or ReLUs. The previous functions cause the outputs to become saturated towards 0 or 1 if they are very large or small. These saturated values cause their gradients to be close to zero, which slows down learning. Learning of the model is called “gradient descent,” and when gradients are small, the model is updated by an insignificant amount.

ReLU solves this problem because is does not saturate. As the output reaches infinity, the activated value reaches infinity. ReLU is given by a surprisingly simple formula: max(0, x).

When outputs are less than zero, the neocons do not contribute to learning. When they are positive, gradients are calculated accordingly.

The team emphasised that ReLU is the biggest contributor to better results. Thus, it is not surprising that ReLU and its slight variations (leaky ReLU) have gained popularity.

## Pooling
The team also used “overlapping pooling.” Pooling is all about reducing the size of images, or downsampling, which allows distinct features to stand out more and reduces computational cost. When pooling, a box of certain size goes through the image like wiping a window. If max pooling is chosen, then the largest pixel value in each box gets to represent that whole box, simultaneously downsampling the image. The team found that using overlapping boxes—with the shape of a rectangle—reduces overfitting. Using a square-shaped pooling layer will result in non-overlapping pooling.

Here is the outline of the structure:

* Images as Input (224 • 224 • 3)
1.  Max Pooling Layer
2. Max Pooling Layer
3.  Convolutional Layer
4. Convolutional Layer
5.  Max Pooling Layer
6. Dense Layer
7. Dense Layer
8. Softmax and Output (as probability for each of the 1000 categories chosen).

ReLU activation function is applied to every layer.

The first five layers break images down into smaller features. The details of the size of each convolution are omitted.

The last three layers are fully-connected (called Dense layers), meaning that the connected neurons directly contribute weights that determine the probabilities at the end. The previous layers analyse and simplify (or downsample) the images, and these layers _determine_ what they are. The final layer distributes the probability of value 1 to 1000 categories, using the Softmax technique.

# Reducing Overfitting
Overfitting is what everyone fears. The weights of the model can become so specifically tailored towards the training set that it cannot ‘generalize’ for the test set. To give an arbitrary example, the accuracy might reach 99% for train set, but 50% when testing it with images that the model never saw. The researchers saw this problem early, so they used techniques that soon became nuts and bolts of the toolbox.

The first one is Data Augmentation. Increasing the size of the training set gives more variety for the model. With the images given by ImageNet, researcher thought of ways to add slight variations. Here are some ways to transform an image: translate it, flip it horizontally, rescaling it, and change the intensity of RGB values.

The second one is Dropout: switching off neurons with a set probability, that is, setting zero as their output. Every feed-forward (showing images to neurons), a random set of neurons do not contribute so that a brand-new model updates the weights every time. This dynamics prevents neurons from forming gridlocked relationships.

# Notes on Variables that are Manually Changed.
These are called “hyperparameters.” Machine Learning often involves intuition and creativity because tuning these parameters affect the result significantly. They are different from the basic _structure_ of the model—the order of layers, depth, width, dimensions, etc. Scientists manually change the parameters, test the accuracy, and then tweak them again until they are confident about their choice.

Hyperparameters include learning rate, optimiser, number of epochs (iterations), dropout probability, etc. The more complex the model is, the more parameters scientists have to juggle. I once wished machine learning never involves ‘guess and check,’ but this is the reality. Professionals often tell us that experience strengthens their intuition.

There are some systematic ways of trying different ‘sets’ of hyper parameters, like random forest, but this is outside the scope of this paper.

----

With two GPUs, it took researchers five to six days to train the model. Thankfully, the speed of GPUs developed rapidly like microchips. Kaggle—a popular data science platform— provides free online GPU that allows large models to be trained.

Also, the job of creating a CNN became so much simpler. Keras is a stellar python library that allows people to focus on building, not on the technical details and subtle math.

I took the first step of reading research papers by starting at the exact point where deep learning took off. It will take some time to catch up with the pace of research, but I am sure I will get there soon.

The biggest challenge is grasping the ambiguous technical terms, such as “stationarity of statistics” and “locality of pixel dependencies.” I found that online helper-tools like Stack Exchange are the best because a lot of people had the same issue. I felt comforted taking a glimpse at the journey of fellow practitioners. It can be rocky sometimes (as it is now), but I should have faith that I can help someone very soon. Machine Learning community is vibrant and supportive, so rather than looking up the dictionary, let’s read people’s words.

After all these years looking at textbooks and articles to learn machine learning, I am ready to jump into the exciting part: absorbing research papers.
