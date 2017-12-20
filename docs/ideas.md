# Ideas

Collection of ideas regarding the workflow implementation.

## Notes

There already exists a quality assesment pipeline, https://github.com/Teichlab/celloline, but it is only executable on an amazon cluster. **I think that we can learn a lot from what they implemented there!**

## Pipeline design ideas

The core upstream module of the pipeline shall be https://github.com/CGATOxford/UMI-tools.

Here is a hypothetical upstream workflow:

| Step | Tool | Inputs | Output |
| -------- | -------- | -------- | -------- |
| Quality Control of FASTQs | FASTQC | R1 + R2 FASTQs | HTML Report
| Quality Control - Detect Outliers (Gini Index) | http://www.morgridge.net/SinQC.html | R1 FASTQ | ugly report (PDFs + Tables)
| Find Cell barcode whitelist (OPTIONAL) | umi_tools whitelist | R1 FASTQ | whitelist.txt |
| Extract CB/UMIs and filter CBs | umi_tools extract | R1 + R2 FASTQs + whitelist.txt | extracted FASTQs |
| Remove PCR duplicates | umi_tools dedup | | |
| Map reads | STAR, Kallisto, Salmon | extracted FASTQs | BAM |
| Assign reads to genes | featureCounts, Kallisto? | BAM + transcriptome GTF | BAM
| Count unique reads per genes per cell | umi_tools count | BAM | Counts.txt

We have to add a http://multiqc.info/ report for every step where it is necessary.
**We are still lacking some trimming of the reads, if the quality is too bad (TrimGalore!, Cutadapt, Trimmomatic). What else are we missing?**

## Downstream

There are various a GUI tools for downstream analysis: https://github.com/diazlab/scell, http://ilab.hawaii.edu:8111/?_state_id_=a9000d20618de32e&tab=info

**The major question I have here is: Which parts of the downstream analysis can we automate?**

Quality Check of the cells

Normalization

Dimension Reduction (PCA, MDS, t-SNE, Diffusion Map, Graph Spatialization)

Differential Expression (DESeq2, EDGE_R)

### Advanced

Subpopulation Detection

Pseudo-Time Construction

