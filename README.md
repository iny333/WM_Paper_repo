### For our 21cmFast Simulations we used version 3.2.1. To generate the seed we use:
<code>import time
start_time = time.time()
random_seed = int(start_time/np.random.randint(1,50))<code>
## Our run of 21cmFast is as follows:
<code>HII_DIM = 256
BOX_LEN = 140
user_params = {"HII_DIM":HII_DIM, "BOX_LEN": BOX_LEN, "USE_FFTW_WISDOM": True,"USE_INTERPOLATION_TABLES": False}
lightcone_quantities = ('brightness_temp','xH_box')
initial_conditions = p21c.initial_conditions(user_params=user_params,random_seed=random_seed, direc=output_dir)
lightcone_fid = p21c.run_lightcone(
    redshift = 8.813873961895457,
    max_redshift=9.372252076209087,
    init_box = initial_conditions,
    lightcone_quantities=lightcone_quantities,
    random_seed = random_seed,
    direc = output_dir,
    zprime_step_factor=1.0005)<code>
### For our parameters' +/-, for the derivatives, we use:
### $T_{vir}$
Plus: {'ION_Tvir_MIN':4.740362689494244}, Minus: astro_params = {'ION_Tvir_MIN':4.653212513775344}
### $R_{max}$
Plus: astro_params = {'R_BUBBLE_MAX':20}, Minus: astro_params = {'R_BUBBLE_MAX':10}
### $\eta$
Plus: astro_params = {'HII_EFF_FACTOR':35}, Minus: astro_params = {'HII_EFF_FACTOR':25}
