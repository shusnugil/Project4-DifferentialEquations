# Project4-DifferentialEquations
PSI Numerical Methods (2022/2023) course project 4. The solutions for the problems are in the file `Project4-SercanHusnugil.ipynb` file, written in Julia v1.8.4.

In this project, we aim to demonstrate how to utilize `julia` for solving differential equations. Specifically, we focus on the wave equation and some of its properties. We make extensive use of the code implemented in lectures by Erik Schnetter (https://pirsa.org/C23003).

In Problem 1, we use finite difference methods to evaluate the 1+1 dimensional wave equation. We impose Dirichlet boundary conditions so that the amplitude of the wave diminishes on the space the boundaries. The initial condition is a Gaussian-like wave of which a plot is shown below.  

![download](https://user-images.githubusercontent.com/122399037/221422372-cc7dd072-ffcd-420b-a62a-1a7ac0e630bc.png)

We plot the propagation of the wave for using the spatial domain bounds `[-1; +1]` and evolving from `t=0` to `t=4L`.

![download](https://user-images.githubusercontent.com/122399037/221422683-7c60d2d9-0a65-41de-a5f5-1a8e096dfe51.png)

In Problem 2, we try different values for time step `dt` and test the instabilities of the code. The way that we implement the coordinate grid, increasing ``dt`` fro ``0.01`` to even ``0.011`` results in an instability. To get around this instability, one can also adjust the total length of t coordinate such that the number of points along t axis changes accordingly. Still, however, the robust solution seems to be settin ``dt = dx`` whenever ``dt`` is changed. This allows the code to generate a plot without returning an empty grid. Of course, increasing the step sizes ``dt=dx`` too much results in more and more coarse-graded grids. If we increase the value from ``dx=dt=0.1`` to ``0.2``, the plot no longer makes physical sense. Therefore, we conclude that for step sizes ``dt=dx=0.2`` and larger, the numerical implementation no longer describes the physical picture we wish to investigate.

In Problem 3, we define and calculate the energy density of the wave. Energy density as a function of `t` and `x` is given as

\begin{equation}
    \epsilon(t,x) = \frac{1}{2} \left(  \left(\frac{du}{dt}\right)^2 + \left(\frac{du}{dx}\right)^2 \right)
\end{equation}
