# HOW TO
1) For endpoints the respective potential
2) use reftraj on the generated trajectory, and rerun with the opposite potential
3) evaluate the gap
4) for intermediate, say 0.5, use hybrid/scaled to generate the trajectory, then rerun twice for each endpoints potential

# RECIPE
1) Input
2) topology.lmp
3) run.sh
NOTE : check pair_style, end point pair_coeff * *, ensure the topology consistent with the number
