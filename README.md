# Introduction

This repo is for the paper _Wavelet Based Statistics for Enhanced 21cm EoR Parameter Constraints_ [2311.00036](https://arxiv.org/abs/2311.00036).


# Frontend Script
In the main script, [Frontend_Fisher_Script.ipynb](https://github.com/iny333/WM_Paper_repo/blob/main/Frontend_Fisher_Script.ipynb) we show we produced our results. This file loads all of our data and then summarises their LoS evolution.
We then create the Fisher matrices for our different statistics, as well as their convergences and covariance stability checks, before plotting our Fisher matrices. 

We use [Chain Consumer](https://samreay.github.io/ChainConsumer/) to produce our Fisher plots. This is a relatively simple package to use, we you simply need to give the package 
you inverse Fisher. 

# Backend Script
To ready our data, to be used in the main script, we show an example notebook containing functions that 
create the window functions and then the statistics needed in the main script.
These can be found in the folder [Backend_Scripts](https://github.com/iny333/WM_Paper_repo/tree/main/Backend_Scripts).

Whilst we use our own power spectra functions to produce the 2D and 3D PS, we use [pywst](https://github.com/bregaldo/pywst/tree/master) to produce our RWST results. The paper for this work can be found here: [1905.01372](https://arxiv.org/abs/1905.01372). To summarise our LoS evolution, we use [PyWavelets](https://pywavelets.readthedocs.io/en/latest/), which can easily been installed with pip or conda.

# Simulations
For our 21cmFast Simulations we used version 3.2.1. To generate the seed we use:
```python
import time
start_time = time.time()
random_seed = int(start_time/np.random.randint(1,50))
```
## Our run of 21cmFast is as follows:
```python
HII_DIM = 256
BOX_LEN = 140
user_params = {"HII_DIM":HII_DIM, "BOX_LEN": BOX_LEN, "USE_FFTW_WISDOM": True,"USE_INTERPOLATION_TABLES": False}
lightcone_quantities = ('brightness_temp','xH_box')
initial_conditions = p21c.initial_conditions(user_params=user_params,random_seed=random_seed, direc=output_dir)
lightcone_fid = p21c.run_lightcone(redshift = 8.813873961895457,max_redshift=9.372252076209087,init_box = initial_conditions
,lightcone_quantities=lightcone_quantities,random_seed = random_seed,direc = output_dir,zprime_step_factor=1.0005)
```
### For our parameters' Plus/Minus, for the derivatives, we use:
### $T_{vir}$
Plus: astro_params = {'ION_Tvir_MIN':4.740362689494244}, Minus: astro_params = {'ION_Tvir_MIN':4.653212513775344}
### $R_{max}$
Plus: astro_params = {'R_BUBBLE_MAX':20}, Minus: astro_params = {'R_BUBBLE_MAX':10}
### $\zeta$
Plus: astro_params = {'HII_EFF_FACTOR':35}, Minus: astro_params = {'HII_EFF_FACTOR':25}
