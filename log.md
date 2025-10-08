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
 
# OCT 5
1) github page fails, due to pull and merge on the wrong dir and then trying to merge back, so now using windows visual studio
2) install visual studio on window, install git, install ruby, jekyl and gem for the theme
3) delete the repo and clone again
4) focus on writing paper, and research statement 

    
# OCT 6
1) github page succes in the linux env, do not edit online. Next task is to build it steady
2) pc lab error, due to upgrade to the new ubuntu noble, keyboard hang, cant log in
3) new 10000 continue chang fa is done, now its in training, the energy profile with prev 10K is promising 
    
# OCT 7
1) computer is run, graphic card is now waiting to change
2) continue bulk, need 1 more active learning
3) finish abstract arka

# OCT 8
1) for cubic bulk, from 4 to 7 is use active6 net, use diff to check the difference
2) active7 for cubic is on the train at interface11, for 500 AIMD sampling --block 2 --stride 20 gives 50 frame, then modify with dummy  


# TO DO
1) pka anthony adsorb and not adsorb, paper, active learning 
2) analysis, new analysis for proton at surface, and orientation, MRT, coverage, check the notes in phone and catatan di rumah
3) chang systyem, need to be run, analysis discussed by christina
4) update gpage, cv, motivation letter, research statement and do apply
5) continue all system, FLAT is already more than 10ns


    
