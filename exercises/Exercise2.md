# Visualizing RNA-seq using IGV
Download the files `resultsAligned.sortedByCoord.out.bam` and `resultsAligned.sortedByCoord.out.bam.bai` from the server to your local computer. If you have forgotten how to do this, revisit https://github.com/BIOS3010/Module-5-multiple-alignment#533-moving-files-from-an-external-server-to-your-own-computer


1. Download IGV from here: http://software.broadinstitute.org/software/igv/download according to your computer's operating system
2. Install the downloaded IGV according to instructions on the web site
3. Open the recently installed IGV software
4. Select «S. Cerevisiae (sacCer3)” in the top left corner of the browser viewer
5. Click File->Load from file select the `resultsAligned.sortedByCoord.out.bam` file you recently downloaded from the server
6. Select “chrI” in the top left corner (right next to where you selected the reference genome version) zoom in until you see reads and the coverage histogram in the top view. Scroll around looking at the different genes. Zoom in so that you can see the individual reads as a line. Do you understand the relationship between the positions of the reads and the histogram on top?
7. Can you identify:
```diff
! A gene
! A highly expressed gene
! A gene with no gene expression
! A non-annotated gene with gene expression
+ Note that yeast has very few introns compared to other eukaryotes.
! But can you find a gene with RNA-seq reads spanning the junction of two exons
! A gene with an exon which is not expressed (meaning that the exon is skipped in the splicing)
! Do you observe some other interesting things?
```
