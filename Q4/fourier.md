## Fourier Transform

_General Idea:_ A Fourier transform converts from the time domain to the frequency domain
 * Time domain - normal domain used for functions, where the value for a certain independent variable (such as time) has a specific output value
 * Frequency domain - provides the amplitude and phase (as complex number) with an input of the frequency
 * Input: time domain function, outputs: frequency domain function

**Explanation:**
 * Almost all functions can be decomposed into a sum of sine and cosine functions
   * Means that a bunch of curves, when weighted properly, can be added together to create almost any function or signal
 * Why is this important? If we can see what frequencies and periodic components make up a function, we can identify the sources or causes of specific output signals in a function
   * Example: sound involves a sum of harmonics: each harmonic is a different frequency; all the harmonics are played together to create a specific sound
     * plucking a string on a guitar causes multiple frequencies to be created to make the sound of that guitar string => _fourier transform allows you to analyze the components of this sound_
   * Example: fourier transform can be used to find the components or sources that are found in a final light wave
   * Example: data compression, only need to store important frequencies to keep a representation of something
 * Overall use: instead of analyzing change over time in a function, we can analyze components of a function and how they add up to make the whole, in other words identify causes of a specific function output!

**Intuitive Understanding of the Fourier Transform equation:**
 * Input => the frequency, output => a rotation (provided by a vector, with the magnitude being the amplitude of the sine curve and the argument being the phase shift)
 * equation: infinite integral over time(function * e ^ (i * 2pi * frequency * time))
 * Representation:
   * the e part = sets the rotational frequency and scales the function based on that
   * When summing over => getting the average value of the sine function after looping across the whole function
   * Can be thought of as converting to a polar equation (a circular figure scaled by the function)
 * When summing the parts in this rotational plane, most will cancel out (opposite quadrant values)
 * In the integral => summing will cancel out other frequencies and will only leave the starting vector after everything cancels
 * starting vector - represents rotation in a circle with phase shift and amplitude

**Concepts:**
 * starts with a Fourier series - a way of representing periodic (repeating) functions through a bunch of sine and cosine functions
   * shows that any periodic function can be created by adding sine and cosine functions with specific coefficients
 * Fourier transform - method of finding a Fourier-series-based function from the original function
   * Original function takes the time as input and outputs the output value of the function
   * The fourier transform of the function takes the frequency as input and provides the amplitude and phase for that specific frequency component in the function
   * Works for non-periodic functions as well

**Mathematical Concepts:**
 * important concept: e ^ iθ represents rotational motion
   * Same as cosθ + isinθ to the power of a value, because it increments by the value over time
   * e shows continuous growth in the rotational motion, through quadrants of the complex plane
 * Goal: find the amplitude and phase shift of a specific frequency in a function given the frequency
 * Observation: for all periodic functions that arent scaled vertically, they integral will be 0 because they all repeat
   * So how do we find the amplitude/phase for a specific frequency? decrease the desired frequency to 0 to find its amplitude, while everything else will cancel out
   * uses the e ^ -i2π * x * frequency - for every whole x number, full rotation completed and frequency repeats
     * Higher frequency value increases the speed of rotation, when frequency parameter is 2, the function scaling value will pass the same weight location two times as fast
   * the function is scaled based on the speed provided by the complex rotation pattern
 * when frequency is low: the function values will be scaled based on the corresponding frequency due to the rotation speed of the e term (speed based on frequency pattern)
 * The frequency is scaled by the function itself at each timestep - used to get information from the actual function and its variation
 * When summing the values in an integral => most cancels out (including other frequencies) except for the "starting" value of the function (complex number)
   * Magnitude provides amplitude, angle provides phase shift