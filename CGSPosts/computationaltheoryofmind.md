---
layout: page
title: Cognitive Science
mathjax: true
permalink: /cogsci/ctm/
---

---

<style> blockquote{ margin: 1.3em 1.9em; border-left-style: solid; border-left-width: thick; border-left-color: lightgray; padding: 0.1em 1em; font-size: 16px; color: lightslategray; } </style>

## The Computational Theory of Mind

We should begin by discussing the main theory of cognitive science -- what is known as the **computational theory of mind**. Following after behaviorism and other schools of thought, this model of cognition took off after the explosion of progress in computer science. Alan Turing was a main proponent

The theory states that the brain acts akin to a computer; the brain and neural circuits throughout the body form a type of connective network. Using some type of input-output mechanism, information can be transferred via complex pathways, or can be represented physically somehow, like a program on a computer stores information. 

<p style="text-align:center">—————</p>

--- There are still, of course, other computational algorithms and models which take different theories as their core assumption. One significant example is reinforcement learning, which adopts an essentially classical behaviorist approach. In particular, it draws on the concept of operant conditioning, described by the influential psychologist B.F Skinner in his 1938 book _The Behaviour of Organisms_. In this model, behavior was thought to occur as a result of repeated interactions between an organism and its environment, in which the organism adapts its behavior as a result of consequences. Operant conditioning uses behavior-reinforcing (reward) or behavior-suppressing (punishment) in order to optimize a particular behavior. Behavior, then, under Skinner's theory, can be seen as an optimization achieved by maximizing reward and minimizing punishment in some particular task.

Reinforcement learning follows the basic idea and formalizes this process into an algorithm. An agent in some state $s$ performs an action $a$ -- often starting with random actions -- either to receive some reward or some punishment $R$, until the behavior of the agent (over many, many training sets) is optimized (measured by say, a Q-score) for the particular task in the given environment. 

$$ Q = R(s, a) $$

<p style="text-align:center">—————</p>

One good example of adopting a computational model of the mind, as something that stores and processes information, is George Miller's hypothesis that working memory was around seven items. For example, if we take the set 

$$ \text{\{cat, dog, apple, sky, tree, fruit, person, car\}} $$

the average person will not be able to memorize these in a short-term sort of way. But if we decrease the size to 6 or 7, a person typically will be able to memorize them in a short-term sense and perhaps transfer the information to paper or elsewhere (this is, incidentally, why authentication confirmation codes are around seven digits).
