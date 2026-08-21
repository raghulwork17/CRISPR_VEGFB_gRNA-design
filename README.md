My first project as a genetic engineering student. With no wet lab access yet, I designed this as a fully dry-lab (in silico) CRISPR-Cas9 guide RNA design and validation pipeline, using the same computational steps a wet lab would need completed before ever touching a bench — target selection, guide design, on-/off-target scoring, and BLAST-based specificity validation.

🎯 Project Overview

Vascular Endothelial Growth Factor B (Vegfb, ENSMUSG00000024962) is involved in angiogenesis and vascular development, making it a useful practice target for learning CRISPR guide design. The goal of this project was to take a real gene from raw sequence to a shortlist of experimentally-ready sgRNAs, entirely computationally, and document the reasoning behind each choice.

🧬 Workflow
Target selection — Loaded the Vegfb (ENSMUSG00000024962) sequence map and defined a target region within Exon 1 (chr19: 6,959,841–6,965,019, mm39/GRCm39 assembly).
Guide (sgRNA) design — Generated candidate 20-nt guides across the target region, each paired with its PAM sequence and cut position, using the Doench, Fusi et al. (2016) scoring models for on-target activity.
Guide scoring — Compared On-Target and Off-Target scores across 304 candidate guides to prioritize efficient, specific guides (e.g., guide at cut position 23 scored 53.2 on-target / 75.4 off-target; guide at position 158 scored 59.2 on-target / 48.0 off-target).
Guide selection — Selected top candidate guides for assembly based on GC content, melting temperature, and combined score profile.
Off-target validation (BLAST) — Ran each selected 20-nt guide sequence through NCBI BLASTN against the mouse genome + transcriptome ("Mouse G+T") database to confirm specificity.
Confirmed 100% identity match to the intended target (Vegfb, transcript variants 1 & 2) with no strong unintended genomic hits.
Reviewed alignment hits across all mouse chromosomes to rule out significant off-target binding sites.
Genome context check — Cross-referenced the target locus on the NCBI Genome Data Viewer (GRCm39, Chr 19) to confirm gene structure, exon boundaries, and surrounding annotations.
🛠️ Tools & Databases Used
Tool	Purpose
Benchling (Molecular Biology suite)	Sequence mapping, CRISPR guide design & scoring, assembly
NCBI BLASTN	Off-target/specificity screening of guide sequences
NCBI Genome Data Viewer	Genomic locus visualization (GRCm39 / mm39 assembly)
Ensembl (release 116)	Gene/transcript annotation reference
📊 Key Results
Target locus: chr19:6,959,841–6,965,019 (GRCm39)
304 candidate guides evaluated across the target region
Final guides selected: cut positions 23 and 158, both validated via BLAST with 100% identity to Vegfb and no significant off-target matches
Guide at position 158: 20 nt, 85% GC content, melting temp 69.5°C
📁 Repository Contents
File	Description
benchling VEGFB.png	Sequence map of the Vegfb gene loaded in Benchling
guide 23 VEGFB.png	Guide design table showing candidate sgRNA at cut position 23
guide 158 VEGFB.png	Guide design table showing candidate sgRNA at cut position 158
23 primer BLAST.png	BLASTN results for the sgRNA at position 23
158 primer BLAST.png	BLASTN results for the sgRNA at position 158
23 transcripts.png	BLAST hits against mouse transcript database for guide 23
158 transcripts.png	BLAST hits against mouse transcript database for guide 158
genomic seq (23).png	BLAST hits against mouse genomic sequences for guide 23
158 genomic seq.png	BLAST hits against mouse genomic sequences for guide 158
data viewer.png	NCBI Genome Data Viewer view of the Vegfb locus (Chr 19, GRCm39)
VEGFB_CRISPR_gRNA_results.xlsx	Compiled guide scores and BLAST results
ncbi_dataset (2).zip	Downloaded NCBI dataset for the Vegfb locus
seqdump.txt, seqdump (1).txt	Raw sequence dumps used for BLAST queries
💡 Why Dry Lab

As a first-year student without current wet lab access, I chose to build the computational half of a CRISPR experiment end-to-end: the target analysis, guide design logic, and off-target safety checks that any real gene-editing experiment depends on before it ever reaches the bench. This project reflects my ability to work with genome browsers, sequence databases, and guide-scoring algorithms — the core bioinformatics skillset behind modern genetic engineering.

📚 Reference

Doench, J.G., Fusi, N., et al. (2016). Optimized sgRNA design to maximize activity and minimize off-target effects of CRISPR-Cas9. Nature Biotechnology.

First-year genetic engineering project — dry lab / in silico CRISPR sgRNA design.
