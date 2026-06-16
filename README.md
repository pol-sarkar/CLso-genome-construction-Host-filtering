# Liberibacter NGS Project: Genome Reconstruction, Annotation, and Comparative Genomics

This repository contains bioinformatics workflows for whole-genome reconstruction and comparative genomics of *“Candidatus Liberibacter”* spp. from Illumina and Nanopore sequencing data. The pipeline is designed for low-titer bacterial pathogens recovered from host-associated samples.

---

## Workflow Overview

The analytical workflow follows a reference-guided genome reconstruction and downstream comparative genomics strategy:

RAW READS  
↓  
Host filtering (removal of plant/insect reads)  
↓  
Read mapping to reference genome (BWA / minimap2)  
↓  
Variant calling (BCFtools / GATK) → VCF generation  
↓  
Consensus genome reconstruction (bcftools consensus)  
↓  
Reference-guided consensus FASTA generation (final genome sequences)  
↓  
Genome annotation (Prokka)  
↓  
Pan-genome analysis (Roary)  
↓  
Lineage-specific gene enrichment analysis (Fisher’s exact test + FDR correction)

---

## Key Methodological Notes

- Final genome sequences are reference-guided consensus assemblies reconstructed from read alignments to a reference genome.
- This approach was used due to low pathogen titer, uneven sequencing depth, and limitations of de novo assembly in several samples.
- All genomes were reconstructed using a consistent reference framework to ensure comparability across samples.

---

## Outputs

### Consensus Genomes
- `*.fasta` → reference-guided consensus genome sequences per sample

### Genome Annotation (Prokka)
- `*.gff` → gene feature annotations  
- `*.gbk` → GenBank formatted annotations  
- `*.faa` → predicted protein sequences  
- `*.ffn` → nucleotide CDS sequences  
- `*.fna` → annotated genome FASTA  
- `*.tsv` → annotation summary tables  

### Comparative Genomics
- Gene presence/absence matrix (Roary)
- Pan-genome clustering
- Lineage-specific gene enrichment results

---

## Downstream Analyses

- Pan-genome construction using Roary
- Gene presence/absence comparisons across lineages
- Fisher’s exact test for lineage-specific gene enrichment
- Benjamini–Hochberg FDR correction for multiple testing

---

## Software Used

- BWA / minimap2  
- Samtools  
- BCFtools / GATK  
- Prokka  
- Roary  
- Python (pandas, numpy, scipy)

---

## Directory Structure

FINAL/NCBI_submission/  
├── assemblies/    # consensus genome FASTA files  
├── annotations/   # Prokka annotation outputs  
├── vcfs/          # variant call files (optional)  
├── metadata/      # sample metadata tables  

---

## Notes

This repository contains reference-guided genome reconstructions rather than de novo assemblies. It is optimized for:

- Low-abundance bacterial pathogen detection  
- Host-contaminated sequencing datasets  
- Comparative genomics across closely related strains  

---

## Citation

If you use this workflow, please cite or acknowledge accordingly.

## Hybrid Genome Assembly (Exploratory)

In addition to reference-guided consensus reconstruction, de novo hybrid genome assemblies were generated using Unicycler from host-filtered Illumina and Nanopore reads.

### Input Data
- Host-filtered Illumina paired-end reads
- Host-filtered Nanopore long reads

### Assembly Tool
- Unicycler (hybrid assembly mode)

### Output
- `hybrid_assemblies/*/assembly.fasta`

---

## Interpretation

Hybrid assemblies were generated to evaluate the feasibility of de novo genome reconstruction. However, assembly completeness varied across samples due to:

- low Illumina sequencing depth in several samples
- uneven long-read coverage after host filtering
- high host-to-pathogen read ratio typical of Liberibacter datasets

As a result, hybrid assemblies were not used for downstream comparative genomics or NCBI submission. Instead, reference-guided consensus genomes were used as the primary dataset.

---

## Role in Study

Hybrid assemblies serve as:
- validation of genome structure where successful
- exploratory de novo comparison to reference-guided genomes
- assessment of assembly feasibility under low-titer conditions
