#Scripts to generate the figures in: "Multiple regimes of robust patterns between network structure and biodiversity"

'figs_paper.m' generates all the figures in the paper using results precomputed and saved in the folder 'data/'.

To show how the data was created an example is provided in 'example_one_set.m'. It calculates the dynamics and surviving species for all the matrices in the ensemble (100 different matrices) using the same single set of parameters and initial conditions for all of the matrices. This results in the following plot

![alt tag](https://github.com/lfjover/networks_params/blob/master/bio_one_set.png)

The plots in Figure 3 were created in this way (with a single parameter set). For Figures 2 and 4, each plot is an average of the number of survivors for 100 different parameters sets. To calculate the data in Figures 2 and 4 we used a computer cluster to compute each run in parallel.

Each run is computed using the function 'pers_one_set.m', which calls 'pp_integrator_stop_heu.m' to integrate  the system 100 times (one for each matrix in the ensemble) based on the stopping time heuristic described in the Methods section.

For Figure 7 'pp_integrator_fixed_time.m' was used to integrate the system for a fixed time.

The code that generates the parameters used in all the runs is in generate_parameters.m
The parameters are saved in the .mat files in the data folder. The names of the files start with "params" (e.g. 'data/params_single_set_fm100.mat'). There is a different file for each plot showing biodiversity in the paper. Once a file is loaded, the parameters and initial conditions in the "params" structure can be accessed in the following way:

[r,phi,beta,m,x0] = params{iSet,:}

where iSet is equal to 1 in the files used to generate Figure 3 ('data/params_single_set_fm1.mat', 'data/params_single_set_fm28.ma', and 'data/params_single_set_fm100.mat'),  and it goes from 1 to 100 in the rest of the files.
