---
layout: post
mathjax: true
title: XOR - Introduction to Neural Networks, Part 1
---
### The basics of neural networks
Traditionally, programs need to be hard coded with whatever you want it to do. If they are programmed using extensive techniques and painstakingly adjusted, they may be able to cover for a majority of situations, or at least enough to complete the necessary tasks. However, a ***neural network*** is a type of algorithm that is capable of learning. Well, kinda. Let me explain..

Neural networks are a type of program that are based on, very loosely, a human neuron. All you really need to know about a neuron, without turning this into a bio lesson, is that there is an <u>input area</u>, a processing area in that carries information which connects the output of one neuron to the input of another - known as <u>synapses</u> - and an <u>output</u> area. These branch off and connect with many other neurons, passing information from the brain and back to it. Millions of these neural connections exist throughout our bodies, collectively referred to as ***neural networks***.

<center> <img src="/images/neuron.gif" alt="Human Neuron Gif"/> </center>


Now that we've discussed real neural networks, we can start looking at ***artificial neural networks***. Like the biological kind, an artificial neural network has <u>inputs</u>, a <u>processing area</u> that transmits information, and <u>outputs</u>. However, these are much simpler, in both design and in function, and nowhere near as powerful as the real kind.

Here is a diagram of a basic artificial neuron:

<img src="/images/basicNN.png" alt="Basic Neuron"/>

This is an example of a simple 3-input, 1-output neural network. As we talked about, each of the neurons has an input, $i_n$, a connection to the next neuron layer, called a ***synapse***, which carries a weight $w_n$, and an output layer. In this case, there is only one output.

The easiest way to understand what's taking place is to think of it like this: by multiplying two numbers together, you can theoretically get any number.

The two numbers in this case are the input and the synaptic weight. The number we are trying to get is the output.
Since the starting synaptic weight is random, it is highly likely the network will need to do some adjusting, or as I like to call it, learning, before it reaches the correct output.

The basic idea is to take the input, multiply it by the synaptic weight, and check if the output is correct. If it is not, adjust the weight, multiply it by the input again, check the output and repeat, until we have reached an ideal synaptic weight.

### What is XOR?
-------------------------------
An XOR gate is a kind of logic gate. It is a very simple example of a specific combination of inputs causing an output. Here it is below, we won't get into too many details as you really only need to know the way it works.

|Input 1   |Input 2   ||Output|
|:--------:|:--------:||:-----:|
| 0        | 0        || OFF|
| 0        | 1        || ON |
| 1        | 0        || ON |
| 1        | 1        || OFF |

The pattern here is that if both inputs are the same, the output is off, and if both inputs are different, the output is on.

### Getting into the details
--------------------------------------
Let's look at it using some raw numbers.

Remember how I said the main idea is that you want to multiply the inputs by the right numbers to get the output?

We'll give our inputs, which is either 0 or 1, and they both will be multiplied by the synaptic weight. We'll adjust it until we get an accurate output each time, and we're confident the neural network has learned the pattern.

In order to do that, all elements have to be numbers. So we'll assign a number to each output, 0 for off, 1 for on. (This is called ***classification***, or specifically, ***binary classification***, but more on that in another post).

So to write this out in math terms, it's the sum of all the inputs multiplied by their synaptic weights. Here's the equation:

$ o = (i_1 \\cdot w_1) + (i_2 \\cdot w_2) + (i_3 \\cdot w_3) + \\cdots $

Which is, in broader terms:
<center>
o = \\sum_n i_n \\cdot w_n
</center>

The outputs can also be represented as the dot product of the inputs and the synaptic weights:

<center> <img src="/images/messymatrix.png" alt="matrix of inputs x weights"/> </center>

Where $i$ is the first and second input, $w$ are the synaptic weights, and $o$ is the output for those specific inputs.

Don't lose me with the symbols. Let's go back to our problem of XOR so I can explain with an actual example. So, we have our inputs and outputs, which we will train the neural network on. Take a look at the updated XOR:

|Input 1   |Input 2   ||Output|
|:--------:|:--------:||:-----:|
| 0        | 0        || 0  (OFF)|
| 0        | 1        || 1  (ON) |
| 1        | 0        || 1  (ON) |
| 1        | 1        || 0  (OFF) |

Or, depicted in matrix form here:

<center> <img src="/images/matrix.png" alt="matrix of inputs/outputs"/> </center>

So now that we have our data, let's plug it into our neural network. We'll use the diagram above. For the first "ON" data set [0, 1] = [1], this is what it should look like:

<center> <img src="/images/inputNN.png" alt="Network with inputs and output"/> </center>

Our neural network needs to find the correct synaptic weights which will allow it to make the right prediction. We can just follow the equation. That is:

<center> <img src="/images/firstinputequation.png" alt="equation with inputs and weights"/> </center>

We'll train it in this same way with all of the data:

<center> <img src="/images/otherinputequations.png" alt="equations with inputs and weights"/> </center>

Let's start laying out our steps thus far:

<pre style="font-family: times, serif; font-size:11pt; text-align: left; line-height: 1.5;">
                <strong>1:</strong> Obtain a dataset with <i>i</i> inputs and <i>o</i> outputs 
                          - the neural network will have this same number of inputs and outputs.
                <strong>2:</strong> If the outputs or inputs are <i>not</i> in numerical form, replace them with numbers (in this example we used 0 and 1).
                <strong>3:</strong> Plug your input vectors into your neural network (in this example the inputs are [0, 0], [0, 1], [1, 0], [1, 1]).
                <strong>4:</strong> Train the network to find the correct synaptic weights.
</pre>

We'll keep adding to our list of steps as we go.
