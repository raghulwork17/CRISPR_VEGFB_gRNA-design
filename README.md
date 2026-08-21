# CRISPR sgRNA Design for VEGFB Mus Musculus First Year Project

I'm a first-year genetic engineering student, and since I don't have wet lab access yet, I wanted to work through what a real CRISPR experiment looks like on the computational side. This project is me designing and validating guide RNAs for the mouse *Vegfb* gene (ENSMUSG00000024962) — everything you'd normally do before you ever pick up a pipette.

## What this is

Vegfb is involved in blood vessel formation, and it seemed like a solid gene to practice on. I picked a target region in Exon 1, generated a batch of candidate sgRNAs, scored them for on-target efficiency and off-target risk, picked two good candidates, and then ran them through BLAST to actually check they were specific to the gene and not going to cut somewhere else in the genome.

## How I did it

1. **Loaded the gene** in Benchling and picked a target region in Exon 1 (chr19: 6,959,841–6,965,019 on GRCm39/mm39).
2. **Generated guides** — Benchling designs 20-nt candidate sgRNAs across the region and pairs each with its PAM and cut site. Scoring is based on the Doench/Fusi 2016 model.
3. **Compared scores** across 304 candidate guides (on-target vs off-target) to shortlist the better ones.
4. **Picked two guides** — cut position 23 (on-target 53.2, off-target 75.4) and cut position 158 (on-target 59.2, off-target 48.0) — based on scores, GC%, and melting temp.
5. **Ran BLASTN** on both guide sequences against the mouse genome + transcriptome to double check specificity. Both came back 100% identity to Vegfb with nothing concerning elsewhere.
6. **Checked the locus** in NCBI Genome Data Viewer just to confirm the gene structure and exon boundaries lined up with what Benchling showed.

## Tools

- **Benchling** – sequence map, guide design, scoring
- **NCBI BLAST** – off-target checking
- **NCBI Genome Data Viewer** – genome context
- **Ensembl** (release 116) – annotation reference

## Results

- Target region: chr19:6,959,841–6,965,019 (GRCm39)
- 304 guides scored, 2 selected (cut positions 23 & 158)
- Both guides confirmed specific to Vegfb via BLAST, no significant off-target hits
- Guide 158: 20nt, 85% GC, Tm 69.5°C

## Files in this repo

| File | What it is |
|---|---|
| `benchling VEGFB.png` | Vegfb sequence map in Benchling |
| `guide 23 VEGFB.png` | Guide design table, cut position 23 |
| `guide 158 VEGFB.png` | Guide design table, cut position 158 |
| `23 primer BLAST.png` | BLAST results, guide 23 |
| `158 primer BLAST.png` | BLAST results, guide 158 |
| `23 transcripts.png` | BLAST hits vs mouse transcripts, guide 23 |
| `158 transcripts.png` | BLAST hits vs mouse transcripts, guide 158 |
| `genomic seq (23).png` | BLAST hits vs mouse genome, guide 23 |
| `158 genomic seq.png` | BLAST hits vs mouse genome, guide 158 |
| `data viewer.png` | Vegfb locus in NCBI Genome Data Viewer |
| `VEGFB_CRISPR_gRNA_results.xlsx` | Compiled scores + BLAST results |
| `ncbi_dataset (2).zip` | NCBI dataset download for the locus |
| `seqdump.txt`, `seqdump (1).txt` | Raw sequences used for BLAST |

## Why dry lab

I don't have bench access yet as a first-year, so this was my way of still getting hands-on with a real CRISPR workflow — figuring out guide design logic, reading scoring output, and running the off-target checks a wet lab would need before ordering primers.

## Reference

Doench, J.G., Fusi, N., et al. (2016). *Optimized sgRNA design to maximize activity and minimize off-target effects of CRISPR-Cas9.* Nature Biotechnology.
