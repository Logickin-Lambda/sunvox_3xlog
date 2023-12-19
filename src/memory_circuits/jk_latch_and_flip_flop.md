# JK Latch and Flip Flop


## Overview
Despite not used in SunVox due to its questionable behavior, let's see how other solve the problem in SR latch by building a JK flip flop.

## JK Flip Flop
To overcome with the invalid state, an electrical engineer named Jack Kilby invented a universal Flip Flop.[^notey] Based on his own name, this flip flop solves the wasted invalid state, replacing with a toggle function as shown:

| IN J | IN K | OUT                | OUT Inverted       |
|------|------|--------------------|--------------------|
| 0    | 0    | retains prev state | retains prev state |
| 0    | 1    | 0                  | 1                  |
| 1    | 0    | 1                  | 0                  |
| 1    | 1    | toggle             | toggle             |

<br>

<object data="../apps/circuitjs/circuitjs.html?ctz=CQAgjCAMB0l3BWcMBMcUHYMGZIA4UA2ATmIxAUgoqoQFMBaMMAKDAUJBQ-ABZeQ2bJzD8oIXtFLSZs4iwAyXHqIFhiKPgKpUAZgEMANgGc61SIuWc0ecBq75xeo6fOXuIjCJS2wXpyAALgBOAK5mSBZghJrYCJqqEtgJYpoAJnQGoYaBDIZ0aeABMJCs0bHxDra8yVVcIBlZOXkFRTpQsKwA5kkpAvy+YjosPTWaNhK8thPDAB7gGFSivljgCBACKAIAUizz0Ugo7OB4VEfVXAIA0nsgpycJYNgnSJsCAMaGANYsQA" width="100%" height="500vh"></object><br>

This is a step forward to a better flip flop since the additional toggle function is useful for switching a device using a momentary switch, or used for building counter; despite its flexibility, this flip flop doesn't made into SunVox, as there are some inconsistent behavior for this device.

- Racing condition

How this flip flop works during the toggle state is that the flip flop intends to oscillate in a high speed, but the clock limits the oscillation, acting like it is toggling ON and Off. There is workaround, but I never use this flip flop in practice because there are two more simpler and more practical alternatives for any applications in SunVox, and I will tell you about that soon.


### Reference

[^notey]:[ElectronicsHub - Designing JK FlipFlop](https://www.electronicshub.org/jk-flipflop/)




