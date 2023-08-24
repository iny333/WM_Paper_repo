For our 21cmFast Simulations we used version 3.2.1. To generate the seed we use:
<code>
import time
start_time = time.time()
random_seed = int(start_time/np.random.randint(1,50))
<code>
