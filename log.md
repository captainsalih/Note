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
 
