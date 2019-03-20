---
layout: post
mathjax: true
title: Data Analysis and Visualization - Python
---
### Introduction
This post is based off a dataset I was working with recently as a side project. I wanted to put some of Python's
libraries to use, like ```matplotlib```, ```seaborn```, ```keras``` and ```pandas```. My goal was to identify some correlations
in the data through visualization techniques, and design a multi-layer perceptron that could leverage these correlations in order
to make accurate predictions on previously unseen parts of the dataset.

So, this is my novice experimentation with visualizing, analyzing and predicting the dataset.

### The Dataset
The dataset is a collection of ~80,000 rows (split into roughly 60,000 training and 20,000 test) of information about how 
people spend their time per week. It highlights certain activities like hours spent sleeping, watching TV, caring for children,
etc. and lastly has a column indicating whether they are employed, unemployed, or not in the labor force.

So, the correlations to look for would be activities that are directly related to the person's employment status.

Here are the first few lines of the data, to give you an idea:
```
  print(df.head())
  
  
```
