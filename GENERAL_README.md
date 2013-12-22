nucleotide-matching-tools
=========================

This repository contains tools for capturing upstream or downstream nucleotide sequences in a deep sequencing library. This is useful for capturing post-transcriptional nucleotide additions, splicing, or editing adjacent to a particular sequence. For example, one can match the 3' end of a mRNA sequence and capture (and quantify) alternative polyadenylation sites.

The input files must be previously compressed/collapsed using fastx_toolkit (http://hannonlab.cshl.edu/fastx_toolkit/) before using these nucleotide matching tools. An example for fastx_toolkit use: fastx_collapser -Q33 -i "input_filename.fq" -o "output_filename.col". 

There are two options for matching sequences: 1) Enter one sequence or a list of sequences to match within your library or 2) create a query file based on a genomic database from which to search. An example of such a file would be the drosophila melanogaster cDNA library in fasta format. Such databases that can be used to generate a query file can be obtained from: ftp://ftp.ensembl.org/pub/. As a specific example, drosophila cDNA in fasta format can be found here: ftp://ftp.ensembl.org/pub/release-74/fasta/drosophila_melanogaster/cdna/. (Note such data is downloaded compressed and needs to be uncompressed, such as by using the command: gunzip "file_name.fq.gz").

Creating a query file from a database for bulk search of upstream or downstream sequences is useful to avoid misattributing the origin of captured sequences. Because of recurring sequences throughout the genome and given deep sequencing libraries are composed of relatively short (50-300 bp) reads, it is important to review all potential origins of a captured sequence. For example, given a query/key sequence of 12 bp "GCA TAG GTG GTT, a captured adjacent sequence could result multiple attributations:

key: GCATAGGTGGTT
>Homo_sapiens_chr1.trna43-GlyGCC (159716980-159717050)  Gly (GCC) 71 bp  Sc: 69.02
CAGTGGTAGAATTCTTGCCTGCCACGCAGGAGGCCCAGGTTTGATTCCTGGCCCATGCA
>Homo_sapiens_chr1.trna43-GlyGCC (161450356-161450426)  Gly (GCC) 71 bp  Sc: 69.02
CAGTGGTAGAATTCTTGCCTGCCACGCAGGAGGCCCAGGTTTGATTCCTGGCCCATGCA

Multiple sequence attribution is fine, as long it is noted and whatever downstream results do not mis-attribute a sequence to an origin or genomic-type when there is also an ignored match elsewhere in the genome.  
