## Applying Rare Event Sampling to the Planet Simulator (PlaSim) 

This repo applies a rare event algorithm to the coupled atmospheric-oceanic model PlaSim. The goals of this research are 
a. determining the edge state in PlaSim between on and off states of the AMOC
b. determining optimal locations and state variables to position optimal observations for an early warning system of AMOC collapse
c. refining the methodology used in Cini et al. to produce noise-induced transitions in PlaSim

A control simulation with a spin-up of 1000 years is initialized with a total of 2000 years, and one random point from the run is chosen to continue a simulation of an ensemble of 100 trajectories. Running this ensemble with an initial kick at the first timepoint results in stochastic forcing of the system, allowing the trajectories to spread. The standard deviation of the AMOC index of the trajectories is taken, and when the system has lost memory over time, this may be taken as the resampling time.

An ensemble of trajectories is initiated taking 100 stationary states of PlaSim from the control run after its spin-up has completed. At resampling intervals, the rare event algorithm is applied. 

At higher values of k or something, transitions are not happening.
-Or maybe, need a different resampling time - the cumulative resampling, which is more like 25 days...but also that's basically what we found already so...??? need to check this again

Plasim sits at the middle of Dijkstra's hierarchy of models \cite{dijkstra2024role}. an Earth System Model of Intermediate Complexity. This model consists of a dynamical core based on the moist primitive equations representing conservation of momentum, mass and energy, which has been adapted from a simplified general circulation model, the Portable University Model of the Atmosphere (PUMA) \cite{fraedrich2005planet}. This has been coupled with systems of lower complexity including land-surface processes, vegetation, ocean and sea ice \cite{fraedrich2005planet}. Our version of PLASIM has included an additional functionality of the large-scale geostrophic ocean, which has been implemented by J Hardenberg.

TODO: Read up on PLASIM
- quantify general description
- specifications of my run (10 atmospheric layers, etc.)
- inputs and outputs, parameterized inputs, etc etc
- AMOC overturning, how it's calculated - looking at one specific region - SPG
- Describe RE algorithm again, put graphs of AMOC spread and calculations of resampling time, AC time

- Have transition already with Matteo's k value, add mine

- Next two steps (if transitions are found) is checking on mass balance flux as a result of the transition (a marker of the edge state), and checking locations which are important for monitoring transitions (and seeing if they match up with the locations of R-tipping) read paper of Emma

- May need to integrate 200 years to get transition, maybe k should also be less idk - check cumulative integral, run in the background fiddling with different resampling times (and calculating the k from them)

