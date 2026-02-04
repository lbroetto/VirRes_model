# VirRes_model: pHMM model for functional annotation of bacterial genomes

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18487266.svg)](https://doi.org/10.5281/zenodo.18487266)

This repository contains a custom pHMM (profile Hidden Markov Model) library designed for the annotation of bacterial protein families associated with virulence, antimicrobial resistance, pathogenicity, and persistence mechanisms. The model comprises 480 carefully selected pHMMs, each representing a distinct bacterial protein family with functional relevance to bacterial survival and adaptation mechanisms under stress in pathogenic and environmental bacteria. The profiles were sourced from well-curated public databases via the InterPro resource, including NCBIFAM, Pfam, PANTHER, SUPERFAMILY, and TIGRFAMs, ensuring high-quality, domain-specific signatures for sensitive and specific genome mining. These models enable deep, homology-based functional annotation of bacterial genomes, supporting genome mining and comparative genomics studies focused on microbial adaptation traits.

Rationale:
The pHMMs represent experimentally validated or phylogenetically conserved protein domains and full-length families involved in key bacterial survival and adaptation mechanisms, including efflux systems, toxin-antitoxin modules, stress response regulators, secretion systems, DNA repair, transcription factors, and metabolic adaptations linked to persistence and resistance.

Library was compiled by Leonardo Broetto (leonardo.broetto@arapiraca.ufal.br, Lbroetto@gmail.com)

# Contact
**Authors:** Leonardo Broetto
**Correspondence:** Lbroetto@gmail.com, leonardo.broetto@arapiraca.ufal.br
**Affiliation:** Núcleo de Pesquisa em Bioinformática e Filogenômica (NPBF), Universidade Federal de Alagoas, Brasil

---

## Source Databases:

All pHMMs were retrieved from curated public databases through InterPro:

| Source | Description |
| :--- | :--- |
| **NCBIFAM** | NCBIfam is a collection of protein families, featuring curated multiple sequence alignments,  hidden Markov models (HMMs) and annotation, which provides a tool for identifying functionally  related proteins based on sequence homology. NCBIfam is maintained at  the National Center for Biotechnology Information (Bethesda, MD). NCBIfam includes models from TIGRFAM,  another database of protein families developed at The Institute for Genomic Research,  then at the J. Craig Venter Institute (Rockville, MD, US). | 
| **Pfam** | Pfam is a large collection of multiple sequence alignments and hidden Markov models covering many common protein domains. Pfam is based at EMBL-EBI, Hinxton, UK. Since 2022, Pfam annotations are hosted by the InterPro website.|
| **PANTHER** |  PANTHER is a large collection of protein families that have been subdivided into functionally related subfamilies, using human expertise. These subfamilies model the divergence of specific functions within protein families, allowing more accurate association with function, as well as inference of amino acids important for functional specificity. Hidden Markov models (HMMs) are built for each family and subfamily for classifying additional protein sequences. PANTHER is based at University of Southern California, CA, US. |
| **SUPERFAMILY** |  SUPERFAMILY is a library of profile hidden Markov models that represent all proteins of known structure. The library is based on the SCOP classification of proteins: each model corresponds to a SCOP domain and aims to represent the entire SCOP superfamily that the domain belongs to. SUPERFAMILY is based at the MRC Laboratory of Molecular Biology, Cambridge, UK. |
| **TIGRFAM** | TIGRFAMs is a database of protein family definitions. Each entry features a seed alignment of trusted representative sequences, a hidden Markov model (HMM) built from that alignment, cutoff scores that let automated annotation pipelines decide which proteins are members, and annotations for transfer onto member proteins. Most TIGRFAMs models are designated equivalog, meaning they assign a specific name to proteins conserved in function from a common ancestral sequence. Models describing more functionally heterogeneous families are designated subfamily or domain, and assign less specific but more widely applicable annotations. |

## Repository Structure

| Directory/File | Description |
|----------------|-------------|
| `VirRes_model.hmm.gz` | Model consisting of custom pHMMs library |
| `LICENSE` | GNU GPLv3 license |
| `README.md` | This documentation |

## Repository Contents

`VirRes_pHMMs.hmm.gz` – a comprehensive pHMM library containing 480 profile Hidden Markov Models for bacterial protein families involved in diverse functional categories such as: toxin–antitoxin systems, multidrug efflux transporters, transcriptional regulators (e.g., MarR, TetR, MerR), stress response proteins, secretion system components, cell wall/envelope modification enzymes, DNA repair and recombination machinery and metabolic regulators linked to persistence.


## Usage Instructions
To use the library, you need to decompress the `.gz` file first. Open your terminal or command prompt and run:
$ gunzip VirRes_model.hmm.gz 

1. Prerequisites
Install HMMER 3.4 from http://hmmer.org/
HMMER Documentation: http://hmmer.org/documentation.html

2. Basic Search Command:
- For proteins identification  
$ hmmsearch --tblout output_file.txt -E 1e-03 --max VirRes_pHMMs.hmm your_proteome.faa

## For Reproducibility and Reuse:
Search command: the search was executed with stringent parameters to ensure high-confidence hits:  
$ hmmsearch --tblout <output_file.txt> -E 1e-03 --max <VirRes_pHMMs.hmm> <proteome.faa>

## Expected Output Format
- The tabular output includes: Target sequence identifier, Query pHMM identifier, E-value (statistical significance), Bit score (alignment quality), Domain boundaries, Alignment coordinate

## Statistical Validation Parameters
- Recommended search parameters:
E-value threshold: 1e-03 (statistical significance cutoff)
Database size correction: Applied via HMMER's built-in mechanisms
Multiple testing adjustment: Bonferroni correction for proteome-wide searches
Coverage requirement: ≥50% of pHMM model length

- Justification of Stringent Parameters:
The 1e-03 E-value threshold was selected based on:
Benchmarking studies showing optimal balance of sensitivity/specificity
Domain architecture conservation in resistance/virulence/persistence/ proteins
Reduction of false positives in large-scale proteome analyses
Comparability with established functional annotation pipelines

## Integration with Other Tools
These pHMM libraries are compatible with:
- AntiSMASH (for biosynthetic gene cluster analysis)
- Prokka (for prokaryotic genome annotation)
- Roary (for pangenome analysis)
- Custom Python/R scripts via Biopython/Bioconductor

## Applications
- Comparative genomics: Identify adaptive traits across bacterial isolates
- Pathogenomics: Characterize virulence potential in clinical isolates
- Metagenomics: Screen for resistance/virulence genes in complex communities
- Functional annotation: Enhance genome annotations with curated protein families

# License and Citation
### If you use this functional annotation model in your research, please cite:

- Broetto, L. (2026). VirRes_model: pHMM model for functional annotation of bacterial genomes (v1.0.0) [Computer software]. Zenodo. https://doi.org/10.5281/zenodo.18487266

- HMMER Software: Eddy, S. R. (2011). Accelerated Profile HMM Searches. PLoS Computational Biology, 7(10), e1002195. https://doi.org/10.1371/journal.pcbi.1002195

or

```bibtex
@software{broetto_phmm_library_2026,
  author       = {Leonardo Broetto},
  title        = {{VirRes_model: pHMM model for functional annotation of bacterial genomes},
  month        = jan,
  year         = 2026,
  publisher    = {Zenodo},
  version      = {v1.0.0},
  doi          = {10.5281/zenodo.18487266},
  url          = {https://doi.org/10.5281/zenodo.18487266}
}
```

This project is licensed under the **GNU General Public License v3.0**.

### Terms for Academic/Research Use:
- Free to use, study, and modify
- Must distribute derivatives under GPLv3
- Must provide source code when distributing binaries
- Must preserve copyright notices and license text

### Terms for Commercial Use:
For commercial applications or proprietary integration, please contact the author (Lbroetto@gmail.com, leonardo.broetto@arapiraca.ufal.br) to discuss alternative licensing options.

**Full license text:** [LICENSE](LICENSE)

### Copyright and Licensing
- **Copyright Holder:** Leonardo Broetto  
- **License:** GNU General Public License v3.0  
- **Year:** 2026

### Research Attribution
The computational methodologies implemented in this software were developed as part of research activities conducted by Leonardo Broetto. Associated research work is linked to Universidade Federal de Alagoas.

### Usage Terms
- **Academic/Research Use:** Permitted under GPLv3 with mandatory citation
- **Commercial Use:** Requires alternative licensing (contact author)
- **Derivative Works:** Must be released under GPLv3

### Contact for Licensing
Leonardo Broetto  
Lbroetto@gmail.com, leonardo.broetto@arapiraca.ufal.br
(Associated with Universidade Federal de Alagoas)
