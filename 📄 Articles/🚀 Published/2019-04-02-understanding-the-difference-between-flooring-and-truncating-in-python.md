---
title: Understanding the Difference Between Flooring and Truncating in Python
slug: understanding-the-difference-between-flooring-and-truncating-in-python
date_published: 2019-04-02T11:37:00.000Z
date_updated: 2021-02-22T17:18:35.000Z
tags: Python
excerpt: Python has two methods for removing fractions from floats and the difference between them is very subtle.
---

Reducing a float (a number with a decimal) to an int (a whole number) is a pretty common task in programming. In Python, you can achieve this by flooring or truncating the number with the `floor` and `trunc` methods, respectively.

Both methods are part of the `math` module and perform a similar function. But there is a subtle difference between the two: `floor` will round down to the nearest whole number, while `trunc` rounds towards 0.

## Intro to Flooring

The `floor` method will round a number down to the nearest whole number. This is useful in cases where you receive a non-whole number and, for what ever reason, don't want the fraction:

    import math
    
    
    math.floor(2.6) # 2
    math.floor(3.2) # 3
    math.floor(9.7) # 9

The key point here is that `floor` will always round *down*, as opposed to true rounding. In true rounding, we would expect the first and last examples in the snippet above to be 3 and 10, because the decimal is above 0.5.

## Intro to Truncating

What about `trunc`, then? Truncating a number, removes the decimal in the direction of 0. We can see how `trunc` behaves by looking at a similar set of examples:

    import math
    
    
    math.trunc(2.6) # 2
    math.trunc(3.2) # 3
    math.trunc(9.7) # 9

From these examples, we can see that `trunc`, like `floor`, is not rounding. If it were, the first and last examples would again be 3 and 10, respectively, but we get 2 and 9.

However, we're getting the same result using `trunc` as we did using `floor`. So, how are they different? Well, the `trunc` method is removing the decimal *towards 0*. In these examples, that does not give us a different result. But there are cases where it will.

## Seeing The Difference

From the examples so far, it would be impossible to tell that `floor` and `trunc` have different behavior so let's look at another example:

    import math
    
    math.floor(-2.6) # -3
    math.trunc(-2.6) # -2

Flooring a number will always round it *down*, while truncating will always round it *towards 0*. So when we floor -2.6, we get -3; when we truncate -2.6, we get -2.

When we truncate a negative number, we effectively round that number up. That's what I mean by "rounding towards 0"!

## Conclusion

The difference between the two is very subtle -- so much so that you can't really tell the difference from the first two examples. This is one of those small differences that you can always look up. And you may have to look it up when the subtle difference in behavior causes a bug!
