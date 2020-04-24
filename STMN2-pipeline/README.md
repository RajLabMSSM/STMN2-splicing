
# STMN2 pipeline

A snakemake pipeline to extract QC'd splice junction reads within the STMN2 locus

Input: BAM files from the NYGC ALS consortium, aligned with the RAPiD pipeline

Steps:

1. BAM QC (with Samtools)
  Extract reads within the STMN2 locus (chr8:79,605,801-79,668,893) and filter out any reads that:
	* mapping quality below 30
	* PCR duplicated
	* mate is unmapped/ not properly paired
2. Extract junctions (with regtools)
  Extract junctions using standard parameters, minimum overhang of 9bp, max intron length of 250kb

3. Cluster junctions (with leafcutter)
   Perform clustering with very lax filters (total read counts and proportion of the cluster) to capture everything

Output: single count matrix of samples (columns) against junctions (rows) for all high quality junctions with STMN2 locus



