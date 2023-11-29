ZWA2
=======

[![Downloads](https://img.shields.io/github/downloads/konskons11/ZWA2/total?style=flat-square)](https://github.com/konskons11/ZWA2/releases)

ZWA2 is a context-based trimming bioinformatics tool for virus genome Next Generation Sequencing (NGS) read decontamination based on a given reference. The tool dissects partially mapped/chimeric reads that arise during NGS, removing moieties which mapped with sequences from the user input reference. The clean output reads are then ready to be fed into _de novo_ assemblers, increasing the availability of reads for more accurate and more efficacious _de novo_ virus genome assembly. 

The main concept behind the ZWA2 pipeline is outlined in the figure below:
![ZWA2_pipeline](https://i.imgur.com/0WLQ1o0.png "ZWA2_pipeline")

Installation of the standalone application
---------------
The ZWA2 standalone application is distributed for Linux and MacOS systems and may be executed directly after download. The prerequisites of ZWA2 ([bwa 0.7.17](https://github.com/lh3/bwa/releases/tag/v0.7.17) and [samtools 1.13](https://github.com/samtools/samtools/releases/tag/1.13)) will be verified for installation upon ZWA2 execution and if not installed, they will be downloaded automatically by the program.

Usage
---------------

The ZWA2 standalone application may be fully or partially deployed upon execution depending on the available user input files. In the case of ZWA2 full deployment, the directories of NGS reads (FASTQ format) and appropriate reference file (FASTA format) must be provided as arguments after the -i and -r flags respectively, in order to be able to perform all necessary alignments. For the alternative and faster partial deployment of ZWA2, the directory of a BAM file can only be passed as an argument after the -m flag, instead of FASTQ and FASTA files, as the user may have already carried out the desired alignment with the mapping software of preference. Alongside the input BAM file, the user may optionally pass as an argument the output unmapped reads of the performed alignment in FASTQ or BAM format after the -u flag, for later use by the algorithm. Lastly, the user has the ability to adjust the mapping sensitivity of the incorporated BWA software by passing the desired level of alignment stringency as an integer number after the -l flag (default value 30 \| <30 loose, >30 stringent). 

Apart from the ZWA2 standalone application, the user may utilize the online ZWA2 tool (https://srv-inseqt.med.duth.gr/ZWA2/HTML/ZWA2_method_selection.html), which does not require the installation of any software but solely the provision of the appropriate input files.

The parameters of the ZWA2 standalone application are summarised in the following table:
|Required argument flags|Description|Deployment|
|:---|:---|:---|
|`-i <string>`|directory of INPUT NGS READS file (.fastq, .fq or .gz extension)|Full|
|`-r <string>`|directory of INPUT REFERENCE file (.fasta, .fa, .fna, .fsta or .gz extension)|Full|
|`-m <string>`|directory of MAPPED NGS READS on REFERENCE file (.bam extension)|Partial|
|`-o <string>`|directory of OUTPUT folder|Full & Partial|

|Optional argument flags|Description|Deployment|
|:---|:---|:---|
|`-l <integer>`|alignment stringency value (default value 30 \| <30 loose, >30 stringent)|Full|
|`-u <string>`|directory of UNMAPPED NGS READS on REFERENCE file (.bam, .fastq, .fq or .gz extension)|Partial|
|`-t`|run ZWA2 on a test dataset to verify installation|TEST MODE|

### Run examples
Full ZWA2 deployment run examples:
```sh
./ZWA2.sh -i reads.fastq -r ref.fasta -o ./
./ZWA2.sh -i reads.fq.gz -r ref.fasta.gz -o ./
./ZWA2.sh -i reads.fq.gz -r ref.fasta.gz -l 40 -o ./
```
Partial ZWA2 deployment run example:
```sh
./ZWA2.sh -m mapped.bam -o ./
./ZWA2.sh -m mapped.bam -u unmapped.bam -o ./
./ZWA2.sh -m mapped.bam -u unmapped.fq.gz -o ./
```
