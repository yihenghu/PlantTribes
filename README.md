# PlantTribes
## Overview
PlantTribes is a collection of automated modular sequence and gene family  analysis pipelines for plant evolutionary studies. It post-processes *de novo* assembly transcripts into putative coding sequences and their corresponding amino acid translations, estimates paralogous/orthologous pairwise synonymous/non-synonymous substitution rates for a set of gene sequences, classifies gene sequences into pre-computed orthologous plant gene family clusters, and builds gene family multiple sequence alignments and their corresponding phylogenies.

All questions and inquires should be addressed to our user email group: `PlantTribes-users@googlegroups.com`

In addition to this README file, you can consult the PlantTribes [manual](docs/PlantTribes.md) more detailed information.

## Installation
PlantTribes pipeline scripts have many external dependencies that need to be installed before the pipelines can be used. Executables of external dependencies should be set in the **_plantTribes.config_** file that is in the **_config_** subdirectory of the installation. 
#### Pipelines dependencies
- **AssemblyPostProcesser pipeline**:  
[ESTScan (version 2.1)](http://estscan.sourceforge.net/), [TransDecoder (version 2.0.1)](https://github.com/TransDecoder/TransDecoder/releases), and [GenomeTools (version 1.5.4)](http://genometools.org/).
- **GeneFamilyClassifier pipeline**:  
[BLASTP (NCBI BLAST version 2.2.29+)](http://blast.ncbi.nlm.nih.gov/Blast.cgi?PAGE_TYPE=BlastDocs&DOC_TYPE=Download), and [HMMScan (HMMER version 3.1b1)](http://hmmer.janelia.org/).
- **PhylogenomicsAnalysis pipeline**:  
[MAFFT (version 7.215 )](http://mafft.cbrc.jp/alignment/software/), [PASTA](https://github.com/smirarab/pasta), [trimAl (version 1.4.rev8)](http://trimal.cgenomics.org/), [RAxML (version 8.1.16)](http://sco.h-its.org/exelixis/web/software/raxml/index.html), and [FastTreeMP (version 2.1.7 SSE3)](http://meta.microbesonline.org/fasttree/).
- **KaKsAnalysis pipeline**:  
[BLASTP (NCBI BLAST version 2.2.29+)](http://blast.ncbi.nlm.nih.gov/Blast.cgi?PAGE_TYPE=BlastDocs&DOC_TYPE=Download), [PAML (version 4.8)](http://abacus.gene.ucl.ac.uk/software/paml.html#download), [EMMIX (version 1.0.1)](http://www.maths.uq.edu.au/~gjm/), and [mclust (version 4.4)](http://www.stat.washington.edu/mclust/).

#### PlantTribes scaffolds data 
- **22 plant genomes (Angiosperms clusters, version 1.0)**  
Download: http://fgp.huck.psu.edu/planttribes_data/22Gv1.0.tar.bz2
- **22 plant genomes (Angiosperms clusters, version 1.1)**  
Download: http://fgp.huck.psu.edu/planttribes_data/22Gv1.1.tar.bz2

#### Install PlantTribes
1. Open a terminal and change to the location where you would to keep PlantTribes. 
  - Example: `cd ~/softwares`
2. Clone the [PlantTribes](https://github.com/dePamphilis/PlantTribes) GitHub repository or download the [zip archive](https://github.com/dePamphilis/PlantTribes/archive/master.zip) and decompress it in your desired location.   
  - Examples: `git clone https://github.com/dePamphilis/PlantTribes.git` or `unzip https://github.com/dePamphilis/PlantTribes/archive/master.zip`
3. Download the scaffold data set(s) that you would like to use in the PlantTribes' **_data_** subdirectory and decompress them.
  - Examples: `cd PlantTribes/data`, followed by `tar -xjvf 22Gv1.1.tar.bz2`

## Using PlantTribes
The execulables for the PlantTribes pipelines are in the **_pipelines_** subdrectory of the installation. You can either add them to your PATH environment variable or execute directly from the PlantTribes installation.

- **AssemblyPostProcesser pipeline**: 
  - Display all usage options: 
    - `PlantTribes/pipelines/AssemblyPostProcesser`
  - Basic run using ESTScan prediction method:
    - `PlantTribes/pipelines/AssemblyPostProcesser  --transcripts transcripts.fasta --prediction_method estscan --score_matrices /path/to/score/matrices/Arabidopsis_thaliana.smat`
- **GeneFamilyClassifier pipeline**: 
  - Display all usage options: 
    - `PlantTribes/pipelines/GeneFamilyClassifier`
  - Basic run using 22Gv1.1 scaffolds, orthomcl clustering method, and blastp classifier:
    - `PlantTribes/pipelines/GeneFamilyClassifier --proteins proteins.fasta --scaffold 22Gv1.1 --method orthomcl --classifier blastp`
- **PhylogenomicsAnalysis pipeline**: 
  - Display all usage options: 
    - `PlantTribes/pipelines/PhylogenomicsAnalysis`
  - Basic run using 22Gv1.1 scaffolds, orthomcl clustering method, and raxml Phylogenetic trees inference method:
    - `PlantTribes/pipelines/PhylogenomicsAnalysis --orthogroup_faa geneFamilyClassification_dir/orthogroups_fasta --scaffold 22Gv1.1  --method orthomcl  --add_alignments  --tree_inference raxml`
- **KaKsAnalysis pipeline**
  - Coming soon!

Please consult the PlantTribes [manual](docs/PlantTribes.md) for a detailed description of all usage options for the pipelines.

## License
PlantTribes is distributed under the GNU GPL v3. For more information, see [license](LICENSE).
