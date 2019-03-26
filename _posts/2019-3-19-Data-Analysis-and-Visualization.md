---
layout: post
mathjax: true
title: Data Analysis and Visualization - Python
---
### Introduction
This post is based off a dataset I was working with recently as a side project. I wanted to put some of Python's
libraries to use, like matplotlib, seaborn, keras and pandas. My goal was to identify some correlations
in the data through visualization techniques, and design a multi-layer perceptron that could leverage these correlations in order
to make accurate predictions on previously unseen parts of the dataset.

So, this is my (novice) experimentation with visualizing, analyzing and predicting the dataset.

### The Dataset
The dataset is a collection of ~80,000 rows (split into roughly 60,000 training and 20,000 test) of information about how 
people spend their time per week. It highlights certain activities like hours spent sleeping, watching TV, caring for children,
etc. and lastly has a column indicating whether they are employed, unemployed, or not in the labor force.

So, I want to look for correlations between a person's employment status and the time they spend doing various activites throughout the week.

Here are the first few lines of the data, to give you an idea:
```python
  print(df.head())
```
```
   Id Education Level  Age Age Range  Gender  Children  Weekly Earnings  Year  \
0   1     High School   51     50-59  Female         0                0  2005   
1   2        Bachelor   42     40-49  Female         2             1480  2005   
2   3          Master   47     40-49    Male         0              904  2005   
3   4    Some College   21     20-29  Female         0              320  2005   
4   5     High School   49     40-49  Female         0                0  2005   

   Weekly Hours Worked  Sleeping         ...          Job Searching  Shopping  \
0                    0       825         ...                      0         0   
1                   40       500         ...                      0       120   
2                   40       480         ...                      0        15   
3                   40       705         ...                      0       105   
4                    0       470         ...                      0         0   

   Eating and Drinking  Socializing & Relaxing  Television  Golfing  Running  \
0                   40                     180         120        0        0   
1                   40                      15          15        0        0   
2                   85                     214         199        0        0   
3                   30                     240         240        0        0   
4                   35                     600          40        0        0   

   Volunteering      Total   Employment Status  
0             0  24.000000          Unemployed  
1             0  21.583333            Employed  
2             0  17.733333            Employed  
3             0  26.833333            Employed  
4             0  23.750000  Not in labor force  

[5 rows x 25 columns]
  
```
The first thing I decided to do to clean up the data a little bit was to change all non-integer values into integers. Meaning, anywhere there was not a real number - for example, in "Education Level", "Age Range", and "Employment Status" - I changed it to a number. 

This process does take some thinking, however. The numbers that I replace the words matter, so I have to be sure to assign them the right value accordingly. First, I changed "Education Level" into a number from 1-10:
```python
#Replace education level with a number
df = df.replace("9th grade", 1)
df = df.replace("10th grade", 2)
df = df.replace("11th grade", 3)
df = df.replace("12th grade", 4)
df = df.replace("High School", 5)
df = df.replace("Associate Degree", 6)
df = df.replace("Some College", 7)
df = df.replace("Bachelor", 8)
df = df.replace("Master", 9)
df = df.replace("Doctoral Degree", 10)
df = df.replace("Prof. Degree", 10)
```
I assigned a value based on how much education they had achieved, increasing it by 1 for each level up until doctoral degree/prof. degree, which are arguably both the terminal level of education.

A similar process was used for "Age Range":
```python
#Replace age range
df = df.replace("0-19", 1)
df = df.replace("20-29", 2)
df = df.replace("30-39", 3)
df = df.replace("40-49", 4)
df = df.replace("50-59", 5)
df = df.replace("60-69", 6)
df = df.replace("70-79", 7)
df = df.replace("80+", 8)
```
For "Gender" and "Education Status", however, the process was a bit different. Being male or female does not mean one has a higher value, nor does unemployment/employment/not being in the labor force. So, I had to use a process called **one-hot encoding** to transform the data.

One-hot encoding is a simple process commonly used in machine learning which allows for us to change a list of classifications or results into binary options. For "Employment Status", the table looked like this:

|**Employment Status**|
|-------------------|
|Unemployed         |
|Employed           |
|Employed           |
|Not in labor force |

If we change it simply into numbers like we did above, for example reassign values from 1-3:

|**Employment Status**|
|---|
|1  |
|2   |
|2   |
|3 |

It will seem like employed has a higher value than unemployed, and not in labor force has a higher value than being employed. However, they are not better or worse than the others, they are just different classification labels. So, we use one-hot encoding to create binary options like this:

<style>
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 30%;
}

td, th {
  border: 1px solid #dddddd;
  font-size: 12pt;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #dddddd;
}
</style>
<table>
  <tr>
    <th><strong>Unemployed</strong></th>
    <th><strong>Employed</strong></th>
    <th><strong>Not in labor force</strong></th>
  </tr>
  <tr>
    <td>1</td>
    <td>0</td>
    <td>0</td>
  </tr>
  <tr>
    <td>0</td>
    <td>1</td>
    <td>0</td>
  </tr>
  <tr>
    <td>0</td>
    <td>1</td>
    <td>0</td>
  </tr>
  <tr>
    <td>0</td>
    <td>0</td>
    <td>1</td>
  </tr>
</table>

This way, when the data is fed into a machine learning algorithm, it will be able to learn that these are labels/results that every person is grouped into, not characteristics with specific values assigned to them.

### Visualizing the Data
Now that the data has been cleaned up a bit, I find it useful to start visualizing the data to see how certain features correlate. This can give us some insight and intuition on how we should build our ML algorithm.

I used the correlation function built into ```pandas``` in order to create a chart. This shows us generally where we should draw our attention, depending on the strength of correlation between different features:

![correlation heatmap](/images/Graphs/correlation.png "Correlation heatmap")

I won't break down the whole thing, but here are some pertinent conclusions we can draw from the data:

  - there are the expected correlations, like weekly hours worked/weekly earnings being highly correlated with each other, and with employment
  
  - there are also the expected negative correlations, like socializing and relaxing having an inverse relationship with weekly hours worked
  
  - there are also ones I would consider useless, as they barely correlate with anything - for example, "Golfing" and "Shopping". These can likely be tossed out of the dataset in order to decrease the noise.

I also wanted to create some additional heatmaps that would help us to visualize the data. Since the correlation heatmap only describes a general sort of correlation, it is useful to see it up close, especially for correlations that are on the weaker side (closer to 0).

Here are a few heatmaps I made using seaborn, which is a library that can create some beautiful visualizations:

![relax-income heatmap](/images/Graphs/Relax-Income.png "Relax-Income Heatmap")

![relax-age heatmap](/images/Graphs/relax-age.png "Relax-Age Heatmap")
