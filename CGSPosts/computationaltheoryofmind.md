---
layout: page
title: Cognitive Science
mathjax: true
permalink: /cogsci/ctm/
---

---

<style> blockquote{ margin: 1.3em 1.9em; border-left-style: solid; border-left-width: thick; border-left-color: lightgray; padding: 0.1em 1em; font-size: 16px; color: lightslategray; } </style>

## The Computational Theory of Mind

Given that the focus of this part of the blog will be the relationship between AI, cognitive science, and various research questions, we should begin by discussing the main theory of cognitive science, or at least the one which undergirds machine learning and artificial intelligence -- what is known as the **computational theory of mind**. 

This approach to studying the brain, cognition and behavior emerged in the 1950s, after the explosion of progress in computer science. Alan Turing was a main proponent of the theory, devising his Turing test for artificial intelligence. In addition, the decline of behaviorism and mind-body identity theory (both of which came under significant philosophical objections and theoretical criticisms) brought about functionalism, proposed by Hilary Putnam, which was an approach to studying the mind by studying its functions. 

Putnam defined functionalism, or as he originally called it, the 'functional state hypothesis' based on a few principles:

That is, things like "thinking" or "visual recognition" should not be identified merely with particular biological events like nerves firing, but by their function. Visual recogition, for example, takes in particular input data, 'processes' it with existing memories, and is able to recognize certain elements. In this definition, such a behavior can be multiply realized -- you don't have to have a retina and visual cortex in order to see, anything able to do these actions could be said to be capable of visual recognition.

$$\text{\small{Mind-Body Identity Theory: Identifying visual recognition with some neural activity in the visual cortex}} $$
$$ \Big\downarrow $$
$$ \text{\small{Functionalism: Visual recognition is processing some input by comparing it to previously seen data}} $$ 

By moving away from biological restrictions and focusing instead on the functions the mind carried out, an easy analogy could be drawn to a computer, which is instantiable in any sort of machine (from very simple to very complex). The theory states that the brain acts akin to a computer; the brain and neural circuits throughout the body form a type of connective network. Using some type of input-output mechanism, information can be transferred via complex pathways, or can be represented physically somehow, like how a computer stores information in the hard drive. In the case of the brain, this computer would be extremely complex. Each neuron could be defined as some mathematical function, taking in inputs and producing some output.

<figure>
  <p style="text-align:center;">
    <img src="/images/bnn-ann.png">
    <figcaption align = "center"><b><p style="font-size: 14px;">A comparison between a biological neuron and neural connection with an artificial neural network. The image attempts to draw an analogy between the biological neuron and the computational unit. A) represents a neuron, B) represents the computational version, C) represents two connected biological neurons, and D) represents an artificial neural network. From Zhengzu et al, 2020. [2]</p></b></figcaption>
  </p>
</figure>

The number of neurons in the brain is upwards of x million, and in theory, this could be modeled precisely by a complex, connected network of computational units.

<figure>
  <p style="text-align:center;">
    <img src="/images/connect2.png">
    <figcaption align = "center"><b><p style="font-size: 14px;">A fully-connected neural network can support an unlimited number of inputs, hidden layers, and outputs, each layer connected to the previous one.</p></b></figcaption>
  </p>
</figure>

Such a **connectionist** theory undergirds the current-day deep learning approach to intelligent systems. The idea is to mimic a very closely connected network of neurons in order to produce high level input-output systems. In this case, simulating the functions and behavior of the brain would merely be a matter of scalea nd computational power, and in theory, any function of the brain could be computationally recreated. The output of such systems is probabilistic, but ultimately serve as a universal functional approximator and are thus, in-principle, capable of fitting to any problem.

<figure>
  <p style="text-align:center;">
    <img src="/images/visualmechanism.png">
    <figcaption align = "center"><b><p style="font-size: 14px;">Paul Churchland imagines the visual system to be a highly complex neural network. From <i> The Engine of Reason </i></p></b></figcaption>
  </p>
</figure>

<p style="text-align:center">—————</p>

$\longrightarrow$ There are still, of course, other computational algorithms and models which take different theories as their core assumption. 

One significant example is reinforcement learning, which adopts an essentially classical behaviorist approach. In particular, it draws on the concept of operant conditioning, described by the influential psychologist B.F Skinner in his 1938 book _The Behavior of Organisms_. 

In this model, behavior was thought to occur as a result of repeated interactions between an organism and its environment, in which the organism adapts its behavior as a result of consequences. Operant conditioning uses behavior-reinforcing (reward) or behavior-suppressing (punishment) in order to optimize a particular behavior. Behavior, then, under Skinner's theory, can be seen as an optimization achieved by maximizing reward and minimizing punishment for some particular task.

Reinforcement learning follows the basic idea and formalizes this process into an algorithm. An agent in some state $s$ performs an action $a$ -- often starting with random actions -- either to receive some reward or some punishment $R$, until the behavior of the agent (over many, many training sets) is optimized (measured by say, a Q-score) for the particular task in the given environment. 

$$ Q = R(s, a) $$

<p style="text-align:center">—————</p>

One good example of adopting a computational model of the mind, as something that stores and processes information, is George Miller's hypothesis that working memory was around seven items. For example, suppose you are at the park and want to memorize several things you see, taken as the following set:  $\text{\{cat, dog, apple, sky, tree, fruit, person, car\}}$

The average person will not be able to memorize these in a short-term, working memory way, given that the set contains 8 items. 


<figure>
  <p style="text-align:center;">
    <img src="/images/workingmemory1.png">
    <figcaption align = "center"><b><p style="font-size: 14px;">A basic schema imagining working memory as an array capable of storing seven items. The 'array' can then be used for storage and recall.</p></b></figcaption>
  </p>
</figure>

<"sun">, the eighth item, has no place, and thus is left out of the working memory, which corresponds to a failure to remember. 

But if we decrease the size to 6 or 7, a person typically will be able to memorize them in a short-term sense and perhaps transfer the information to elsewhere (this is, incidentally, why authentication confirmation codes are around seven digits).
