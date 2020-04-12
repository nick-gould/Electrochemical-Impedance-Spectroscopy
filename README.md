# Electrochemical-Impedance-Spectroscopy
Building equivalent circuits and working up EIS data using Python

## Electrochemical Impedance Spectroscopy

Electrochemical Impedance Spectroscopy, or EIS for short, is an analytical technique for probing the inner workings of an electrochemical system like a battery or fuel cell. In principle, it could also be used for any unknown electrical circuit. It works by introducing unit impulses to the circuit at a range of frequencies and measuring the impedance.

Gamry, a manufacturer of potentiostats that can be used to perform EIS measurements, [has a good primer on the subject](https://www.gamry.com/application-notes/EIS/basics-of-electrochemical-impedance-spectroscopy/).

I'm also familiar with the math behind EIS by a background in [Control Theory](https://en.wikipedia.org/wiki/Control_theory) and didn't learn it as an electrochemist might. So the wording may make more sense to an electrical engineer or chemical engineer than it might an electrochemist (who is more likely to use it).

The short explaination is an equivalent circuit is set up with several individual circuit elements and the liberal application of [Ohm's Law](https://en.wikipedia.org/wiki/Ohm%27s_law) and worked up using either Laplace Transformations (as I do here) or Fourier Transformations (a special case of Laplace Transformations and how most EIS literature does it). The impedance response is a complex number.

The advantage to doing it in the frequency domain is all the math is algebra and all the complicated dynamics of the differential equations are removed by the transform. Working with the data as Laplace Transforms also allows (usually) convenient conversion between frequency and time domains.

A [Gamry Interface 1010E Potentiostat](https://www.gamry.com/potentiostats/interface-1010e-potentiostat/) (the machine I'm most familiar with) has a range of 2 MHz to 10 μHz. Low frequencies take a long time to run in practice, but may be necessary to probe things like diffusion. 

Here I'm going to: 
* Set up Python classes for common circuit elements
* Set up a Python class for an Equivalent Circuit made of of those individual elements
* Plot Nyquist and Bode diagrams for example data
* Return those data as a pandas dataframe
