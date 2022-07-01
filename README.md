# Signal-Generator
Matlab function that implements a general signal generator that:

1-asks user for following parameters: Sampling frequency of signal- Start and end of signal- Number of breakpoints and their position(i.e. the points that the signal definition rule changes).
Example: The signal is defined from -2:0 as a DC signal and from 0:2 as ramp the user will enter that the number of break points =1 and the position at t=0.

2. According to the number of break points the program asks the user at each region to enter the specifications of the signal at this region which are:
a. DC signal: Amplitude.
b. Ramp signal: slope – intercept.
c. General order polynomial: Amplitude-power – intercept. d. Exponential signal: Amplitude – exponent.
e. Sinusoidal signal: Amplitude – frequency – phase.

3. Display the resulting signal in time domain

4. the program asks the user if he wants to perform any operation on the signal 
a. Amplitude Scaling: scale value.
b. Time reversal.
c. Time shift: shift value.
d. Expanding the signal: expanding value
e. Compressing the signal: compressing value
f. None

5. Display the new signal in time domain
