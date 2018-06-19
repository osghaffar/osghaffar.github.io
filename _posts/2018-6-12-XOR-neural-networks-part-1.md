---
layout: post
mathjax: true
title: XOR - Introduction to Neural Networks, Part 1
---
### The basics of neural networks
Traditionally, programs need to be hard coded with whatever you want it to do. If they are programmed using extensive techniques and painstakingly adjusted, they may be able to cover for a majority of situations, or at least enough to complete the necessary tasks. However, ***neural networks*** are a type of algorithm that's capable of learning. Well, kinda. Let me explain..

Neural networks are a type of program that are based on, very loosely, a human neuron. All you really need to know about a neuron, without turning this into a bio lesson, is that there is an <u>input area</u>, a processing area in that carries information connecting the output of one neuron to the input of another - known as <u>synapses</u> - and an <u>output</u> area. These branch off and connect with many other neurons, passing information from the brain and back. Millions of these neural connections exist throughout our bodies, collectively referred to as ***neural networks***.


![neuron gif](images/neuron.gif "Neuron - Via GIPHY")


Now that we've looked at real neural networks, we can start discussing ***artificial neural networks***. Like the biological kind, an artificial neural network has <u>inputs</u>, a <u>processing area</u> that transmits information, and <u>outputs</u>. However, these are much simpler, in both design and in function, and nowhere near as powerful as the real kind.

Here is a diagram of a basic artificial neuron:

![basic neuron](images/basicNN.png "Basic Neuron")

This is an example of a simple 3-input, 1-output neural network. As we talked about, each of the neurons has an input, $i_n$, a connection to the next neuron layer, called a ***synapse***, which carries a weight $w_n$, and an output layer. In this case, there is only one output.

We start with random synaptic weights, which almost always leads to incorrect outputs. These weights will need to be adjusted, a process I prefer to call "learning".

The basic idea is to take the input, multiply it by the synaptic weight, and check if the output is correct. If it is not, adjust the weight, multiply it by the input again, check the output and repeat, until we have reached an ideal synaptic weight.

### What is XOR?
-------------------------------
An XOR gate is a kind of logic gate. It takes in two inputs, both a $0$ or $1$ (i.e. it has so-called ***boolean*** inputs), and outputs a single $0$ or $1$ according to the following table:

|Input 1|Input 2||Output|
|:--------:|:--------:||:-----:|
| 0        | 0        || 0|
| 0        | 1        || 1 |
| 1        | 0        || 1 |
| 1        | 1        || 0 |

$0$ can be thought of as representing "OFF" or "FALSE", while $1$ is "ON" or "TRUE".

### Getting into the details
--------------------------------------
Let's look at it more closely.

Remember how I said the main idea is that you want to multiply the inputs by the right numbers to get the output?

We'll give our inputs, which is either 0 or 1, and they both will be multiplied by the synaptic weight. We'll adjust it until we get an accurate output each time, and we're confident the neural network has learned the pattern.

To write this out in mathematical terms, it is the sum of all the inputs multiplied by their synaptic weights. Here's the equation (where $o$ is the output):

$$o=(i_1 \cdot w_1) + (i_2 \cdot w_2) + (i_3 \cdot w_3) + \cdots $$

or equivalently:

$$o=\sum_n i_n \cdot w_n$$

Let's get back to our example. We already have our inputs and outputs, which we will train the neural network on, so let's plug it into our neural network. We'll use the diagram above. For the first data set, this is what it should look like:

<img src="/images/inputNN.png" alt="Network with inputs and output">

Now we just follow the equation. That is:

$$\sum_n i_n \cdot w_n = (0 \cdot w_1) + (0 \cdot w_2) = 0$$

Our neural network needs to find the correct synaptic weights which will allow it to make the right prediction. We'll train it in this same way with all of the data:

$$\sum_n i_n \cdot w_n = (0 \cdot w_1) + (1 \cdot w_2) = 1$$

$$\sum_n i_n \cdot w_n = (1 \cdot w_1) + (0 \cdot w_2) = 1$$

$$\sum_n i_n \cdot w_n = (1 \cdot w_1) + (1 \cdot w_2) = 0$$

Let's start laying out our steps thus far:

<pre style="font-family: times, serif; font-size:11pt; text-align: left; line-height: 1.5;">
                <strong>1:</strong> Obtain a dataset with <i>i<sub>x</sub></i> inputs and <i>o<sub>y</sub></i> outputs 
                          - the neural network will have this same number of inputs and outputs.
                <strong>2:</strong> Plug your input vectors into your neural network (in this example the inputs are [0, 0], [0, 1], [1, 0], [1, 1]).
                <strong>3:</strong> Train the network to find the correct synaptic weights.
</pre>

We'll keep adding to our list of steps as we go.o.
