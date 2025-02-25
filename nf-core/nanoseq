# \[Test] nf-core/nanoseq

This is a test page for using **nf-core/nanoseq** with Nextflow.

## nf-core/nanoseq

**nfcore/nanoseq** is a bioinformatics analysis pipeline for Nanopore DNA/RNA sequencing data that can be used to perform basecalling, demultiplexing, QC, alignment, and downstream analysis. [Read more](https://nf-co.re/nanoseq/3.1.0/)

## Input file formats

You can start from **FASTQ (.fastq /.fq)** files, but for the test we are using **BAM** files.\
\
You need **two input files** in the **data** directory:

### 1. FASTQ or BAM files

**FASTQ files (.fastq / .fq / .fastq.gz / .fq.gz)** are files that store a DNA/RNA sequence and its quality scores. File extensions that contain **.gz** represents the gzip compressed files.&#x20;

**BAM files (.bam)** are the compressed binary version of **SAM files (.sam)** that represent the aligned sequences. SAM files are human-readable unlike BAM files. You can use the command `samtools view file.bam` if you wish to know the content of BAM files. You have one BAM file per sample.

* [x] Put ALL of your BAM files into **data/bam** directory

```
mkdir -p projects/AMD  // make the project directory
cd projects/AMD        // change directory into the project directory, all of the analysis will be done in this directory
mkdir -p data/bam      // make the data directory
mv <bam file directory>/*.bam* data/bam // move the files from where they were to the data directory
```

### 2. CSV file

You now need a **CSV file**, Comma-Separated Values, which lists your input files.

* [x] Make the CSV file

```
touch samplesheet.csv
nano samplesheet.csv
```

The header of this file is:

```
group,replicate,barcode,input_file,fasta,gtf
```

* group: patient/control
* replicate: number your samples (i.e. 1, 2, ...)
* barcode: unique ID for your samples (i.e. patient1)
* input\_file: full path of your input file
* fasta: reference fasta to which sequences are aligned
* gtf: annotation (optional)

For example, your samplesheet.csv file will look like:

```
group,replicate,barcode,input_file,fasta,gtf
AMD,1,AMD_P1,/project/AMD/data/AMD_P1.bam,hg38,
AMD,2,AMD_P2,/project/AMD/data/AMD_P2.bam,hg38,
Control,1,AMD_C1,/project/AMD/data/AMD_C1.bam,hg38,
Control,2,AMD_C2,/project/AMD/data/AMD_C2.bam,hg38,
```

You can specify FASTQ files in the input\_file column if your sequenced data aren't aligned yet.
```
group,replicate,barcode,input\_file,fasta,gtf AMD,1,AMD\_P1,/project/AMD/data/AMD\_P1.fastq,hg38,
```

Note that the last value is left empty as it is optional.

## Running nanoseq

![image](https://github.com/user-attachments/assets/4b3c523f-a22b-459b-83e7-75e9d6ffe5d6) Because we have BAM files, we are going to start the pipeline from samtools command. To do this, we need to provide two parameters: --skip\_demultiplexing and --skip\_alignment

* [x] Run the nanoseq
If you are using **BAM** files, as it is already aligned, you can skip alignment.

```
nextflow run nf-core/nanoseq \  // run nanoseq
    --input samplesheet.csv \   // provide the CSV file you created above
    --protocol cDNA \           // RNA
    --outdir result
    -profile conda
    -c ../../JK/projects/MIDD/resourceLimits.config
    -with-tower
    --skip_demultiplexing
    --skip_nanoplot
    --skip_fastqc
    --skip_fusion_analysis
    --skip_alignment
```
However, if you are using **FASTQ** files, you can't skip the alignment.
```
nextflow run nf-core/nanoseq \  // run nanoseq
    --input samplesheet.csv \   // provide the CSV file you created above
    --protocol cDNA \           // RNA
    --outdir result
    -profile conda
    -c ../../JK/projects/MIDD/resourceLimits.config
    -with-tower
    --skip_demultiplexing
    --skip_nanoplot
    --skip_fastqc
    --skip_fusion_analysis
```

Once you're done with the run, you'll see the results in `result` directory.
