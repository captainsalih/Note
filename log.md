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
3) changfa 100 step active learning ready to be trained
4) continue for more 10000 just in case this additional does not work
5) run h3o_1nm lambda 1 and 0 on elysium, the combination is done by generating data from aimd data, here 0 cp2k is 1 lammps, applied also for 1 cp2k. The lmp file is generate using atomsk, check pka_ti for detail. the input is the same with the h30 bulk with some modification
6) run active8 of cubic bulk on daenfall

# OCT 9
1) continue NNP for BULK, FLAT, PIT
2) run TI-NNP for H3O, Lambda 0.25, 0.25, 0.75 (REFTRAJ TWICE NOT YET)
3) run TI-NNP for acetic_confine REFTRAJ for 0.25, 0.5, 0.75
4) run TI-NNP for acetic_confine_adsorb for all
5) run TI-AIMD for acetic_confine_adsorb on daenfall
6) run TI-AIMD for acetic_1nm on daenfall

# OCT 12
1) TI on daenfall still on pending, switch to dhysnet run right away
2) since there is CHARGE -1 use LSD afterward,
3) succes finish CUBIC active on interface11, next train CHANG
4) TI-adsorb all and acetid REFTRAJ is on elysium and not copy yet
5) data for CUBIC on elysium is copied to the temporary now run continue with new net fresh from interface 11

# OCT 13
1) TI on daenfall still on pending
2) On Dhysnet is still running, long than I expected is 286 simulation time get 2000 and enough
3) The AIMD for the adsorb is very different with the one on the bulk, the FUNCTIONAL is B3LYP
4) continue the simulation of CUBIC, PIT, FLAT, this time FLAT use new net

# OCT 14-16
1) TI need to increase the temp
2) daenfal for TI is fast, but currently full
3) the problem of different in current result of TI is due to the assignment of H1 or dummy on the pos file
5) continue the simulation of CUBIC, PIT, FLAT, this time FLAT use new net
6) check the stability of new net
7) chang simulation is getting stable but still far from equilibration O of molecule is pulled away..may be due to the hyperparameter

# OCT 17
1) Copy and continue PIT, FLAT, BULK
2) Check BULK new net stability also for flat
3) the new new of bulk disperse, use 8.8 for active9
4) there is also active8 that still not train, get 50 out of it
5) FLat is getting better with new net
6) on optimize new tool surface density, there is a animation of H
7) I Think its not neccessary to know how many H, may be distribution is enough, write it first

# OCT 19-20
1) Complete high temperature 340,350,360 of acetic acid
2) Run high temperature for acetic adsorb
3) create pyton for pka eval
4) the h30 1nm is wrong, need to re-do
5) success on making polyfit

# OCT 21
1) Finish the pka, the trend and value is in line.
2) need to check the systematic error from jun cheng paer
3) code adsorption drift
4) additional point for acetic acid as well as confinement
5) check paper from anthony, is pka up or donw on confinement

# OCT 22
1) The h3O_nm is actuially right, you lmp is created by you using atomsk, the one in anthony is acetic conf configuration, the input is actually created according to h3O in bulk in term of which one is going to be restarined
2) Since the h3O_1m is the same for middle and adsorb, there are data for high temp, without reftraj, check it out
3) from this you must undertrand that it is important to write in very detailed version so you are not lost, especially in handling parallel system

# OCT 27
1) The h3O_nm for intermediate is wrong since its not contain Si, currently run, REFTRAJ D and P not run yet
2) run acetic bulk on 300 K not the REFTRAJ
3) increase the system size to check the finite effect, check the code to parse the system to make it periodically big, then replace the other acid to 4 water

# OCT 28
1) set first mpi gpu for deepmd training
2) using cpu and distribution, under the hood of tensorflow

# OCT 29
1) undestanding the basic of machine learning, Neural Network
2) using pytocrcs, increasing the accuracy by comparing linear neural network and conolutional neural network testing on sign hand
3) Understanding the data augmentation and augmentation. Test also on the sign hand
4) using the avail model on pytorc hub, testing on clasified door for animal, 
5) transferlearning, and freezing
6) key convolution, convolution, flaten, then linear, linear, out

# OCT 31
1) Learning about the GPU speed paralelization, split the network on different network, using tensor parallel, and then pipeline parallel, check nccl
2) about the the assesment day3 
3) clone of the gpt, pythorc in gpt model for the data,
4) run beseline, then implement arg runfirstdeepsped.py, refer the notebook6 on convlution, its about deepspeeed

# Nov 3
1) h3o_1nm is finished on elysium
2) 300 is done
3) REFTRAJ_P and REFTRAJ_D of intermediate is run, if correc, then run for the pka eval, use the code to generate the periodic it better to move it on the middle use avogadro (check the difference)
4) TO DO,analysis 300 acetic, 330 confinement, big system (ceate system first)

# Nov 4
1) confinement finish
2) create python to multiply the box, check surface_pes_grid project on gpt, the chat is replicationg the PBC
3) its going to create 8 copy of periodic surround it, 1 0 1 mean 1 copy in x, 0 in y, and 1 in z
```bash
python transform_big_cell.py   --in 1_frame.xyz   --out supercell.xyz   --box  22.2680 25.2900  20.3530   --copies 1 0 1
```    
4) run lambda 0 on elysium, tesint success

# Nov 6
1) 3 points for bigger system is done
2) since the energy increase multipy by the size of the system
3) now running the hydronium on the elysium
4) arka code for grid search is done
5) use the density profile to get C so we know where is the distribution of them on the system
6) to do : make the angle for surface water molecule, using angle from normal to bisection and normal side of water so we get flat orientation
7) combine the data and stride and run the simulation, the data for angle should give the ide of structural of the surface, the the edge

# Nov 7
1) big system h3o fail due to the box size
2) to do : similar to the previous one make the angular analysis

# Nov 7
1) on gpu the pka big NNP takes 13 hours with gpu
2) on the reduction data, use configuration, plot energy or force vs configuration, use soap to check the similarity, reduce it
3) on the angular analyisis, similar to the surface proton, where we use ROI, means that we can select first solvation layers, second, etc ,and evaluate the angle orienatation
4) to do : angular analisys, pka h3o big finalize, write the paper, target 1 week
5) check cp2k with higher level of simulation, use for halide, microsoft functional
6) on chang, now 50K dataset, system not explode but it seems the distance elongated, currently increase the sel for Na and Cl
7) to do is optimize the configuration, add to data set, or add new data that already run on chang daenfal (20000), combine it become 70K
8) make sure the high energy is not include on the dataset

# Nov 10
1) the difference in energy between h3o big and acet big is enormous, about 129 eV, in case of small system its around 0.54eV
2) here acetic is higher with 800-ish and h3o with 700-ish,
3) since the energy increase by the number of molecule, currently rerun the h3o by only remove the hydrogen from additional h3o due to the multipication of the system
4) create picrture for acetic in bulk, work again on workflow so you dont overburden
5) make cv according again in detail, check ig

# Nov 12
1) deleting 3 hydrogen or 3 more water molecule decrease the energy by 65
2) currently run with 6 less water
3) finish analysis RDF for acetic acid and water, and figure 2 for anthony paper
4) supplementary also done
5) work again on workflow so you dont overburden
9) make cv according again in detail, check ig

# Nov 13
1) Succes make new layout of CV
2) as expectec 3 delete increase 61 energy, need 4 more to close the gap
3) the water on the middle tends to go the surface, currently test in three different configuration
4) prepare the water system that make the consisten number of molecule

# Nov 17
1) evaluation of h3o 1nm to make it on the middle is successed, turn out test2 is the good one
2) currently run for different composition of water, name test2, test3, test4, read readme on
```bash
/home/saleh/temporary_files/ANTHONY/test_hydronium_big
```
3) create from test2 that in the middle, and delete the water again, see from which one have the best close to target and delete according to those number of water (in term of deleteion done in number 2 above)

# 1TO DO
1) pka anthony adsorb and not adsorb, paper, active learning, TEMPERATURE, DONE
2) analysis, new analysis for proton at surface, and orientation, MRT, coverage, check the notes in phone and catatan di rumah; DONE
3) chang systyem, need to be run, analysis discussed by christina
4) update gpage, cv, motivation letter, research statement and do apply
5) continue all system, FLAT is already more than 10ns; CHECK CUBIC WHETHER IT NEED ACTIVE LEARN; I BELIEVE THERE IS DATA RUN ON HPC; CHECK
6) ARKA grid search code DONE
7) TAUFIK use the same code diff system


    
