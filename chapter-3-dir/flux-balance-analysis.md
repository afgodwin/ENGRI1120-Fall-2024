# Introduction to Flux Balance Analysis and Metabolic Engineering

## Introduction

Metabolic engineering is the practice of optimizing genetic and regulatory processes within cells to increase the cell's production of a desired small molecule or macromolecle product, e.g., proteins of interest and is a key component of Biotechnology. There are (roughly) two categories of Biotechnology, industrial biotechnology, and medical biotechnology. Metabolic engineering plays a vital role in both sectors. Industrial biotechnology is typically consumer-focused, e.g., components of consumer products such as detergents, food products, and small-molecule chemical feedstocks. On the other hand, medical biotechnology develops molecules for human (and animal) health applications, e.g., antibodies, therapeutic proteins, vaccines, etc. 

The overall objective as a metabolic engineer is to maximize the `performance` of a metabolic network, e.g., develop a system that produces a desired product with the highest possible yield, or at the maximum possible rate, etc. Toward this objective, metabolic engineers manipulate the biochemical networks cells use to convert raw materials into molecules necessary for the cell's survival. Metabolic engineering specifically seeks to:

1. Mathematically model biochemical networks, calculate the yield (product divided by substrate) of valuable products, and identify parts of the network that constrain the production of these products of interest. 
1. Use genetic engineering techniques to modify the biochemical network to relieve constraints limiting production. Metabolic engineers can then model the modified network to calculate the new product yield and identify new constraints (back to 1).

Resources for metabolic engineering:

* [Bailey JE. Toward a science of metabolic engineering. Science. 1991 Jun 21;252(5013):1668-75. doi: 10.1126/science.2047876. PMID: 2047876.](https://pubmed.ncbi.nlm.nih.gov/2047876/)

* [Stephanopoulos G, Vallino JJ. Network rigidity and metabolic engineering in metabolite overproduction. Science. 1991 Jun 21;252(5013):1675-81. doi: 10.1126/science.1904627. PMID: 1904627.](https://pubmed.ncbi.nlm.nih.gov/1904627/)

Resources for biochemical network information

* [Kanehisa M, Goto S. KEGG: kyoto encyclopedia of genes and genomes. Nucleic Acids Res. 2000 Jan 1;28(1):27-30. doi: 10.1093/nar/28.1.27. PMID: 10592173; PMCID: PMC102409.](https://www.genome.jp/kegg/)

* [Karp, Peter D et al. "The BioCyc collection of microbial genomes and metabolic pathways." Briefings in bioinformatics vol. 20,4 (2019): 1085-1093. doi:10.1093/bib/bbx085](https://pubmed.ncbi.nlm.nih.gov/29447345/)

* [Gama-Castro, Socorro et al. "RegulonDB version 9.0: high-level integration of gene regulation, coexpression, motif clustering and beyond." Nucleic acids research vol. 44,D1 (2016): D133-43. doi:10.1093/nar/gkv1156](https://pubmed.ncbi.nlm.nih.gov/26527724/)

---

## Theory of Flux Balance Analysis 
Flux balance analysis (FBA) is a mathematical modeling and analysis approach that estimates the _intracellular_ or _cell-free_ reaction rate (metabolic flux) of carbon and energy throughout a metabolic network (units: $\star$mol/gDW-time or $\star$mol/L-time for cell-free networks). 
However, flux balance analysis is a general tool that can be used to estimate _flows_ through many different types of networks and graphs, e.g., social graphs, communication networks, or other types of problems that can be represented as a network of graphs.  Flux balance analysis is arguably the most widely used computational tool in metabolic engineering. However, there are alternatives to FBA, such as metabolic flux analysis (MFA), but these alternatives vary more in the solution approach than the structure of the estimation problem. 

Let's look at the following reference to understand better the different components of a flux balance analysis problem:

* [Orth, J., Thiele, I. & Palsson, B. What is flux balance analysis?. Nat Biotechnol 28, 245–248 (2010). https://doi.org/10.1038/nbt.1614](https://www.ncbi.nlm.nih.gov/labs/pmc/articles/PMC3108565/)

Computational tools for working with flux balance analysis models:

* [Heirendt, Laurent et al. "Creation and analysis of biochemical constraint-based models using the COBRA Toolbox v.3.0." Nature protocols vol. 14,3 (2019): 639-702. doi:10.1038/s41596-018-0098-2](https://pubmed.ncbi.nlm.nih.gov/30787451/)

### Flux balance analysis problem structure
The FBA problem is typically encoded as a linear programming (LP) problem of the form:

$$\max_{v}\sum_{i=1}^{\mathcal{R}}c_{i}v_{i}$$

subject to the constraints:

$$\begin{eqnarray}
\mathbf{S}\mathbf{v} &=& \mathbf{0}\\
\mathcal{L}\leq&\mathbf{v}&\leq\mathcal{U}\\
\dots &=& \dots
\end{eqnarray}$$

where $\mathbf{S}$ denotes the stoichiometric matrix, $c_{i}$ denote the objective coefficients, 
$\mathbf{v}$ denotes the metabolic flux (the unknown that we are trying to estimate), and 
$\mathcal{L}$ ($\mathcal{U}$) denote the permissible lower (upper) bounds on the _unkown_ metabolic flux. The first set of constraints enforces conservation of mass, while the second imparts thermodynamic and kinetic information into the calculation. Finally, there are potentially other types of constraints (both linear and nonlinear) used in this type of problem (we will not cover these here, but these additional constraints may be important in specific applications that culd be encountered in practice).

#### Formulation and properties of the stoichiometric matrix $S$
The stoichiometric matrix $\mathbf{S}$ is a $\mathcal{M}\times\mathcal{R}$ array holding the 
coefficients $\sigma_{ij}$; each row of $\mathbf{S}$ describes a metabolite, while each column represents a possible chemical reaction. Thus, the stoichiometric matrix is a _digital_ representation of the biochemical capabilities of a metabolic network. 

When formulating the stoichiometric matrix, what should be included to describe known or unknown desired phenomena? For example, suppose we are interested in producing product $P$ or making sense of a metabolic data set. Should every possible reaction or just some _subset_ of all possible reactions be included in the stoichiometric matrix? The practical significance of this question is two-fold:

* Fewer material balances are better when describing the behavior of a metabolic network, and
* Fewer chemical reactions (fluxes) result in less uncertainty when estimating the kinetic rates $\hat{r}_{j}$ (bounds) or other constraints.

#### Convex pathway analysis

Convex pathway analysis is an approach to catalog all possible steady-state pathways through a reaction network. In particular, convex decomposition approaches posit that any potential steady-state flux can be represented as the [convex combination](https://en.wikipedia.org/wiki/Convex_combination) of a set of [convex independent](https://en.wikipedia.org/wiki/Convex_position) basis vectors called _extreme pathways_ $\mathbf{P}_{i}$:

$$\mathbf{v} = \sum_{i=1}^{\mathcal{P}}\alpha_{i}\mathbf{P}_{i}$$

where $\mathcal{P}$ denotes the number of basis pathways, and $\mathbf{P}_{i}$ denotes the $\mathcal{R}\times{1}$ extreme pathway basis vector. The term(s) $\alpha_{i}\geq{0}$ denotes the weight of extreme pathway $i$.

Extreme pathways are _very difficult_ to compute but can give super exciting insights into the operation and capabilities of a metabolic network.

Convex pathway analysis approaches:

* [Bell SL, Palsson BØ. Expa: a program for calculating extreme pathways in biochemical reaction networks. Bioinformatics. 2005 Apr 15;21(8):1739-40. doi: 10.1093/bioinformatics/bti228. Epub 2004 Dec 21. PMID: 15613397.](https://pubmed.ncbi.nlm.nih.gov/15613397/)

* [Trinh CT, Wlaschin A, Srienc F. Elementary mode analysis: a useful metabolic pathway analysis tool for characterizing cellular metabolism. Appl Microbiol Biotechnol. 2009;81(5):813-826. doi:10.1007/s00253-008-1770-1](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2909134/)

* [Bordbar A, Nagarajan H, Lewis NE, et al. Minimal metabolic pathway structure is consistent with associated biomolecular interactions. Mol Syst Biol. 2014;10(7):737. Published 2014 Jul 1. doi:10.15252/msb.20145243](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4299494/)

* [Song HS, Goldberg N, Mahajan A, Ramkrishna D. Sequential computation of elementary modes and minimal cut sets in genome-scale metabolic networks using alternate integer linear programming. Bioinformatics. 2017 Aug 1;33(15):2345-2353. doi: 10.1093/bioinformatics/btx171. PMID: 28369193.](https://pubmed.ncbi.nlm.nih.gov/28369193/)


# Analysis of Biochemical reaction networks
Fill me in.

## Summary
Fill me in.