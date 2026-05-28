# CLso-genome-construction-Host-filtering
Low abundance CLso genome construction-Host filtering
FASTQ (trimmed reads)
        ↓
BWA mapping to host genomes (plant + insect)
        ↓
samtools view -f 12  (keep unmapped pairs)
        ↓
host-free FASTQ
        ↓
assembly / CLso analysis


1. Host-filter Illumina (DONE ✔)
2. Host-filter ONT (NOW DO THIS ✔)
3.Option 1 (BEST): Hybrid reference-guided polishing

Use:

your Illumina reads
your cleaned ONT reads
CLso reference

Pipeline:

map ONT + Illumina to reference
generate consensus
polish with Illumina
recover variants/haplotypes

This will give you:

nearly complete genome
publication-quality SNP calls
strain comparison across samples

and is MUCH more realistic than forcing Flye.

Important conclusion

You do NOT have enough ONT depth for:

single-contig de novo assembly
circular chromosome reconstruction

But you DO have enough for:

reference-guided complete genome reconstruction.
