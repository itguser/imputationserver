## HLA Imputation Pipeline

In addition to intergenic SNPs, HLA imputation outputs five different types of markers: (1) binary marker for classical HLA alleles; (2) binary marker for the presence/absence of a specific amino acid residue; (3) HLA intragenic SNPs, and (4) binary markers for insertion/deletions, as described in the typical output below. The goal is to minimize prior assumption on which types of variations will be causal and test all types of variations simultaneously in an unbiased fashion. However, the users are always free to restrict analyses to specific marker subsets.

!!! note
    For binary encodings, A = Absent, T = Present.


| Type   |      Format      |  Example |
|----------|-------------|------|
| Classical HLA alleles |  HLA\_[GENE]\*[ALLELE]| HLA_A\*01:02 (two-field allele) <br> HLA_A\*02 (one-field allele) |
| HLA amino acids |  AA_[GENE]\_[AMINO ACID POSITION]\_[GENOMIC POSITION]\_[EXON]\_[RESIDUE] | AA_B_97_31324201_exon3_V (amino acid position 97 in HLA-B, genomic position 31324201 (GrCh37) in exon 3, residue = V (Val) ) |
| HLA intragenic SNPs |  SNPS_[GENE]\_[GENE POSITION]\_[GENOMIC POSITION]\_[EXON/INTRON] | SNPS_C_2666_31237183_intron6 (SNP at position 2666 of the gene body, genomic position 31237183 in intron 6)|
| Insertions/deletions |  INDEL_[TYPE]\_[GENE]\_[POSITION]| INDEL_AA_C_300x301_31237792 Indel between amino acids 300 and 301 in HLA-C, at genomic position 31237792) |

<br> 
We note that our current implementation of the reference panel is limited to the G-group resolution (DNA sequences that determine the exons 2 and 3 for class I and exon 2 for class II genes), and amino acid positions outside the binding groove were taken as its best approximation. When converting G-group alleles to the two-field resolution, we first approximated G-group alleles to their corresponding allele at the four-field resolution based on the ordered allele list in the distributed IPD-IMGT/HLA database (version 3.32.0). We explicitly include exonic information in the HLA-TAPAS output.


For more information about HLA imputation and help, please visit [https://github.com/immunogenomics/HLA-TAPAS](https://github.com/immunogenomics/HLA-TAPAS).
