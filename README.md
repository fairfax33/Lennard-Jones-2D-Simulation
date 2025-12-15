# Lennard-Jones-2D-Simulation
Lennard Jones simulation of Molecular Dynamics featuring cell list implementation &amp; velocity verlet integration. Physics kernels compiled in Numba for runtime.

(supposedly) Shareable link to jupyter notebook - https://datahub.berkeley.edu/hub/user-redirect/lab/tree/Final_Project/Tau%20Experiment.ipynb

Download link - https://datahub.berkeley.edu/user/micahkeegan/files/Final_Project/Tau%20Experiment.ipynb?_xsrf=MnwxOjB8MTA6MTc2NTc2ODcyNXw1Ol94c3JmfDEzMjpaR0ZsTlRsaE1HWmhZbVV4TkRRd01tRTFaak15TmpWa01UUmhaVGRqTXpnNllXSmhaalU1TUdFME9UQTVOVGMwWmpCbU5tRmtPV0l3WldNME1XUXhNemN3TldKaFltTTNaVFZrWlRJek9XWmlOakkxWWpBM01UbGxZekU1WkRCaVpBPT18MDgyZmY4NDlkZjhhYjVhOTljMDQ0ZWIzNzhiNzM3MDAzZGU0NGU4M2YxNGNlOTAwZTZmYWM0YjA0M2UyMTNlNA

Read ME from 1st cell:

Cell 1: Read Me

Cells 2-4 are initilization of simulator

Cell 5 initializes a full-control simulator named "sim"

Cell 6 initializes helper functions to scale particle & quiver size

Cell 7 generates visualization of first N steps for sim, also where you set frame & capture rate

Cell 8 runs a pure physics simulation of first N steps for sim, also optionally generates 1st & last frames

Cell 9 generates any visualization created in previous 2 steps

Cell 10 is 2 helper functions to help with MB calculations

Cell 11 is a mega plotting function that graphs actual velocity distribution x expected, along with quantifiable error metrics (L1 is most helpful imo)

Cell 12 creates a new simulator instance and runs N steps, taking a snapshot (saves particle velocities) at user-defined intervals

Cell 13 visualizes convergence to MB from constant velocity

Cell 14 visualizes adherence to MB of a particular snapshot / final state

Cell 15 initializes real CPU runtime of Simulator class for 50 steps x theoretical GPU runtime

Cell 16 runs & plots function from cell 15

Useful Notes:

- Inside cell 5, simulation settings can be modified for visualization.
    There are sample combinations provided inside quotations that will not crash the program

- Inside cell 7 there are visualization settings. It is possible to increase framerate picture quality, and # of frames captured, but not recommended to do so.
    Oftentimes, the reason the simulation crashes is due to too many frames with too many pixels overloading the storage
    It is a good idea to not exceed 1000 steps of 300 particles for 6 frames captured per second displayed at 45 frames per second, with an 8 inch length x 80 pixel clarity. 
    
- Inside cell 11 there is a total_bins variable that can be modified to plot the simulated particles using a user_defined amount of bins.

- The variables at the top of cell 12 can be modified to create more intensive pure-physics simulations. There is no worry about overloading RAM here, as the particles & calculations themselves do not take up much storage.
    The main limitation is how long the user is willing to sit at their desk while the simulation runs
    A simulation of 100,000 particles for 10,000 steps will take ~ ___ seconds to run on a Macbook Air M4


- To view the difference in runtime between Numba compilation & running in pure python: 
    After running each cell in the notebook, comment out the @njit decorators above each function inside Cell 3
    Then, run cell 3 to update changes
    Then, run cell 16.
    Warning: before doing this, I recommend changing the up_to varible inside cell 16 to something lesser, like 8, and adjusting + observing runtime changes from there
    (You should see ~100x slowdown in the early stages)
