---
layout: post
mathjax: true
title: Algorithmic Trading - Ichimoku
---
### Introduction
When trading the financial markets, traders will want to use any and all tools they can to pick out important information from the vast amounts of noisy data. Many technical indicators are used in the financial markets as a way to detect profitable trade signals, as well as entries and exits. 

Examples of these indicators range from the widely known moving averages to the lesser known, more estoric ones like Fibonnaci retracements and Gann time cycles. 

No technical indicator is the holy grail, but Ichimoku - full name Ichimoku Kinko Hyo - is pretty good by itself.

In this post, we will explore the Ichimoku indicator, its components, and we will write and code a trading algorithm that uses Ichimoku signals to trade.

### Ichimoku Kinko Hyo
Ichimoku Kinko Hyo (roughly meaning _"one glance equilibrium chart"_ in Japanese) is a technical indicator that was invented in Japan in the 1930s. It was developed by a man named Goichi Hosoda who was, interestingly, a journalist. This indicator allegedly took him 30 years to develop, and was released to the public sometime during the 1960s. 

Here's a picture of an Ichimoku indicator running on EUR/USD.

![chart with indicator](/images/ichi-chart.png "Chart with indicator")

At first glance, this indicator seems ridiculously messy and unnecessarily complicated, like a math textbook. Once you get used to looking at it though, it gets much simpler and more intuitive. There are several moving parts, but one could argue that its relative complexity makes it more successful than something like simple moving averages, for example.

Let's break down this indicator part by part. Ichimoku Kinko Hyo has 6 components:

- **Tenkan-sen**: Also known as the _conversion line_, this is calculated by adding the maximum price of the last 9 periods to the minimum price of the last 9 periods, and dividing this value by 2. In the picture above, Tenkan-sen is the red line. In terms of moving averages, this can be thought of as a short-term, faster moving line.

- **Kijun-sen**: Also known as the _base line_, this is calculated by adding the maximum price of the last 26 periods to the minimum price of the last 9 periods, and dividing this value by 2. In the picture above, Kijun-sen is the blue line. This can be thought of as a slower, long-term version of Tenkan-sen.

- **Chiko span**: Also known as the _lagging line_, this is simply the prices plotted 26 periods behind the actual price. So, on a daily chart, the price for November 26 would be shown on the chart at November 1. In the picture above, the Chiko span is the green line. This one is slightly more confusing to look at, but it gets easier once you start matching up where the indicator is lagging behind.

- **Senkou span A**: This is the orange-ish line you see on the chart. This is calculated by adding the Tenkan-sen and Kijun sen, and dividing by 2. The line is plotted 26 periods ahead, the opposite direction that the Chiko span is plotted.

- **Senkou span B**: This is the tan line you see on the chart. This is calculated by adding the highest high of the last 52 periods and the lowest low of the last 52 periods, and dividing by 2. Like Senkou span A, it is also plotted 26 periods ahead.

- Together, Senkou span A and B make a cloud shaped area that is filled in. This area is known as **Kumo**. Kumo serves as indicators of support and resistance.

Also, the numbers 9, 26, and 52 are not set in stone. You can change them to whatever you see fit, but I think it's best if we stick with what Goichi Hosoda chose after 30 years of development. There isn't a reason given for these specific numbers, or at least not one I could find; however, I still wouldn't call them arbitrary. The man had to be on to something if he chose those numbers.

### Signals We Can Ascertain
Now that we've understood the parts that make up the Ichimoku indicator, we can start seeing how it can indicate a buy or sell signal.

The core of the Ichimoku indicator is the two main lines, Tenkan-sen and Kijun-sen. The slower movement and reduced reactivity to market movement from Kijun-sen (hence it being named the base line) contrasts with the faster movement and hightened reactivity to the market from Tenkan-sen (conversion line). This difference in behavior is due to the difference in the time period they are calculated on (9 vs 26 periods). These two lines cross over each other when the price shifts up or down.

In addition, the Senkou spans give a good range for how high or low the price will most likely go. Of course, nothing is certain, and definitely not when it comes to the financial markets, but calculations using the last 52 days seem to hold their ground.

Using this information, we can deduce a few signal ideas.

<u>Buy signals</u>:

The Tenkan-sen crossing over the Kijun-sen would indicate price has moved upwards in the short term, signaling to buy.

In addition, if they are above the Kumo (meaning the cross over has happened above the cloud), this would mean the price has crossed a 52 day high and is moving upwards significantly. This would make it a strong buy signal.

<u>Sell signals</u>:

On the other hand, the Tenkan-sen crossing under the Kijun-sen would indicate price has moved downwards in the short term, which is a signal to sell.

Similarly, if this cross over is happening below the Kumo, it would mean price has dropped significantly and it would be a strong sell signal.

There is lots more you can garner by using this indicator, but we won't go too far down that rabbit hole today.

### The Algorithm

For this tutorial, we aren't going to create an overly complex trading bot; rather it will be super simple and use the most basic Ichimoku signals to trade. The idea is to highlight the simplicity but effectiveness of the indicator and to demonstrate that it can be utilized algorithmically.

We will be using the basic cross over of Tenkan-sen and Kijun-sen. When the conversion line crosses above the base line, we'll buy, and when the conversion line crosses below the base line, we will sell. 

To close the trades, we have a few options - either we can set a take profit, meaning once we've made a certain amount of money we close the trade automatically, or we can wait until the conversion line crosses the base line back the opposite way. Although the take profit may be more economically satisfying, choosing a take profit that maximizes our possible profit would take far too long and require a lot of statistical analysis. So, for the sake of brevity and for the sake of demonstrating the indicator, we will simply use the second cross over as our close signal.

So, in short, here's the algorithm put together:

![Algorithm for ichimoku trading](/images/ichimoku.png "Algorithm for ichimoku trading")

### Converting to Code
We'll be using MQL4 to code our trading algorithm. MQL4<sup>[1](#footnote1)</sup> is a language designed for trading, but it is based in C++ and isn't too difficult to use, especially if you are familiar with C++ already. 

Thankfully, there are several built-in functions in MQL4 that will allow us to skip having to type in the conversion and base line equations; however, it is still good to have them handy in case you use a language that doesn't have these built-in.

Here's the main algorithm inside a function:
```c
void start()
{
    int ticket = 0;
    bool buyorder = false, sellorder = false;
    
    int OrderTotal1 = OrderCounter(1111);
    int OrderTotal2 = OrderCounter(2222);
    
    double conversionLine = iIchimoku(NULL, 0, 9, 26, 52, 1, 0);
    double baseLine = iIchimoku(NULL, 0, 9, 26, 52, 2, 0);
    
    if((conversionLine > baseLine) && (OrderTotal1 <= 2)){
        ticket = OrderSend(Symbol(),OP_BUY,LotSize,Ask,3,0,0,NULL,1111,0,Green);
        buyorder = true;
    }
            
    if((baseLine > conversionLine) && (OrderTotal2 <= 2)){
        ticket = OrderSend(Symbol(),OP_SELL,LotSize,Bid,3,0,0,NULL,2222,0,Green);
        sellorder = true;
    }
}

```
The code is relatively straightforward, so we can start breaking it down without too much prelude. 
-------------------------------------------------------------------------------------------------
The first few lines of code are mostly necessary to help smooth the function out:
```c
    int ticket = 0;
    bool buyorder = false, sellorder = false;
    
    int OrderTotal1 = OrderCounter(1111);
    int OrderTotal2 = OrderCounter(2222);
```
The ```int ticket``` simply is a way for MQL4 to keep track of your trades. It will number each subsequent trade you place, e.g. trade #1, trade #2, and so on. 

Our ```buyorder``` and ```sellorder``` booleans are in place as a trigger. Once we have placed an order, we will set these to true and they will be the "gate" to start the process to check for cloing.

The ```OrderTotal``` is part of another function that I'll get to later; in short, it's just a way to keep track of how many trades have been opened.
______________________________________________________________________________________________
Moving on, we have these two lines:
```c
    double conversionLine = iIchimoku(NULL, 0, 9, 26, 52, 1, 0);
    double baseLine = iIchimoku(NULL, 0, 9, 26, 52, 2, 0);
```
Here is where we define our conversion (Tenkan-sen) and base (Kijun-sen) lines. As I said earlier, MQL4 has some nicely built-in functions that take care of the calculations for us. In this case, it is ```iIchimoku```. 

According to the docs<sup>[2](#footnote2)</sup>, the parameters are as follows:
```
   iIchimoku(Symbol, Timeframe, Tenkan-sen, Kijun-sen, Senkou Span B period, Data Source, Time Shift)
```
Using this, we can fill it in with the information we have - we don't want any specific symbol, or currency pair, so we can leave that as NULL. Our timeframe is the current one, so we leave that as 0. Then, we replace the next three values with our 9, 26, and 52 respectively. The data source is which line you want as the return value - the conversion line, base line, or other. For this, we put 1 in the conversion line and 2 for the base line. Finally, we don't want to shift the time at all, so we keep that as 0.
_____________________________________________________________________________________________
This last part of the code is fairly straightforward as well:
```c
    if((conversionLine > baseLine) && (OrderTotal1 <= 2)){
        ticket = OrderSend(Symbol(),OP_BUY,LotSize,Ask,3,0,0,NULL,1111,0,Green);
        buyorder = true;
    }
            
    if(buyorder == true){
        if(baseLine > conversionLine) && (OrderTotal1 >= 1){
            OrderClose(OrderTicket(), OrderLots(), Bid, 3, Green);
        }
    }
            
    if((baseLine > conversionLine) && (OrderTotal2 <= 2)){
        ticket = OrderSend(Symbol(),OP_SELL,LotSize,Bid,3,0,0,NULL,2222,0,Green);
        sellorder = true;
    }
    
    if(sellorder == true){
        if(conversionLine > baseLine) && (OrderTotal1 >= 1){
            OrderClose(OrderTicket(), OrderLots(), Ask, 3, Red);
        }
    }
```
If the conversion line is greater than the baseline, we buy. If the base line is greater, we sell. The order total keeps track of how many trades we have already opened, to prevent us from opening an unnecessary amount. Additionally, ```buyorder``` and ```sellorder``` become true and allow the close signal to become active once the cross over occurs again.

### Results

#### References
-----------------
<a name="footnote1">1</a>: <a href="https://docs.mql4.com">MQL4 documentation</a>

<a name="footnote2">2</a>: <a href="https://docs.mql4.com/indicators/iichimoku">MQL4 iIchimoku documentation</a>

