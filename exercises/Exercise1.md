## 13.1.1. Logging in to the external server
Using your terminal, log in to either `itf-appn-test01.hpc.uio.no` (group 1-5 do this) or `itf-appn-test02.hpc.uio.no` (group
6-10). If you have forgotten how to do this, refer back to the [exercises from Module 7](https://github.com/BIOS3010/Module-7---HTS/blob/main/00-Get_started.md#logging-on-to-the-server).

```diff
! In your home directory, make a directory called `Module13` 
! Navigate into the newly created `Module13` folder
```

```diff
+ Hint:
+ You should remember how to do this, but if not revisit exercise 1.3.9 and 1.3.3
```

## 13.1.2. Downloading the RNA-seq data
First, we need to download the required RNA-seq data:
```diff
! Download: https://ddbj.nig.ac.jp/public/ddbj_database/dra/fastq/ERA294/ERA294220/ERX424840/ERR458493.fastq.bz2
+ Note that the file ends with .bz2
! Use Google to find which decompression command to use for .bz2 files
! Decompress the file `ERR458493.fastq.bz2`
! Do you recognize the file type?
```

```diff
Note: 
+ Forgotten how to download files? revisit exercise 1.4.11
```

## 13.1.3. Downloading the Saccharomyces cerevisiae genome sequence

```diff
! Create a folder called `sacCer3`
! Download: https://hgdownload.soe.ucsc.edu/goldenPath/sacCer3/bigZips/sacCer3.fa.gz
! Move the file `sacCer3.fa.gz` into the `sacCer3` folder
! Decompress sacCer3/sacCer3.fa.gz
! Do you recognize the file type?
```
```diff
Note: 
+ Forgotten how to decompress .gz files? revisit exercise 1.4.12
```

## 13.1.4. Download the Saccharomyces cerevisiae genome annotations from Ensembl
```diff
! Download http://hgdownload.cse.ucsc.edu/goldenPath/sacCer3/bigZips/genes/sacCer3.ensGene.gtf.gz
! Move `sacCer3.ensGene.gtf.gz` into the `sacCer3` folder
! Decompress sacCer3/sacCer3.ensGene.gtf.gz
```

Now we have the (1) RNA-seq sequence data (fastq format), the genome sequence of the organism we are studing (fasta format), and the gene annotation (.gtf format). Now we are ready to do our RNA-seq gene expression analysis.

## 13.1.5. Preparing for mapping the RNA-seq data
- Run the following commands to load the sequence mapping software (STAR) and software to work with the sequences (SAMtools):

```bash
module load STAR/2.7.8a-GCC-10.2.0 SAMtools/1.10-GCC-9.3.0
```
Then, make an index of the genome:

```bash
STAR --runThreadN 1 --runMode genomeGenerate --genomeDir sacCer3 --genomeFastaFiles sacCer3/sacCer3.fa --sjdbGTFfile sacCer3/sacCer3.ensGene.gtf --sjdbOverhang 49
```

## 13.1.6 Mapping RNA-seq reads to the refernence genome index
- Run this command to map the reads to the reference genome sequence:

```bash
STAR --genomeDir sacCer3/ --readFilesIn ERR458493.fastq --outFileNamePrefix results --outFilterMultimapNmax 1 --outSAMtype BAM SortedByCoordinate --runThreadN 1 --alignIntronMin 1 --alignIntronMax 2500
```

## 13.1.7 Make an index of the mapping results (needed for visualization later)
- Run this:
```bash
samtools index resultsAligned.sortedByCoord.out.bam
```

## 13.1.8 Interpreting the output file
```diff
! Look at the resultsLog.final.out file. Try to describe what you see in the file.
```
