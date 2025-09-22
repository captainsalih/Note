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

### REFTRAJ-ENDPOINTS
1) copy input and dump to REFTRAJ, edit the mass commented or out commented based on the opposite topology
2) Edit the pair_style match to the opposite potential
3) Edit the last
```bash
rerun ./surface_2.dump first 0 every 1 dump x y z
```
---
4) Disable the restart. Just in case one want to dump the file then change the name so it will not the same
```bash
dump  1 all custom 1 revt_surface_2.dump id type x y z
```
---
6) copy the opposite potential NNP and topo lmp file to the current REFTRAJ dir
7) Apply the post-processing code, for initial endpoints (to sparse the output match to the dump used in reftraj)
8) On the REFTRAJ, use post-processing, with none sparse, the output will be extracted_data
 
