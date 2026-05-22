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
3. Unicycler hybrid assembly
   OR Flye + polishing (backup)
4. Check circular contigs + coverage
