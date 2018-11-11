both folders contain 2 Sn atoms, with different atomic positions.
I believe Sn is beta-Sn and Sn2 is the most common tin structure as
found in the inorganic chemistry database.

both contains several short runs and one long run, the short runs were
done with Ecutoff 150 ev, becuase looking at the SSSP pseudos this seemed 
ok for quick calculations.
For the long ones, they've got 350ev and 250ev, respectively.

there are two main things that annoy me, 
a) so many p-1 symmetry groups, only a few with I4
b) the energies.

I'll send off another one now with max_geom_iter = 200
(theyve been 20 in the past, which seems standard at examples,
but its very little, no?) 200 is probably way to much though

[s1422421@studentrun01 Sn]$ cat Sn.cell 
%BLOCK LATTICE_ABC
5.8315 5.8315	3.1814
90.000	90.000	90.000
%ENDBLOCK LATTICE_ABC

#SPECIES=Sn
#NATOM=2

#SLACK=0.25
#OVERLAP=0.1
#MINSEP=2.5
#COMPACT

KPOINTS_MP_SPACING 0.1

SYMMETRY_GENERATE
SNAP_TO_SYMMETRY

%BLOCK SPECIES_POT
QC5
%ENDBLOCK SPECIES_POT

[s1422421@studentrun01 Sn]$ cat ../Sn2/Sn.cell 
%BLOCK LATTICE_ABC
3.299 3.299 3.299
109.471 109.471 109.471
%ENDBLOCK LATTICE_ABC

#SPECIES=Sn
#NATOM=2

#SLACK=0.25
#OVERLAP=0.1
#MINSEP=2.5
#COMPACT

KPOINTS_MP_SPACING 0.1

SYMMETRY_GENERATE
SNAP_TO_SYMMETRY

%BLOCK SPECIES_POT
QC5
%ENDBLOCK SPECIES_POT
[s1422421@studentrun01 Sn]$ 





[s1422421@studentrun01 Sn]$ cat Sn.param
task                 : geometryoptimization
xc_functional        : PBE
spin_polarized       : false
fix_occupancy        : false
metals_method        : dm
mixing_scheme        : pulay
max_scf_cycles       : 1000
cut_off_energy       : 350 eV
opt_strategy         : speed
page_wvfns           : 0
num_dump_cycles      : 0
backup_interval      : 0
geom_method          : LBFGS
geom_max_iter        : 20
mix_history_length   : 20
finite_basis_corr    : 0
fixed_npw            : true
write_cell_structure : true
write_checkpoint     : none
write_bib            : false
write_otfg           : false
write_cst_esp        : false # Requires Castep 17 and above
write_bands          : false # Requires Castep 17 and above
write_geom           : false # Requires Castep 17 and above
bs_write_eigenvalues : false
calculate_stress     : true
