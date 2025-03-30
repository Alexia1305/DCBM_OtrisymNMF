# Degree-Corrected Block Model: A New Approach and Efficient Initialization for Inference


This **Python** code contains the tests conducted for a paper submission for **GRETSI 25**.
We use **OtrisymNMF** as a **degree corrected block model (DCBM)** to detect communities in several benchmark networks, including the LFR benchmark. 
We also demonstrate that our initialization, based on separable NMF, significantly improves the results of classical inference methods for the **DCBM of Karrer and Newman**.

All the tools for OtrisymNMF are available in the Python package **OtrisymNMF**. For Karrer and Newman's DCBM and inference methods, we used the **pysbm** package.
The Karate notebook compares the use of OtrisymNMF and Karrer and Newman's DCBM on the **Karate Club network**.
The Tests folder contains experiments demonstrating that the SVCA initialization significantly improves the results of inference methods.

# Reproducing the Results

To reproduce the results:

- **LFR Graphs Tests (Figure 2):** Run the script located at `Tests/LFR_benchmark.py` and select the desired value for $mu.
- **Karate Club (Figure 3):** Open and run the notebook `Karate.ipynb`.
- **Scotland Corporate Interlock Network Tests:** Execute the script `Tests/Scotland_test.py`.


## OtrisymNMF
This package provides implementations of the **Orthogonal Symmetric Nonnegative Matrix Tri-Factorization** (OtrisymNMF) algorithm  as proposed in the paper:

**Dache, Alexandra, Arnaud Vandaele, and Nicolas Gillis.**  
*"Orthogonal Symmetric Nonnegative Matrix Tri-Factorization."*  
IEEE International Workshop on Machine Learning for Signal Processing (MLSP), 2024.  
Institute of Electrical and Electronics Engineers (IEEE), United States.

The algorithm aims to solve the following optimization problem:

\[
\min_{W \geq 0, S \geq 0} \|X - WSW^T\|_F^2 \quad \text{s.t.} \quad W^TW = I
\]

Where:
- **X** is a given symmetric nonnegative matrix (e.g., adjacency matrix of an undirected graph).
- **W** is a matrix representing the assignment of elements to **r** communities.
- **S** is a central matrix describing interactions between communities.

The **OtrisymNMF** package also includes the **SVCA** algorithm to initialize the inference.



## pysbm
A Python Package for Stochastic Block Model Inference by 

Funke T, Becker T (2019) Stochastic block models: A comparison of variants and inference methods. 
PLoS ONE 14(4): e0215296. https://doi.org/10.1371/journal.pone.0215296

They implement the stochastic block model variants from the following publications:

- Karrer B, Newman ME. Stochastic blockmodels and community structure in networks. Physical Review E. 2011; 83(1):016107. https://doi.org/10.1103/PhysRevE.83.016107 
- Peixoto TP. Entropy of stochastic blockmodel ensembles. Physical Review E. 2012; 85(5):056122. https://doi.org/10.1103/PhysRevE.85.056122
- Côme E, Latouche P. Model selection and clustering in stochastic block models based on the exact inte- grated complete data likelihood. Statistical Modelling. 2015; 15(6):564–589. https://doi.org/10.1177/1471082X15577017
- Newman MEJ, Reinert G. Estimating the Number of Communities in a Network. Phys Rev Lett. 2016; 117:078301. https://doi.org/10.1103/PhysRevLett.117.078301 PMID: 27564002
- Peixoto TP. Hierarchical block structures and high-resolution model selection in large networks. Physi- cal Review X. 2014; 4(1):011047. https://doi.org/10.1103/PhysRevX.4.011047
- Peixoto TP. Nonparametric Bayesian inference of the microcanonical stochastic block model. Physical
Review E. 2017; 95(1):012317. https://doi.org/10.1103/PhysRevE.95.012317 PMID: 28208453
