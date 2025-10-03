# SEP21
1) run all,flat,pit,cubic, on elysium 
2) run active7 CUBIC on daenfall
3) train active6 CUBIC on interface11, here using stride 20 to get 50 point out of 500
4) run acet_1nm, lambda1, lambda0 on elysium
5) evaluation who is who 340 evary 200ps, test sparse evary 10 data, goal to get symmetry
6) set desity=True on set_dens_true, gives lower concentration but more smooth

# SEP22
1) Create the proton density, eval using cutoff criteria, set the farthest distance as the proton
2) Run bulk continue
3) Run acetic_1nm 0.75, 0.25, plus reftraj
4) compare with the DFT data using log, since the reftraj data is going to be sparsed (in order to reduce the size of the generated data)

# SEP23
1) continue run for bulk, Flat, and Pit. Most of Flat have reached the 10ps, decided to continue
2) frezee and analysis the r-squared for active6 of BULK
3) finish the last part, d-band center of arka

# SEP26
1) continue run for bulk using net active6, Flat continue to 20ns, and Pit continue to5ns currently only 4ns.
2) interface2 down, when change the GPU to 5090 RTX
3) once is up fix the problem with NVIDIA driver to tensorflow 2

# OCT 4
1) train 10000 in interface11 data of acid ion in solution, got better result than what we have so far using i=pi current vesion
2) continue cp2k 10000, 7 hour wait,
3) once its done take tail 9000 of the previous, combine with the continue and train for 1 mio
use the following for a sufficient calculation that required accuracy. the benchmark is on https://manual.cp2k.org/trunk/methods/dft/cutoff.html

```bash
&MGRID
  CUTOFF 250
  REL_CUTOFF 60 
&END MGRID
```    
 
