---
layout: page
title: Cognitive Science
mathjax: true
permalink: /cogsci/ctm/
---

---

<style> blockquote{ margin: 1.3em 1.9em; border-left-style: solid; border-left-width: medium; border-left-color: gray; padding: 0.1em 1em; text-align: justify; font-size: 16px; color: darkslategray; } </style>

## The Computational Theory of Mind, Connectionism, and AI

Given that the focus of this part of the blog will be the relationship between AI, cognitive science, and various research questions, we should begin by discussing a main theory of cognitive science -- what is known as the **computational theory of mind** -- and in particular, work our way to the theory which undergirds machine learning and artificial intelligence, known as **connectionism**.

This approach to studying the brain, cognition and behavior emerged in the 1950s, after the explosion of progress in computer science. Alan Turing was a main proponent of the theory, devising his Turing test for artificial intelligence. In addition, the decline of behaviorism and mind-body identity theory (both of which came under significant philosophical objections and theoretical criticisms) brought about functionalism, proposed by Hilary Putnam, which was an approach to studying the mind by studying its functions.<sup><a href="#footnote1">[1]</a></sup>

### Turing Machines and Functionalism

Functionalism is based around the idea of "multiple realizability", in that the same function, once clearly defined, can be instantiated by any number of different things. The original Turing machine, for example, could be realized by any type of machine as long as it is able to carry out the intended function (symbol manipulation). Nowadays, a Turing machine could be implemented fully digitally. The upshot is that function is emphasized, and not material composition. 

That is, things like "thinking" or "visual recognition" should not merely be identified with particular biological events like nerves firing, but rather by their function. Visual recogition, for example, takes in particular input data, 'processes' it, and by comparing it with existing memories, is able to recognize certain shared elements. Under this definition, such behavior can be multiply realized -- you don't have to have a retina and visual cortex in order to see; anything that is able to perform these particular actions could be said to be capable of visual recognition, just as anything able to do basic symbol manipulation (regardless of its material form) could be considered a Turing machine. 

As Turing himself wrote:

<blockquote>
"May not machines carry out something which ought to be described as thinking but which is very different from what a man does?"<sup><a href="#footnote2">[2]</a></sup>
</blockquote>
    
Implicit in this is the idea of multiple realizability, that biological structure or even similitarity matters little as long as a common function is accomplished. What are the common elements between what we do when we think, and what a machine could do, that would cause us to describe it as "thinking"? That is the fundamental question.

By moving away from biological restrictions and focusing instead on the functions the mind carried out, an easy analogy could be drawn to a computer, which is instantiable in any sort of machine (from very simple to very complex). 

A Turing machine, as originally devised, is a rather simple input-output program that accomplishes a certain task. For example, "if position #4505 contains 0, obey the next instruction stored in position #6707, otherwise move on to position #7820". Put in pseudocode, it would resemble an if-then statement like so:

```
if position[4505] == 0:
    go to position[6707]
    
else:
    go to position[7820]
```

Turing then compares this to a real-life example of 'instruction following', and this is where we can begin drafting the theory itself:

<blockquote>
<p class="has-text-align-justify">"To take a domestic analogy. Suppose Mother wants Tommy to call at the cobbler's every morning on his way to school to see if her shoes are done; ... she can stick up a notice ... in the hall which he will see when he leaves for school and which tells him to call for the shoes, and also to destroy the notice when he comes back if he has the shoes with him."<sup><a href="#footnote3">[3]</a></sup></p>
</blockquote>

So, again, writing this in pseudocode gets us a set of nested instructions like this:
```
while shoes != done:
    call
    
    if call == true:
        get shoes
        
        if get shoes == true:
            shoes = done
```

Here, Turing remarks, "the reader must accept it as a fact that digital computers can be constructed ... according to the principles we have described, and that they can in fact mimic the actions of a human computer very closely."<sup><a href="#footnote4">[4]</a></sup> Turing's point is that any human behavior can in theory be made into some sort of function, and thus, in theory, a sufficiently complex computer could (and would) be doing tasks that resemble human ones. 

$\longrightarrow$ We don't want to say that functionalism and computationalism are one and the same thing (something the cognitive scientist and philosopher Jerry Fodor expressed concern about), but merely to draw the connections and similarities between the two. Functionalism is a good way to understand how the abstractions of computational processes can be applied to the mind.

### The Computational Theory of Mind
So, following this, human thought could be seen as a computational process -- one that involved symbol manipulation, just like what a Turing machine would do.

In 1961, Allen Newell and Herbert Simon posited the "General Problem Solver" (GPS). This was an attempt at trying to reproduce the process of "thinking" in computational form. For example, they had a person think out loud as they went about solving a particular logic problem, like reversing a logical expression. 

Say we want to solve a simple math problem: $ 2x = 4$. First, we isolate the variable and then perform the same operation to the other side of the equation -- divide by 2 -- which yields us our answer. 

By doing this, human thinking just <i>is</i> a type of symbol manipulation, which led Newell and Simon to state outright:

<blockquote>
    We can postulate that the processes going on inside the subject’s skin – involving sensory organs, neural tissue, and muscular movements controlled by the neural signals – are also symbol-manipulating processes; that is, patterns in various encodings can be detected, recorded, transmitted, stored, copied, and so on, by the mechanisms of this system.<sup><a href="#footnote5">[5]</a></sup>
</blockquote>

#### Examples 

Let's look at a few very simplified examples to see this sort of theory in action.

One good example of adopting a computational model of the mind, as something that stores and processes information, is George Miller's hypothesis that working memory was around seven items.<sup><a href="#footnote6">[6]</a></sup> For example, suppose you are at the park and want to memorize several things you see, taken as the following set:  $\text{\{cat, dog, apple, sky, tree, fruit, person, car\}}$

The average person will <i>not</i> be able to memorize these in a short-term, working memory way, given that the set contains 8 items. 

<figure>
  <p style="text-align:center;">
    <img src="/images/workingmemory1.png">
    <figcaption align = "center"><b><p style="font-size: 13px;">A basic schema imagining working memory as an array capable of storing seven items. The 'array' can then be used for storage and recall.</p></b></figcaption>
  </p>
</figure>

"sun", the eighth item, has no place in the array, and thus is left out of the working memory, which would corresponod to a failure to remember. 

But if we decrease the size to 6 or 7, a person typically will be able to memorize them in a short-term sense and perhaps transfer the information to elsewhere (this is, incidentally, why authentication confirmation codes are around seven digits).

There are other, similar experiments: in one task, subjects were tested on numerosity judgements by their ability to determine the number of some specific items displayed to them. The participants were able to judge the presence of four items quickly and accurately, while performance dropped rapidly on five items or more.<sup><a href="#footnote7">[7]</a></sup> This also applies to our olfactory judgements, as another experiment reveals a limit in the ability to distinguish different odors (3-4 items). There are more experiments which describe other interesting, discrete limitations on our abilities, and we should wonder why this is the case. As one of the researchers put it, "the results indicated this ... could not be increased by training. Therefore, the limit may be imposed physiologically or by processing constraints."<sup><a href="#footnote8">[8]</a></sup>

One can also draw on the work on 

Another interesting phenomena that lends itself to a computational model of the mind is the concept of single-neuron representation. This is when a single neuron, at least as it appears to researchers, is responsible for the storage and representation of something. For example, a single neuron is responsible for information about a celebrity, or one's grandmother. This plays into an almost naive view of the mind as a computer, where each neuron would be like a file, storing particular information about some particular thing.

### Connectionism and Artificial Neural Networks
The theory states that the brain acts akin to a computer; the brain and neural circuits throughout the body form a type of connective network. Using some type of input-output mechanism, information can be transferred via complex pathways, or can be represented physically somehow, like how a computer stores information in the hard drive. In the case of the brain, this computer would be extremely complex. Each neuron could be defined as some mathematical function, taking in inputs and producing some output.

Frank Rosenblatt, in his seminal paper titled, "The Perceptron: A Probablistic Model for Information Storage and Organization in the Brain", proposed exactly this -- a way to mathematically represent the behavior of a neuron probabilistically, particularly in a way that could be used computationally:

<blockquote>
The theory has been developed for a hypothetical nervous system, or machine, called a <i>perceptron</i>. The perceptron is designed to illustrate some of the fundamental properties of intelligent systems in general, without becoming too deeply enmeshed in the special, and frequently unknown, conditions which hold for particular biological organisms. The analogy between the perceptron and biological systems should be readily apparent to the reader.<sup><a href="#footnote9">[9]</a></sup>
</blockquote>

In other words, one can represent some of the functions done by the "brain", but in a general way that need not worry about the specifics of particular biological structures, some of which might not even be known (as is the case now, and certainly was the case when Rosenblatt published the paper). However, as he notes, these similarities are enough that a person will be able to recognize them.

<figure>
  <p style="text-align:center;">
    <img src="/images/bnn-ann.png">
    <figcaption align = "center"><b><p style="font-size: 13px;">A comparison between a biological neuron and neural connection with an artificial neural network. The image attempts to draw an analogy between the biological neuron and the computational unit. A) represents a neuron, B) represents the computational version, C) represents two connected biological neurons, and D) represents an artificial neural network. From Zhengzu et al, 2020.<sup><a href="#footnote10">[10]</a></sup></p></b></figcaption>
  </p>
</figure>

The number of neurons in the brain is upwards of x million, and in theory, this could be modeled precisely by a complex, connected network of computational units.

<figure>
  <p style="text-align:center;">
    <img src="/images/connect2.png">
    <figcaption align = "center"><b><p style="font-size: 13px;">A fully-connected neural network can support an unlimited number of inputs, hidden layers, and outputs, each layer connected to the previous one.</p></b></figcaption>
  </p>
</figure>

Such a **connectionist** theory undergirds the current-day deep learning approach to intelligent systems. The idea is to mimic a very closely connected network of neurons in order to produce highly complex input-output systems. In this case, simulating the functions and behavior of the brain would merely be a matter of scale and computational power, and in theory, any function of the brain could be computationally recreated. The output of such systems is probabilistic, but serve as a universal functional approximator and are thus, in-principle, capable of fitting to any problem.

<figure>
  <p style="text-align:center;">
    <img src="/images/visualmechanism.png">
    <figcaption align = "center"><b><p style="font-size: 13px;">Paul Churchland imagines the visual system to be a highly complex neural network. From <i> The Engine of Reason</i>[5]</p></b></figcaption>
  </p>
</figure>

<p style="text-align:center">—————</p>

### Other Computational Models of Behavior
There are still, of course, other computational algorithms and models which take different theories as their core assumption. 

One significant example is reinforcement learning, which adopts an essentially classical behaviorist approach. In particular, it draws on the concept of operant conditioning, described by the influential psychologist B.F Skinner in his 1938 book _The Behavior of Organisms_. 

In this model, behavior was thought to occur as a result of repeated interactions between an organism and its environment, in which the organism adapts its behavior as a result of consequences. Operant conditioning uses behavior-reinforcing (reward) or behavior-suppressing (punishment) in order to optimize a particular behavior. Behavior, then, under Skinner's theory, can be seen as an optimization achieved by maximizing reward and minimizing punishment for some particular task.

<figure>
  <p style="text-align:center;">
    <img src="/images/rl.png">
    <figcaption align = "center"><b><p style="font-size: 13px;">Reinforcement learning involves an interaction between the agent and its environment, with a reward function adjusting the agent's actions based on environmental 'feedback'.</p></b></figcaption>
  </p>
</figure>

Reinforcement learning follows the basic idea and formalizes this process into an algorithm. An agent in some state $s$ performs an action $a$ -- often starting with random actions -- either to receive some reward or some punishment $R$, until the behavior of the agent (over many, many training sets) is optimized (measured by some value $V$) for the particular task in the given environment. For any action in a given state:

$$ V = R(s, a) $$

<p style="text-align:center">—————</p>



---

#### References:

<p class="has-text-align-justify" style="font-size:16px">
  <ol style="font-size:16px">
      <li> See Robert M. Harnish, <i>Minds, Brains, Computers: A Historical Introduction to the Foundations of Cognitive Science</i> (Wiley-Blackwell, 2000), pg. 185-186.</li>
      <li> Alan Turing, "Computing Machinery and Intelligence", <i>Mind</i>, Vol. 59, No. 236 (Oct., 1950) pg. 435</li>
      <li> Alan Turing, "Computing Machinery and Intelligence", pg. 438</li>
      <li> George Miller, "The Magical Number Seven, Plus or Minus Two: Some Limits on our Capacity for Processing Information" (1956), <i>Philosophical Review</i>, 63, pg. 81-97. </li>
      <li> Atkinson, et. al, "The magic number 4 ± 0: A new look at visual numerosity judgements" (1976), <i>Perception</i>, 5(3), 327–334.</i>
      <li> Livermore, et. al. "Influence of training and experience on the perception of multicomponent odor mixtures" (1996), <i>Journal of Experimental Psychology: Human Perception and Performance</i>, 22(2), 267–277; see also, Simons, et. al, "What is magic about the magical number four?" (1982), <i>Psychol. Res</i> 44, 283–294.</li>
      <li> Frank Rosenblatt, "The perceptron: A probabilistic model for information storage and organization in the brain.", <i>Psychological Review</i>, 65(6) (1958) pg. 387</li>
      <li> Zhenzhu Meng, Hu Yating, and Christophe Ancey, "Using a Data Driven Approach to Predict Waves Generated by Gravity Driven Mass Flows" (2020), Water 12, no. 2: 600.</li>
      <li> Paul Churchland, <i>The Engine of Reason, The Seat of the Soul</i> (MIT Press, 1995), pg. 10</li>
    

