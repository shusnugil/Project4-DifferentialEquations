# Project4-DifferentialEquations
PSI Numerical Methods (2022/2023) course project 4. The solutions for the problems are in the file `Project4-SercanHusnugil.ipynb` file, written in Julia v1.8.4.

In this project, we aim to demonstrate how to utilize `julia` for solving differential equations. Specifically, we focus on the wave equation and some of its properties. We make extensive use of the code implemented in lectures by Erik Schnetter (https://pirsa.org/C23003).

In Problem 1, we use finite difference methods to evaluate the 1+1 dimensional wave equation. We impose Dirichlet boundary conditions so that the amplitude of the wave diminishes on the space the boundaries. The initial condition is a Gaussian-like wave of which a plot is shown below.  

![download](https://user-images.githubusercontent.com/122399037/221422372-cc7dd072-ffcd-420b-a62a-1a7ac0e630bc.png)

We plot the propagation of the wave for using the spatial domain bounds `[-1; +1]` and evolving from `t=0` to `t=4L`.

![download](https://user-images.githubusercontent.com/122399037/221422683-7c60d2d9-0a65-41de-a5f5-1a8e096dfe51.png)

In Problem 2, we try different values for time step `dt` and test the instabilities of the code. The way that we implement the coordinate grid, increasing ``dt`` fro ``0.01`` to even ``0.011`` results in an instability. To get around this instability, one can also adjust the total length of t coordinate such that the number of points along t axis changes accordingly. Still, however, the robust solution seems to be settin ``dt = dx`` whenever ``dt`` is changed. This allows the code to generate a plot without returning an empty grid. Of course, increasing the step sizes ``dt=dx`` too much results in more and more coarse-graded grids. If we increase the value from ``dx=dt=0.1`` to ``0.2``, the plot no longer makes physical sense. Therefore, we conclude that for step sizes ``dt=dx=0.2`` and larger, the numerical implementation no longer describes the physical picture we wish to investigate.

In Problem 3, we define and calculate the energy density of the wave. Energy density as a function of `t` and `x` is given as

$\epsilon(t,x) = \frac{1}{2} \left(  \left(\frac{du}{dt}\right)^2 + \left(\frac{du}{dx}\right)^2 \right)$

Below, we plot the energy density using the function from Problem 1. We decrease the width of the initial wave to `W = 0.05` after trying different values to get an optimum plot.

![download](https://user-images.githubusercontent.com/122399037/221425029-aeb5bc97-c9a3-4381-8d54-7c7d06b177cc.png)

As expected, values of energy density are high at the peaks of the Gaussian-like wave. Furthermore, when the waves are reflected from the boundaries or cross each other they interfere for a short amount of time, resulting a higher value of energy density.

Finally, in Problem 4, we calculate total energy, `E(t)`, as a function of time by integrating energy density over the spatial axis. The resulting plot is shown below:

![download](https://user-images.githubusercontent.com/122399037/221447894-d2e0a91f-6989-4a01-9f8a-1aeb70f7cf39.png)

We see some oscillations in the value of `E(t)`. The deviations from the constant value are especially prominent at the time values where the waves reflect from the boundaries or intersect with each other. This effect is expected since we are implementing finite difference methods.

Note that if we decrease the step size finite size effects are diminished and the oscillations become less prominent.

![download](https://user-images.githubusercontent.com/122399037/221448052-ea77cb00-bc91-4314-892b-5a7e35a31ca6.png)

Apart from the initial step in time and the `t` values at which multiple waves reflect from the bounrdary or intersect the energy seems to be constant. Therefore, decreasing the time step decreased the fluctuations in the energy as expected.
