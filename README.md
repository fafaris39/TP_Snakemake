# ATACseq workflow Snakemake
## Université Clermont auvergne, 2022
This is atacseq analysis snakemake of data produced in the Gomez-Cabrero et al. (2019) publication (STATegra, a comprehensive multi-omics dataset of B-cell differentiation in mouse https://pubmed.ncbi.nlm.nih.gov/31672995/ ). The atacseq analysis locate in (https://github.com/fafaris39/Projet_GPU/tree/master).
The purpose of this project is to identify accessible chromatin regions,, which are generally transciptionally active genes. For this reason, the analysis was conducted on a murine B3 cell line,This cell line from the mouse model the pre-B1 stage (or Hardy's fraction C'). After the nuclear translocation of the transcription factor Ikaros, those cells progress to the pre-BII stage (or Hardy's fraction D).During the pre-BII stage, B cell progenitors undergo a growth arrest and a differentiation. This B3 cell line was transduced by a retroviral pathway with a vector coding for a fusion protein, Ikaros-REt2, which enable to control nuclear levels of Ikaros after exposing to the Tamoxifen drug. After drug treatment, the cultures have been collected at t=0h and t=24h.

### Dependencies, in order of use:
		- FastQC
		- Trimmomotic                             
		- FastQC
		- Bowtie2                  
		- Picard(MarkDuplicates)                 
		- deepTools        
		- Macs2(callpeak)

### Directory structure

```
├── atacseq
│   ├── data
│   │   ├── NexteraPE-PE.fa
│   │   ├── reference
│   │   │   ├── bowtie2
│   │   │   │   ├── all.1.bt2
│   │   │   │   ├── all.2.bt2
│   │   │   │   ├── all.3.bt2
│   │   │   │   ├── all.4.bt2
│   │   │   │   ├── all.rev.1.bt2
│   │   │   │   └── all.rev.2.bt2
│   │   │   └── fasta
│   │   │       ├── all.fasta
│   │   │       ├── chr1.fna
│   │   │       ├── chr10.fna
│   │   │       ├── chr11.fna
│   │   │       ├── chr12.fna
│   │   │       ├── chr13.fna
│   │   │       ├── chr14.fna
│   │   │       ├── chr15.fna
│   │   │       ├── chr16.fna
│   │   │       ├── chr17.fna
│   │   │       ├── chr18.fna
│   │   │       ├── chr19.fna
│   │   │       ├── chr2.fna
│   │   │       ├── chr3.fna
│   │   │       ├── chr4.fna
│   │   │       ├── chr5.fna
│   │   │       ├── chr6.fna
│   │   │       ├── chr7.fna
│   │   │       ├── chr8.fna
│   │   │       ├── chr9.fna
│   │   │       ├── chrX.fna
│   │   │       ├── chrY.fna
│   │   │       └── protein.faa
│   │   └── subset
│   │       ├── ss_50k_0h_R1_1.fastq.gz
│   │       ├── ss_50k_0h_R1_2.fastq.gz
│   │       ├── ss_50k_0h_R2_1.fastq.gz
│   │       ├── ss_50k_0h_R2_2.fastq.gz
│   │       ├── ss_50k_0h_R3_1.fastq.gz
│   │       ├── ss_50k_0h_R3_2.fastq.gz
│   │       ├── ss_50k_24h_R1_1.fastq.gz
│   │       ├── ss_50k_24h_R1_2.fastq.gz
│   │       ├── ss_50k_24h_R2_1.fastq.gz
│   │       ├── ss_50k_24h_R2_2.fastq.gz
│   │       ├── ss_50k_24h_R3_1.fastq.gz
│   │       └── ss_50k_24h_R3_2.fastq.gz
│   ├── logs
│   ├── results
│   ├── scripts
│   │   ├── Snakefile
│   │   ├── config
│   │   │   └── config.yaml
│   │   └── envs
│   │       ├── bowtie2.yaml
│   │       ├── deeptools.yaml
│   │       ├── macs2.yaml
│   │       ├── picard.yaml
│   │       ├── qc.yaml
│   │       └── trim.yaml
│   └── tmp
├── data -> /ifb/data
└── tmp
    └── ss_50k_0h_R1_1.fastq
```

### To launch the pipeline you need :
* __subset__ and __bonwtie2__ index files in `atacseq/data/subset` & `atacseq/data/reference/bowtie2`
* All output in   `atacseq/results`
* Snakemake config in `atacseq/scripts/config`
* Conda environment config files are in `atacseq/scripts/envs`
