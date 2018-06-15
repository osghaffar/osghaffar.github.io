---
layout: post
title: XOR Introduction to Neural Networks - Part 1
---
### The basics of neural networks
Traditionally, programs need to be hard coded with whatever you want it to do. If they are programmed using extensive techniques and painstakingly adjusted, they may be able to cover for a majority of situations, or at least enough to complete the necessary tasks. However, ***neural networks*** are a type of algorithm that's capable of learning. Well, kinda. Let me explain..

Neural networks are a type of program that are based on, very loosely, a human neuron. All you really need to know about a neuron, without turning this into a bio lesson, is that there is an <u>input area</u>, a processing area in that carries information which connects the output of one neuron to the input of another - known as <u>synapses</u> - and an <u>output</u> area. These branch off and connect with many other neurons, passing information from the brain and back. Millions of these neural connections exist throughout our bodies, collectively referred to as ***neural networks***.

<img src="/images/neuron.gif" alt="Human Neuron Gif"/>


Now that we've discussed real neural networks, we can start looking at ***artificial neural networks***. Like the biological kind, an artificial neural network has <u>inputs</u>, a <u>processing area</u> that transmits information, and <u>outputs</u>. However, these are much simpler, in both design and in function, and nowhere near as powerful as the real kind.


Here is a diagram of a basic artificial neuron:

![alt text](images/basicNN.png "Basic Neuron")
<img src="/images/basicNN.png" alt="Basic Neuron"/>


This is an example of a simple 3-input, 1-output neural network. As we talked about, each of the neurons has an input, $i_n$, a connection to the next neuron layer, called a ***synapse***, which carries a weight $w_n$, and an output layer. In this case, there is only one output.

The easiest way to understand what's taking place is to think of it like this: by multiplying two numbers together, you can theoretically get any number.

The two numbers in this case are the input and the synaptic weight. The number we are trying to get is the output.
Since the starting synaptic weight is random, it is highly likely the network will need to do some adjusting, or as I like to call it, learning, before it reaches the correct output.

The basic idea is to take the input, multiply it by the synaptic weight, and check if the output is correct. If it is not, adjust the weight, multiply it by the input again, check the output and repeat, until we have reached an ideal synaptic weight.


