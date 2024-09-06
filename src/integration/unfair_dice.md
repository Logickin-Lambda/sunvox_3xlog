# Example 1 - Unfair Dice

## Overview
In this Chapter, I am going to show you how to use the concept in the previous chapters, to build a simple siz face dice which you can roll with keypress.

## Planning The Project
To build a dice which can accept user input, we need to identify the components:
- A randomizer generates number ranging from 1 - 6
- An input for taking users' entries
- A timer for the dice animation
- A memory block to store a random value once the timer times up
- A display element to show the dice dots

With all those components, you may try to come up with a flow chart, to see how the logic flows:

![dice flow chart](../images/integration/unfair_dice_flow_chart.png)

As you can see, in this project, I would expect a user pressing key, and it triggers a timer with the midi signal which it updates graphics based on the randomizer. The timer counts until it has reached the time limit. Once it times up, it send a write signal to a memory while it records the last state of the randomizer, while changing the display showing the dice value based on the stored value in the memory.

Once you have a clear flow of logic, you may move on to the next phase.

## Input
To prevent user breaking the contraption by rapidly pressing the input, we need a SR latch, after a full volumed, monophonic DC generator. Remember to leave a AM modulator for the resetting the SR latch:

![dice input](../images/integration/dice_input.gif)


## Timer
The main timer comes after the input, which is a simple rising edge monostable (5 second in this case).

![dice timer](../images/integration/dice_timer.gif)

## Randomizer
