# NanoseqTest
This is a test page for using **nf-core/nanoseq** using Seqera. 

## nf-core/nanoseq
**nfcore/nanoseq** is a bioinformatics analysis pipeline for Nanopore DNA/RNA sequencing data that can be used to perform basecalling, demultiplexing, QC, alignment, and downstream analysis. [Read more](https://nf-co.re/nanoseq/3.1.0/)  
  
## Input file formats
You can start from **FASTQ (.fastq /.fq)** files, but for the test we are using **BAM** files.<br/>
 <br/>
You need **two input files** in the **data** directory:
### 1. BAM files
**BAM files (.bam)** are the compressed binary version of **SAM files (.sam)** that represent the aligned sequences. SAM files are human-readable unlike BAM files. 
You can use the command `samtools view file.bam` if you wish to know the content of BAM files. You have one BAM file per sample.
- [x] Put <ins>ALL</ins> of your BAM files into **data/bam** directory
```
mkdir -p projects/AMD  // make the project directory
cd projects/AMD        // change directory into the project directory, all of the analysis will be done in this directory
mkdir -p data/bam      // make the data directory
mv <bam file directory>/*.bam* data/bam // move the files from where they were to the data directory
```
### 2. CSV file
You now need a **CSV file**, Comma-Separated Values, which lists your input files.  
```
touch samplesheet.csv
nano samplesheet.csv
```
The header of this file is:
```
group,replicate,barcode,input_file,fasta,gtf
```
- group: patient/control
- replicate: number your samples (i.e. 1, 2, ...)
- barcode: unique ID for your samples (i.e. patient1)
- input_file: full path of your input file
- fasta: reference fasta to which sequences are aligned
- gtf: annotation (optional)
  
For example, your samplesheet.csv file will look like:
```
group,replicate,barcode,input_file,fasta,gtf
AMD,1,AMD_P1,/project/AMD/data/AMD_P1.bam,hg38,
AMD,2,AMD_P2,/project/AMD/data/AMD_P2.bam,hg38,
Control,1,AMD_C1,/project/AMD/data/AMD_C1.bam,hg38,
Control,2,AMD_C2,/project/AMD/data/AMD_C2.bam,hg38,
```
Note that the last value is left empty as it is optional.


## Running nanoseq
![image](https://github.com/user-attachments/assets/4b3c523f-a22b-459b-83e7-75e9d6ffe5d6) </br>
Because we have BAM files, we are going to start the pipeline from samtools command.
To do this, we need to provide two parameters: --skip_demultiplexing and --skip_alignment
```
nextflow run nf-core/nanoseq \  // run nanoseq
    --input samplesheet.csv \   // provide the CSV file you created above
    --protocol cDNA \           // RNA
    --skip_demultiplexing \
    --skip_alignment \
    -profile docker
```

Once you're done with the run, you'll see the results in `results` directory.

