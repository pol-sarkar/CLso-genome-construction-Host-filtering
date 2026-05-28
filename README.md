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

NOT have enough ONT depth for:

single-contig de novo assembly
circular chromosome reconstruction

But you DO have enough for:

reference-guided complete genome reconstruction.

Flye de novo alone → failed (fragmented, contamination, low coverage)
Host filtering alone → insufficient enrichment

Final successful strategy:

reference-guided read enrichment + consensus reconstruction

To overcome low pathogen abundance and host contamination, we implemented a combined reference-guided enrichment and hybrid sequencing strategy, using long-read nanopore and short-read Illumina data to reconstruct high-quality CLso genomes. A final consensus genome (~1.27 Mb) was generated through reference-based read mapping and variant-aware consensus calling, followed by structural and functional annotation.
