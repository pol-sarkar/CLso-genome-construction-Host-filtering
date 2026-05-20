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
