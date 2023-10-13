# ZWA2
ZWA2 is a context-based trimming bioinformatics tool for virus genome RNA-seq read decontamination based on a given reference. The tool dissects chimera reads that arise during NGS, removing chimeric moieties with the user input reference. The clean output reads are then ready to be fed into _de novo_ assemblers, increasing the availability of reads for more accurate and more efficacious _de novo_ virus genome assembly.

_Dependencies:_
- [bwa](http://bio-bwa.sourceforge.net/)
- [samtools](http://www.htslib.org/)

