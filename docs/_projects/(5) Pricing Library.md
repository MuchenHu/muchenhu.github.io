---
name: Library for Derivatives Pricing
tools: [C++, OOP]
image: https://github.com/MuchenHu/muchenhu.github.io/blob/master/docs/option_pricing.png?raw=true
description: This course project for Financial Engineering at SAIF involved developing a C++ library for derivative pricing. 
---

# Library for Derivatives Pricing

This course project for *Financial Engineering*, advised by [Zhihao Yin](https://en.saif.sjtu.edu.cn/faculty-research/yin-zhihao), involved developing a C++ library for derivative pricing. Algorithms implemented include:

- Yield Curve Bootstrapping Algorithm
- Bermudan Put Option Pricing Algorithm
- European Option Pricing
- Swaption Pricing with Hull-White Trinomial Tree Model
- The Longstaff Schwartz Algorithm
- Monte Carlo Simulation

<!-- Object-oriented analysis and design is all about figuring out what objects are and how they should interact. An object is a collection of data and associated behaviors. The key purpose of modeling an object in object-oriented design is to determine what the *public interface* of that object will be. The interface is the collection of attributes and methods that other objects can access to interact with that object. -->

In the Lib, there are three major packages: Instrument, XPricer and YC.
- **Instrument**: The Instrument package defines the scope or characteristics of a financial instrument. It only provides data containers and built-in functions to display, compare or calculate traits which do not highly rely on other objects or extra inputs (e.g. yield to maturity).
    - Bond
    - Option
- **XPricer**: The XPricer package provides different models and methods for pricing. X stands for different instruments. The scope of `pricing' is relatively small. It does not include model calibration and yield curve bootstrap etc, although these processes are necessary when we want to price an instrument. 
    - TreeModel
    - SwapPricer
    - OptionPricer
    - SwaptionPricer
- **YC**: The YC package provides various functions for yield curve. For now, the existing functions mainly focus on yield curve bootstrap.
    - BondBootstrap
    - HullWhiteBootstrap

## Why Build a Custom Library?

For example, consider the following problem:

Swaption is an option which gives the buyer the right to enter into a swap. In our problem, the swaption is semi-annual for 5 years, and the option can be exercised starting from 0.5 years to 4.5 years. In the underlying swap, the swaption buyer pays the fixed rate and receives the floating rate.

I already know how to price (Bermudan) option in the previous homework. In this case, each node on the pricing tree, regardless of binomial or trinomial type, corresponds to the swap value in this state and time. Therefore, in this case, my focus is to price a swap.

In order to achieve that, the interest rate trees must be constructed. This is where the Hull-White model comes in. To make sure that there are no statistical arbitrage opportunities in Hull-White model, the shift parameter need to be calibrated to minimize the difference between model discount curve and market discount curves.

Swaption pricing follows the same methodology as option pricing once we have the swap value for each node. However, we need to pay attention to the contract terms. For example, for the Bermudan swaption we are required to price, we can only exercise the swaption since t = 0.5. This means for node (0, 0), we can only back propagate the future swaption value and no comparison is involved. Also, the last chance for us to exercise is at t = 4.5. As a result, the back propagation starts from t = 4.5 instead of t = 5. This is why we need an extra package ‘SwaptionPricer’ even though core methods are already built in other packages.

In summary, the Bermudan swaption pricing process is illustrated in the following UML Diagram.

<div class="row">
    {% include elements/figure.html image="https://github.com/MuchenHu/muchenhu.github.io/blob/master/docs/UML.png?raw=true" %}
</div>
Grade: A+