# Numerical Operations – Dynamic Division


> This is the extension of the previous chapter and they might contains advance concepts; if you feel overwhelmed, please move on to other chapters first and goes back to this chapter once you are ready.

## Overview

Due to the re-discovery of the properties in [waveshaper lookup tables](https://logickin.net/logicprocessing/waveshaper-in-lq-mode-redifines-sunvox-programming/), quite a few mathematical operations, considered as impossible, have been brought into the reality. Let we show you the first problem:

Division has been my headache since I was messing around logic stuff in SunVox, as most of the division methods require a dynamic number of iterations. This is not really an issue in computers because they have ultra high clock speed and low feedback latency, making the process time being unnoticeable; nevertheless, this is not applied in SunVox owing to its rather long 20ms feedback delay and its limited sample frequencies (44100, 48000 or 96000 in most cases). As a result, division will take ages to complete.

Take 8455 / 2 as an example; if we loop for every iterations, we ended up increasing an accumulator by 4228 times, which it takes (4228 * 20) / 1000 = 84.56s. Roughly a minute to complete a single division is horrific because not only we ended up with wasting all the time to do a simple task, but also making the machine hard to predict the run time. Thus, we must find something better.

## Multiplied Divisor

Let’s look at the first non-iterative method. Considering that we only need to divide a single bit, we only need to know a few things:

1. Is dividend (Numerator) large enough for cancelling the divisor (denominator)?
2. If so, how to represent the answer?
3. How to handle for the remaining values?

As you can see, since we need to compare number between dividend and divisor, negative detector is needed, and because negative detectors only switch on when dividend is smaller than the divisor, we must apply an NOT gate for the answer. We must sort out the remainder as well, so we must return the subtracted result during comparing the the two inputs; hence, we have the following:

![single stage of multiplied divider](../images/numerical_operations/8-bit-divider-single-stage.png)

But... why is this have a x2 for the divisor side? This is the middle stage of the division logic, which the divisor is multiplied by two for each stage, except for the first stage. Thus, the divisor is grown exponentially by passing every stage, to minimize the number of subtraction by representing the answer in binary form. If we apply this rule, by chaining 8 of them, we can get a 8 bit division circuit:

![8 bit divider](../images/numerical_operations/8-bit-divider.png)

It works because it is basically a binary long division; if you insert 67 / 5 into the structure, it triggers stage of 8x and 4x and 1x which is 13, while the remainder 2 is shown in the remainder module. (Module 2E in the image of 8 bit division structure). It works on decimal number too since there is not quantization, so you can easily fill a equation of 10.6 / 5.3 and you can still get a two.

However, this circuit has two flaws. The first problem is quite obvious that the result does not support decimal numbers, so you cannot compute anything precise; another problem is the range of operation is narrow. Even though you can extend the number of stages to handles larger number or finer fractions, it is unrealistic that the division circuit is so huge which might consumes too much CPU power, so this implementation is not ideal yet.

## Newton’s Method With Waveshaper

You might already know in the “Waveshaper In LQ Mode Redifines SunVox Programming” post. Let me tell about about the Newton’s method which includes a division algorithm which provides a great result with a small, fixed number of iteration. All you need to know is the following equation: