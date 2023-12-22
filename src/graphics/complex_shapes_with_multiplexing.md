# Complex Shapes With Multiplexing

## Overview
> If you can play it slowly, you can play it quickly.
> 
> [*- The Sacrilegious Violin Guy (2018)*](https://www.youtube.com/watch?v=BvsvaCU6i1M)

"If there are only points, line and circles, why are those seven segment displays existed in the pong game and the VOXCOM 1610?"

![segment displays](../images/graphics/segment_displays.png)

As you are wondering, there is no way to make display using the techniques I have mentioned before because there is no way to conditionally control the individual segments other than redraw everything. To achieve such behavior, you must do Multiplexing.

## Concept
Let we put away SunVox away for awhile for introducing the concept. In the real world, displays don't have an one to one pin for every pixels because this approach is expensive and space inefficient. Take a standard standard definition 16:9 television as an example [^tv_resolution]; if the aforementioned way for controlling pixels was used, you would needed 640 x 480 number of control pins! (307200 in total) There is no way to have that many pins for a processor to control, not to mention how we can suppose to route all the connections with all three colors.

Therefore, to make it more space efficient and easier for processors to control, one of the solutions is to connecting the input pin of LEDs into specific rows, likewise to the output pins into a specific column, forming an matrix like shown[^dot_matrix]:

![segment displays](../images/graphics/dot_matrix_display.png)

Great, we have now reduce the complexity of connections from \\(O(n^2)\\) to \\(O(2n)\\) which is far easier to manage, especially for larger displays. With this approach, we can light up individual LED by switching on the a specific row and column. I have prepared a little simulation so that you can try out the LED matrix:

<object data="../apps/circuitjs/circuitjs.html?ctz=CQAgjCAMB0l3BWEA2M0wE4EYBwBYDMcMAmEpBSECqhAUwFowwAoPSJDMEkAZkjzhuVfoNrUWAJxBceokDmSD5VMHCkzufXsgVLtu1eumy+yHHuXmo4Y5p7sqiwY5trIG03l49nIbzxGHgDOlnwCCnDhYuAgAGYAhgA2wXQsoX68OpEi2arxyanpYToWOFGlbgUpaRn6ruVUrvmJNcV+ATn+PlWtRaEYBP76g4IIJBYthbUyAOy6eCPz1BO908XuFouCmyuTsX0zauzDOwK0q1NtoWqzDvq3POP7EIcsAOYyQ89fY0NUHk+GGWP2BugQ-ygH1skAsP12EJigNsJ3h52okORjz2tjuGKRLAASl15PMLCobKibADoAgWAB3EkRRoGKGMllZXQc6wedkVaws5oMroNKKdDxAA" width="100%" height="500vh"></object><br>

Nevertheless, there is a problem: the matrix works for individual light, how about a more complex shape, like a letter "A"? No matter how hard you have tried, you can either able to switch on or off for the whole row or column of the matrix, and you can't switch off the middle LEDs. 

This is where Multiplexing comes in. Multiplexing doesn't generate the whole image, but one line at a time like shown:

<object data="../apps/circuitjs/circuitjs.html?ctz=CQAgjCAMB0l3BWK0BMC4E4AscwGYA2AlMFDEdCiyCgUwFowwAoHJbLEPSTphFLjyhUEzAE4gOgzgA4MBacLBxxkrJzyEQchZoU1lkVVMIzt8rgTMGVEqTho6QDpbbWcseAU88CbRgCUQAHZ+EBRggVCBFBxwcPB4cOgkFBThGFEwAjwQlBpuTmCZDSEEUgEkJBoaqGYgyJpfECszZtq46oyU5gBCEAATWgAzAEMAVwAbABclABoUObw5rDmkAEE5gCE5gGE5gBE5gFFBsQBLADdaMQAdAGchgGMAeyGJQzhbgEdcL4A7SCfH5A0G3QGgyAgpjKcHwWG-ZSwiG4aFg-7MfJmUhwZy40gEDy4nAWIZjKazWpdIwAd202UUTkKdTpMgZem0Xi4Wlp9N0Vm0WDMphZfLxjkJ4tFbIUzRkMiaXN5Mi5HKZPOYrKFljMTIFyslLh8uOVCucXJ8Ss12jNcrNET81vlNAd4EILsiovwBA9Am9BX1TsNuJkkrQ+iDnHDbpQZmjvPwsfCCAUieFga16d12tiNSdObipAsua9ZAUJaL-OsTtVWhVMVi0q5KEbBKjjYTKDDra7GgzYuZMvCkGrrIZWPAKGbI9L0+xU4EIqMsyYWiwFiYQnX+nijGgwWICH4GBIJ6LwXIYGgobQx9PFTwWAYykSNDJExmqiYJRare9v84fwvzAH8EBPcB-zAvxX2A0CfQgrQU1qQxYM4fhsUgpMgI+ECPA3f9t1cBNlA8SVNw8M0E3dZwyOowiqPgwjvzwiM6TTGjeC8Mx0K9LiKCTZj+NHScLCwMiywoeDOwsJCILgvM2N7DjJ0lKDS1U8DBLUzsuTE3gFwA2cBGIXhcMM5cILKATIE9HiDBAPcD1vMhTxIMgL3Aa9DzvMAMAfJ9GH8QYRg-aZrXIihSESWz1C9TCMKs4TlBi3geBoBADzqFcbMqeCSPSqT4hgAgT0gPA5CFEgZFjEDkGCEDlEIPB0AwC8IiQQxgvJT82LSihMsMMwfWrbLOk0uBuPA+zHO8lzfLc1rLy85yzz8ltH2fIL3wpcKJpaGdWoUQk82ymcTMkTLzumq8nKPOaz3cpabzu1b-M218utC8LILynLJIUhCFDU-KKCm76tHOwbzOtQ7lNh4avT2vTX24zKEz65GQYQWL0c9TG-vKR0AHMLqOuInGOjJmCAA" width="100%" height="500vh"></object><br>

If it can do it slowly, it can do it quickly. Once you have increased the simulation speed, you can start to see the letter "A" on the dot matrix display because it is fast enough to fool our eyes to see it as a single still image rather than a bunch of scan lines although it is slightly dimmer than a constantly on LED.

This is the priciple of multiplexing, so let me show you how to do that in SunVox.

## Implementation
Let me start from a simple example, making an interlocking twin circles. Here is an image made by overlapping two modules:

![interlocking circles](../images/graphics/interlocking_circles.png)

Clearly, we can't do that inside a metamodule because we only have one output channel, so we must combine the two elements into one before returning the result. We can't just sum two images using amplifiers because it will combine the total magnitude of two circle into one, resulting in a larger circle:

![interlocking circles the wrong way](../images/graphics/interlocking_circles_wrong.png)

For that problem, we must show them one at the time; this can be done using a square LFO and a NOT gate, alternating the first and the second circle using modulators. Keep in mind that the frequency of the square LFO must not be the multiple of the LFO which generates shapes, or you will get a incomplete shape as a result:

![interlocking circles the correct way](../images/graphics/interlocking_circles_correct.png)



### Reference

[^tv_resolution]:[TYPITO - List of TV Resolutions](https://typito.com/blog/video-resolutions/)

[^dot_matrix]:[Image by Microcontrollerslab - LED Matrix Interfacing with PIC Microcontroller](https://microcontrollerslab.com/led-matrix-interfacing-pic-microcontroller/)