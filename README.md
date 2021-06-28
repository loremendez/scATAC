# scATAC
A collection of Notebooks to analyse scATAC-seq data. 


<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
-->

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary><h2 style="display: inline-block">Table of Contents</h2></summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#references">References</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>


<!-- ABOUT THE PROJECT -->
## About The Project

This is a collection of Notebooks made to analyse scATAC-seq data. They are based on the vignettes from different R-algorithms: [Signac](https://satijalab.org/signac/), [Seurat](https://satijalab.org/seurat/), [Cicero](https://cole-trapnell-lab.github.io/cicero-release/docs_m3/) and [Monocle3](https://cole-trapnell-lab.github.io/monocle3/docs/introduction/).

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
<dd>Overrepresented motifs in a cluster of cells in comparison to another cluster of cells. Computes motif activities using <a href=https://www.nature.com/articles/nmeth.4401>ChromVAR</a>.</dd>
<dt>5. Transcription Factor Footprints</dt>
<dd>Finds TF footprints. *Similarly to nucleosomes, bound TFs hinder cleavage of DNA, resulting in defined regions of decreased signal strength within larger regions of high signal-known as footprints*, <a href=https://www.nature.com/articles/s41467-020-18035-1>Bentsen et. al, 2020</a>.</dd>
</dl>

### Built With

* [Anaconda 4.10.1](https://www.anaconda.com/)
* [R 4.0.2](https://www.r-project.org/)

<!-- GETTING STARTED -->
## Getting Started

Install the environment and follow the Notebooks.

### Prerequisites

Anaconda. If you haven't installed Anaconda yet, you can follow the next tutorial: [Anaconda Installation.](https://docs.anaconda.com/anaconda/install/)

### Installation

1. Clone the repo
   ```sh
   git clone https://github.com/loremendez/Gemstones.git
   ```
2. Install the environment <br>
    1. Create and activate the environment
        ```sh
        conda create -n atac_env r-base=4.0.2
        conda activate atac_env
        ```
    2. Install Signac, genome assembly and gene annotation packages following the [instructions on the website](https://satijalab.org/signac/articles/install.html).
    3. Install additional packages in R console. Important: do not update any packages. 
       ```sh
       if (!requireNamespace("remotes", quietly = TRUE)) {install.packages("remotes")}
       remotes::install_github('satijalab/seurat-wrappers')
       remotes::install_github("mojaveazure/seurat-disk")
       BiocManager::install(c("motifmatchr", "TFBSTools", "JASPAR2020", "chromVAR"))
       ``` 
    5. Install Monocle3 following the [instructions](https://cole-trapnell-lab.github.io/monocle3/docs/installation/) or: 
        ```sh
        conda install -c bioconda r-monocle3
        ``` 
    6. Install Cicero in R console.
       ```sh
       remotes::install_github("cole-trapnell-lab/cicero-release", ref = "monocle3")
       ``` 
    8. Install jupyter-lab.
       ```sh
       conda install jupyterlab
       ``` 
    10. Create a Kernel from R console (optional).
       ```sh
       install.packages('IRkernel')
       IRkernel::installspec(name='atac_seq', displayname='atac_seq')
       ``` 

<!-- USAGE EXAMPLES -->
## Usage

Activate the environment, open Jupyter-lab and the notebooks in order.
```sh
jupyter-lab
```

<!-- References -->
## References
<a id="1">[1]</a>
[Signac](https://satijalab.org/signac/).
[Seurat](https://satijalab.org/seurat/)
[Cicero](https://cole-trapnell-lab.github.io/cicero-release/docs_m3/)
[Monocle3](https://cole-trapnell-lab.github.io/monocle3/docs/introduction/)


<!-- CONTACT -->
## Contact

Lorena Mendez - [LinkedIn](https://www.linkedin.com/in/lorena-mendezg/?originalSubdomain=de) - lorena.mendez@tum.de

Take a look into my [other](https://github.com/loremendez) projects!
