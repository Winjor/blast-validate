Preprint available at <https://doi.org/10.1101/181636>

> Bazinet, A. L., Ondov, B. D., Sommer, D. D., & Ratnayake, S. (2017). BLAST-based validation of metagenomic sequence assignments. [_bioRxiv_:181636](https://doi.org/10.1101/181636).

**************************************************
**************************************************

Download and install the [ART read simulator](https://omictools.com/art-tool) and [Krona](https://github.com/marbl/Krona)

**************************************************
**************************************************

Simulate reads with ART, example:

art_illumina -ss HS25 -i B_anthracis_Ames.fa -p -l 250 -f 10 -m 868 -s 408 -o ba_ART_sim -1 /usr/local/packages/art_bin_MountRainier/Illumina_profiles/HiSeq2500L250R1.txt -2 /usr/local/packages/art_bin_MountRainier/Illumina_profiles/HiSeq2500L250R2.txt

-p = paired-end  
-l = length of reads to simulate (250 bp)  
-f = fold-coverage (10x)  
-m = mean fragment length  
-s = fragment length standard deviation  
-o = output prefix  
-1 / -2 = custom quality profiles for R1 and R2

**************************************************
**************************************************

Run parameter sweep, example:

perl scripts/blastValidate.pl -e -2,-4,-8,-16,-24 -b 5,6,7 -x -t 1392 ba_ART_sim.fasta ba_ART_sim

**************************************************
**************************************************

Evaluate parameter sweep, example:

perl scripts/evaluate_parameter_sweep.pl 1392 /path/to/B_anthracis/LCA/files /path/to/B_cereus (near neighbor)/LCA/files

**************************************************
**************************************************
