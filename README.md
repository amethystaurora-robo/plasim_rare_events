## Applying Rare Event Sampling to the Planet Simulator (PlaSim) Run

This research applies a rare event algorithm which uses cloning and killing (more below) to force the system towards a collapsed state. The algorithm is applied to the Global Climate Model (GCM) of intermediate complexity, PlaSim, to allow for improved accuracy of results as compared to the Gottwald model, but to save on computational cost when compared with other models.

A control simulation with a spin-up of 1000 years is initialized, and one random point from the run is chosen to continue a simulation of an ensemble of 100 trajectories. Running this ensemble with an initial kick at the first timepoint results in stochastic forcing of the system, allowing the trajectories to spread. The standard deviation of the AMOC index of the trajectories is taken, and when the system has lost memory over time, trajectories may be resampled. 
