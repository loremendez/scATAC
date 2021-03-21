# scATAC
Analysis of scATAC-seq data.

## Content

This is a collection of notebooks based on scATAC-seq vignettes from [Signac](https://satijalab.org/signac/), [Seurat](https://satijalab.org/seurat/), [Cicero](https://cole-trapnell-lab.github.io/cicero-release/docs_m3/) and [Monocle3](https://cole-trapnell-lab.github.io/monocle3/docs/introduction/).

<dl>
<dt>0. Pre-analysis</dt>
<dd>Quality checks, filters, dimensional reduction and gene activity quantification.</dd>
<dt>1. Data Integration</dt>
<dd>Add scRNA-seq information and compute co-embedding.</dd>
<dt>2. Coaccessibility</dt>
<dd>Scores co-accessibility between peaks to predict cis-regulatory interactions, such as those between promoters and enhancers.</dd>
<dt>2.1 Trajectories</dt>
<dd>Tries to infer trajectories using chromatin accessibility to compute pseudotime. (Under review)</dd>
<dt>3. Differentially Accessible Peaks</dt>
<dd>Differences between chromatin accessibility in groups or clusters of cells.</dd>
<dt>4. Motif Analysis</dt>
<dd>Overrepresented motifs in a cluster of cells in comparison to another cluster of cells. Computes motif activities using [ChromVAR](https://www.nature.com/articles/nmeth.4401).</dd>
<dt>5. Transcription Factor Footprints</dt>
<dd>Finds TF footprints. *Similarly to nucleosomes, bound TFs hinder cleavage of DNA, resulting in defined regions of decreased signal strength within larger regions of high signal-known as footprints*, [Bentsen et. al, 2020](https://www.nature.com/articles/s41467-020-18035-1).</dd>
</dl>

<!-- GETTING STARTED -->
## Environment

First, we need to set up the environment.

1. Set up an environment with R 4.0.2.: <br>
`conda create -n atac_env r-base=4.0.2`<br>
`conda activate atac_env`<br>

For the next steps do not update any of the suggested packages at the end of each installation.

2. Install Signac, genome assembly and gene annotation packages following the [instructions on the website](https://satijalab.org/signac/articles/install.html).<br>

3. Install additional Seurat packages in R console:<br>
`if (!requireNamespace("remotes", quietly = TRUE)) {
  install.packages("remotes")
}`<br>
`remotes::install_github('satijalab/seurat-wrappers')`<br>
`remotes::install_github("mojaveazure/seurat-disk")`<br>

4. Install packages for motif and transcription factor analysis:
`BiocManager::install(c("motifmatchr", "TFBSTools", "JASPAR2020", "chromVAR"))`<br>

For this step, agree to downgrade packages if necessary:

5. Install monocle3 for trajectory analysis:
with conda: `conda install -c bioconda r-monocle3`
or follow the [instructions on the website](https://cole-trapnell-lab.github.io/monocle3/docs/installation/).

6. Install Cicero for co-accessibility analysis:<br>
`remotes::install_github("cole-trapnell-lab/cicero-release", ref = "monocle3")`<br>
