---
title: Deep Learning Tutorials
layout: default
---

# Deep Learning Tutorials

Welcome to our Tutorials page. If you are just getting started with Deep Learning, and DeepLearning4J these tutorials will help clarify some of the concepts. Image recognition, Text processing and Classification examples are provided here. Some of the examples provide a written introduction along with code, while others over a screencast with voice of the code being written. Enjoy !

## Basic Neural Networks

### MNIST for Beginners

MNIST is the "Hello World" of machine learning. With this tutorial, you can train on MNIST with a single-layer neural network.

[View the tutorial](http://deeplearning4j.org/mnist-for-beginners.html)<br>
[Just show me the code](https://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/feedforward/mnist/MLPMnistSingleLayerExample.java)

### MNIST for Experts

By applying a more complex algorithm, Lenet, to MNIST, you can achieve 99 percent accuracy. Lenet is a deep convolutional network.

[Just show me the code](https://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/convolution/LenetMnistExample.java)

### Word2Vec Tutorial

Word2vec is a popular natural-language processing algorithm capable of creating neural word embeddings, which in turn can be fed into deeper neural networks. 

[View the tutorial](./word2vec)<br>
[Just show me the code](https://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/nlp/word2vec/Word2VecRawTextExample.java)

### Linear Classifier Tutorial

This tutorial shows you how a multilayer perceptron can be used as a linear classifier. 

[Just show me the code](https://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/feedforward/classification/MLPClassifierLinear.java)

Video lecture by instructor Tom Hanlon on Machine Learning. Tom provides an overview of how to build a simple neural net in this introductory tutorial. This screencast shows how to build a Linear Classifier using Deeplearning4j.

<iframe width="560" height="315" src="https://www.youtube.com/embed/BN_g2t0ykxg" frameborder="0" allowfullscreen></iframe>

### XOR Tutorial

XOR is a digital logic gate that implements an exclusive or. XOR means that a true output, or an output of 1, results if one, and only one, of the inputs to the gate is true.

[Just show me the code](https://github.com/deeplearning4j/dl4j-examples/blob/master/dl4j-examples/src/main/java/org/deeplearning4j/examples/feedforward/xor/XorExample.java)

### DataVec + Spark Tutorial

This tutorial shows how to use Skymind's DataVec to ingest Comma Separated Values from a text file, convert the fields to numeric using a DataVec Transform Process in Spark, and save the modified data. Transforming non-numeric data to numeric data is a key preliminary step to using a Neural Network to analyze the data.

<iframe width="560" height="315" src="https://www.youtube.com/embed/L5DtC8_4F-c" frameborder="0" allowfullscreen></iframe>

### Beginners Guide to Recurrent Networks and LSTM's

Recurrent nets are a type of artificial neural network designed to recognize patterns in sequences of data, such as text, genomes, handwriting, the spoken word, or numerical times series data emanating from sensors, stock markets and government agencies.

Long Short-Term Memory Units provide a mechanism to allow a nueral net to learn from experience to classify, process and predict time series events.

[View the tutorial](https://deeplearning4j.org/lstm.html)

### Using Recurrent Networks in DL4J

A more in depth discussion of RNN's including configuring your code to use RNN's in DL4J

[View the tutorial](http://deeplearning4j.org/usingrnns)


### <a name="beginner">Other Deeplearning4j Tutorials</a>

* [Introduction to Neural Networks](./neuralnet-overview)
* [Restricted Boltzmann Machines](./restrictedboltzmannmachine)
* [Eigenvectors, Covariance, PCA and Entropy](./eigenvector)
* [LSTMs and Recurrent Networks](./lstm)
* [Neural Networks and Regression](./linear-regression)
* [Convolutional Networks](./convolutionalnets)
* [Neural Word Embeddings, Word2vec and Doc2vec](./word2vec)
