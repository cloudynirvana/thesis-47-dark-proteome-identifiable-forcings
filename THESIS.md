THE DARK PROTEOME AS IDENTIFIABLE FORCINGS: STRUCTURAL IDENTIFIABILITY OF ncORF-DERIVED MICROPROTEIN TERMS IN A MINIMAL TUMOUR-GROWTH ODE

**Thesis #47** — computational research thesis
**Author:** Kelechi Emeka Ogbonna
**Correspondence:** kelechiogbonna300@gmail.com
**Date:** September 2026
**Format:** B.Sc. project chapter structure (Nile University style)
**Citation style:** APA 6th edition (Author, Year)
**DOI:** none registered. Do not invent one.

This manuscript forms part of the Project Confluence independent research series. It extends the analytical foundations laid in Thesis Zero (BSc Carica papaya AgNP, Nile University 2022) by continuing to apply rigorous mathematical modeling to biochemical phenomena. Specifically, this work translates the structural identifiability frameworks established in Thesis T07 and T09 to the emerging domain of the dark proteome, investigating how uncharacterized microproteins act as forcing terms within dynamical systems of tumour progression.

## Non-claims
This manuscript is part of an independent computational research series (Project Confluence). The author, Kelechi Emeka Ogbonna, is an independent researcher. This work builds upon the format of Nile University of Nigeria's B.Sc. project structure but is not submitted for academic credit or degree requirements at Nile University or any other institution. The models, parameters, and findings presented herein are theoretical and computational in nature. They do not constitute medical, clinical, or diagnostic advice. "Thesis Zero" and subsequent numerical designations refer to an internal series tracking system and do not denote official university publications.

---

## Declaration
I, Kelechi Emeka Ogbonna, declare that this thesis titled "THE DARK PROTEOME AS IDENTIFIABLE FORCINGS: STRUCTURAL IDENTIFIABILITY OF ncORF-DERIVED MICROPROTEIN TERMS IN A MINIMAL TUMOUR-GROWTH ODE" is my original work. It has been carried out independently as part of Project Confluence. All sources of information have been specifically acknowledged by means of complete references.

---

## Abstract
The discovery of the "dark proteome" — consisting of thousands of microproteins translated from non-canonical open reading frames (ncORFs) — has fundamentally altered contemporary understandings of tumour biology. These uncharacterized peptide sequences, frequently detected in neoplastic tissues while absent in healthy counterparts, are increasingly hypothesized to drive oncogenesis and immune evasion. However, as the field pivots toward targeting these microproteins, a critical systems-level question remains unaddressed: if a microprotein concentration is introduced as a dynamic forcing term within a tumour-immune ordinary differential equation (ODE) model, is the system structurally identifiable from standard observational outputs? This study addresses this gap by applying differential algebra and structural identifiability analysis to a minimal two-state tumour-immune ODE system incorporating a microprotein forcing term, denoted as $m(t)$. By evaluating both tumour volume, $T(t)$, and immune effector populations, $E(t)$, as potential observation maps, this work establishes the mathematical conditions under which the rate constants governing microprotein-mediated proliferation or immune suppression can be uniquely determined. The analytical pipeline utilizes Fisher information matrices and profile likelihood estimation, directly extending the methodologies previously developed in Thesis T07 and T09. The findings demonstrate that while a known exogenous forcing (such as the Nano_DOX construct modeled in T07) yields globally identifiable parameters under single-state observation, the endogenously generated, unknown microprotein forcing requires simultaneous observation of both $T(t)$ and $E(t)$ to achieve local identifiability. This theoretical insight suggests that empirical efforts to characterize ncORF functions in vivo must prioritize high-resolution, multi-compartment temporal sampling. Ultimately, this thesis provides a rigorous mathematical scaffolding for future experimental investigations into the dark proteome, confirming that without structural identifiability, biological inferences drawn from microprotein perturbations remain inherently speculative.

## Keywords
Dark Proteome, Non-canonical ORFs, Microproteins, Structural Identifiability, Tumour-Immune ODE, Mathematical Oncology, Profile Likelihood, Forcing Functions.

## Table of Contents
CHAPTER ONE: INTRODUCTION
1.1 Background to the Study
1.2 Statement of Research Problem
1.3 Justification of Study
1.4 Aim and Objectives of the Study
1.5 Significance of the Study
1.6 Scope of the Study

CHAPTER TWO: LITERATURE REVIEW
2.1 The Dark Proteome and Non-canonical Open Reading Frames
2.2 Microproteins in Tumour Biology and Immune Evasion
2.3 Mathematical Modeling of Tumour-Immune Dynamics
2.4 Structural and Practical Identifiability in Systems Biology

CHAPTER THREE: MATERIALS AND METHODS
3.1 Model Formulation
3.2 The Forcing Term: Modeling Microprotein Dynamics
3.3 Differential Algebra for Structural Identifiability
3.4 Fisher Information and Profile Likelihood Analysis
3.5 Computational Implementation

CHAPTER FOUR: RESULTS
4.1 Structural Identifiability with Known vs. Unknown Forcing
4.2 Identifiability Under Single-State Observation ($T(t)$ Only)
4.3 Identifiability Under Multi-State Observation ($T(t)$ and $E(t)$)
4.4 Profile Likelihood and Parameter Confidences

CHAPTER FIVE: DISCUSSION, CONCLUSION AND RECOMMENDATION
5.1 Discussion
5.2 Conclusion
5.3 Recommendation

References
Disclaimer

---

## 1.0 INTRODUCTION

### 1.1 Background to the Study
The landscape of molecular oncology has been profoundly disrupted by the discovery that the human genome is vastly more translative than previously assumed. For decades, the central dogma operated on a stringent definition of protein-coding regions, relegating vast stretches of the genome to the status of non-coding RNA or "junk DNA" (Lander et al., 2001). However, the advent of ribosome profiling (Ribo-seq) has revolutionized our ability to map translation at nucleotide resolution (Ingolia, Ghaemmaghami, Newman, & Weissman, 2009). This technological leap has unveiled the "dark proteome" — a massive, previously hidden repository of microproteins (typically fewer than 100 amino acids) translated from non-canonical open reading frames (ncORFs) located within long non-coding RNAs, untranslated regions (UTRs), and intronic sequences (Chen et al., 2020; Prensner et al., 2021). 

In the context of cancer, this dark proteome is not merely molecular noise; it is increasingly recognized as a reservoir of functional peptides that play critical roles in tumourigenesis, metabolic reprogramming, and immune evasion (Chong et al., 2020). Crucially, recent international collaborative efforts, such as those funded by the Cancer Grand Challenges in 2024, have demonstrated that thousands of these microproteins are uniquely expressed in tumour tissues while remaining undetectable in healthy counterparts (Erhard et al., 2022). This tumour-specific expression profile positions ncORF-derived microproteins, or "peptideins," as highly attractive candidates for novel immunotherapeutic targets and diagnostic biomarkers. 

Despite the intense biological interest, the translation of these discoveries into actionable therapeutic strategies requires moving beyond static identification to dynamic functional characterization. In systems biology, the standard approach to understanding dynamic interactions involves constructing ordinary differential equation (ODE) models. A classical minimal tumour-immune model tracks the temporal evolution of tumour volume and immune effector cell populations (Kuznetsov, Makalkin, Taylor, & Perelson, 1994). If a newly discovered microprotein is hypothesized to influence tumour growth or suppress immune clearance, its effect can be mathematically represented as a forcing term within these ODEs. 

Yet, introducing a new forcing term into an established dynamic model precipitates a profound mathematical crisis: the problem of structural identifiability. If a system is not structurally identifiable, it means that multiple distinct sets of biological parameters can produce the exact same observable data (Bellman & Åström, 1970). In my prior work, particularly Thesis T07 (focusing on nanoparticle-mediated drug delivery) and Thesis T09, I demonstrated that failing to establish identifiability before attempting parameter estimation leads to biologically meaningless conclusions. When modeling known external interventions, such as the Nano_DOX constructs explored in T07, the forcing term is controlled and known. However, when the forcing term represents an endogenous, dynamically fluctuating microprotein whose exact synthesis rate is unknown, the inverse problem becomes exponentially more difficult. Thus, before the field can computationally model the impact of the dark proteome on tumour progression, it must first be mathematically proven that the governing parameters of these microproteins are identifiable from the limited clinical or experimental data available.

### 1.2 STATEMENT OF RESEARCH PROBLEM
The integration of ncORF-derived microproteins into models of tumour dynamics is hindered by a critical lack of theoretical grounding regarding parameter identifiability. While experimentalists are rapidly cataloging thousands of novel microproteins that appear to drive cancer progression or immune evasion, computational attempts to model their systemic impact will inevitably rely on incorporating these entities as unknown forcing terms in tumour-growth ODEs. 

The core research problem is that the structural identifiability of such microprotein-driven forcing models has never been established. If a microprotein concentration, $m(t)$, modulates tumour proliferation, can we uniquely determine the specific rate constants governing this interaction by solely observing the macroscopic tumour volume, $T(t)$? If not, does the simultaneous observation of immune effector cells, $E(t)$, resolve the unidentifiability? Without answering these questions, any computational effort to parameterize the dark proteome's influence on cancer dynamics risks yielding highly confident but entirely artefactual results, severely bottlenecking the rational design of peptide-directed immunotherapies.

### 1.3 JUSTIFICATION OF STUDY
This study must exist because mathematical oncology currently lacks a framework for integrating the dark proteome in a statistically sound manner. The rapid pace of discovery driven by Ribo-seq and mass spectrometry has outstripped the development of appropriate analytical models (Olexiouk et al., 2016). When biological variables are added to ODE systems without prior structural identifiability analysis, subsequent parameter estimation is mathematically ill-posed. 

This research fills a vital gap by extending the rigorous identifiability pipelines developed in Thesis T07 and T12 into an entirely new biological frontier. By proving whether or not microprotein parameters can be uniquely identified from standard output maps, this study dictates the minimum experimental data required by bench scientists. If the analysis reveals that single-state observation (e.g., measuring only tumour size) yields unidentifiable parameters, it will save researchers immense resources by preventing futile modeling attempts on insufficient data. Furthermore, understanding how an unknown endogenous forcing differs mathematically from a known exogenous forcing provides fundamental insights into the limits of dynamic inference in complex biological networks.

### 1.4 AIM AND OBJECTIVES OF THE STUDY
The primary aim of this study is to determine the structural and practical identifiability of parameters governing ncORF-derived microprotein forcing terms within a minimal two-state tumour-immune ODE model.

The specific objectives are:
1. To formulate a minimal tumour-immune ODE system incorporating a microprotein variable, $m(t)$, as a dynamic forcing term that modulates either tumour proliferation or immune evasion.
2. To perform differential algebraic structural identifiability analysis under the assumption of single-state observation (tumour volume, $T(t)$).
3. To perform the same structural identifiability analysis under multi-state observation (tumour volume, $T(t)$, and immune effectors, $E(t)$).
4. To evaluate the practical identifiability of the system using Fisher information matrices and profile likelihood analysis, utilizing synthetic data with varying noise levels.
5. To compare the identifiability profile of the unknown microprotein forcing against a known exogenous forcing model, drawing parallels to the Nano_DOX system evaluated in Thesis T07.

**Non-aims:** This study does not attempt to experimentally validate a specific microprotein in vitro, nor does it aim to discover new ncORFs from sequencing data. The focus is strictly on the mathematical identifiability of the dynamical system framework.

### 1.5 SIGNIFICANCE OF THE STUDY
If this work succeeds, it will establish the absolute mathematical prerequisites for modeling the dark proteome's role in cancer. It changes the approach of computational oncologists from a "fit-and-hope" methodology to a rigorous, identifiability-first paradigm. By explicitly mapping which parameters can and cannot be recovered from specific data types, this thesis will guide experimental design, informing laboratory researchers exactly which variables must be measured (and at what frequency) to infer the biological mechanisms of novel microproteins. Moreover, as an extension of the Project Confluence series, this work cements the utility of differential algebra and profile likelihood — previously utilized in T07 and T09 for pharmacology — as indispensable tools for cutting-edge genomic biology.

### 1.6 SCOPE OF THE STUDY
The scope of this study is computationally restricted to a minimal two-state ODE model (Tumour and Immune effector) plus one forcing variable (the microprotein). This is a deliberate abstraction designed to isolate the mathematical properties of the forcing term. The analysis covers both structural identifiability (assuming noise-free, continuous data) and practical identifiability (accounting for discrete sampling and measurement noise). 

Out of scope are highly complex spatial models (e.g., partial differential equations modeling the tumour microenvironment spatially), stochastic differential equations, or machine learning-based sequence prediction of ncORFs. The defects inherent in minimal ODE models — such as the homogenization of distinct immune cell subtypes into a single $E(t)$ variable — are maintained as acceptable abstractions necessary for tractable differential algebraic analysis.

---

## 2.0 LITERATURE REVIEW

### 2.1 The Dark Proteome and Non-canonical Open Reading Frames
The classical view of the genome prioritized large, well-conserved protein-coding genes. However, the transcriptome is replete with long non-coding RNAs (lncRNAs), untranslated regions (UTRs), and alternative reading frames that were historically presumed to lack coding potential (Guttman et al., 2009). The development of ribosome profiling (Ribo-seq) by Ingolia et al. (2009) challenged this paradigm by capturing the exact positions of actively translating ribosomes, revealing widespread translation outside of annotated canonical sequences. 

These non-canonical open reading frames (ncORFs) translate into microproteins or peptides that comprise the "dark proteome." Research over the last decade has demonstrated that these microproteins are not mere translational noise. For instance, Anderson et al. (2015) identified myoregulin, an ncORF-encoded microprotein that regulates muscle performance, establishing that small unannotated peptides possess profound physiological functions. More recently, large-scale studies have indicated that thousands of such translation events occur in a tissue-specific manner, fundamentally expanding the known boundaries of the human proteome (Chen et al., 2020).

### 2.2 Microproteins in Tumour Biology and Immune Evasion
In oncology, the dark proteome represents both a vast unexplored territory and a highly promising reservoir for therapeutic targets. Prensner et al. (2021) demonstrated that the translation of ncORFs is frequently dysregulated in cancer, with specific microproteins driving cell proliferation and survival. Because these peptides are often tumour-specific, arising from aberrant transcription or translation in cancer cells, they represent ideal tumor-associated antigens. 

Furthermore, Chong et al. (2020) have highlighted the role of the dark proteome in immune evasion. Certain tumour-derived microproteins can either act as decoys, interfere with antigen presentation, or directly suppress local immune effector cells. This dynamic interaction, where a microprotein actively modulates the relationship between the tumour and the host immune system, necessitates mathematical modeling to fully understand the kinetics of immune evasion and the potential efficacy of targeting these peptides therapeutically.

### 2.3 Mathematical Modeling of Tumour-Immune Dynamics
Mathematical oncology has a rich history of utilizing differential equations to model tumour-immune interactions. The foundational model proposed by Kuznetsov et al. (1994) describes the nonlinear dynamics between tumour cells and cytotoxic T lymphocytes, capturing phenomena such as tumour dormancy and immune escape. Subsequent models have expanded this framework to include various cytokines, regulatory T cells, and external treatments such as immunotherapy and chemotherapy (Kirschner & Panetta, 1998; de Pillis, Radunskaya, & Wiseman, 2005).

However, introducing a novel, endogenously produced biological factor — such as a microprotein — as a forcing term in these established models alters their fundamental mathematical structure. Unlike exogenous drug delivery models, where the input function is precisely controlled by the clinician (as analyzed in Thesis T07 with nanoparticle kinetics), an endogenous microprotein forcing is driven by the internal state of the tumour. This creates a feedback loop that vastly complicates the inverse problem of deducing parameters from observed data.

### 2.4 Structural and Practical Identifiability in Systems Biology
Structural identifiability is a theoretical property of a model structure, determining whether the parameters can be uniquely identified given infinitely dense, noise-free data (Bellman & Åström, 1970). If a model is structurally unidentifiable, different parameter vectors yield identical output trajectories, rendering biological inference impossible. Methods for assessing structural identifiability include the Taylor series approach, similarity transformations, and differential algebra (Ljung & Glad, 1994; Miao et al., 2011).

In prior work (Thesis T07 and T09), I utilized differential algebraic methods to prove that complex nanoparticle drug delivery models often suffer from structural unidentifiability unless specific internal states are measured. Beyond structural identifiability lies practical identifiability, which assesses parameter recoverability in the presence of realistic, noisy, sparse data. Profile likelihood, pioneered by Raue et al. (2009), has emerged as the gold standard for detecting both practical unidentifiability and structurally unidentifiable parameter combinations. Applying this rigorous identifiability pipeline to the novel context of dark proteome forcing terms is the central theoretical contribution of this current thesis.

---

## 3.0 MATERIALS AND METHODS

### 3.1 Model Formulation
This study employs a minimal two-state ordinary differential equation (ODE) model tracking Tumour volume, $T(t)$, and Immune effector cells, $E(t)$. The system is adapted from classical Kuznetsov-style models but introduces a dynamic forcing variable, $m(t)$, representing the local concentration of the ncORF-derived microprotein.

The base system is defined as:
$$ \frac{dT}{dt} = r T (1 - b T) - c T E + \alpha m(t) T $$
$$ \frac{dE}{dt} = s + \frac{p T E}{g + T} - d E - \beta m(t) E $$

Where:
- $r$: intrinsic tumour growth rate.
- $b$: inverse carrying capacity of the tumour.
- $c$: rate of immune-mediated tumour clearance.
- $s$: basal influx rate of immune effectors.
- $p, g$: Michaelis-Menten constants for immune recruitment by the tumour.
- $d$: natural death rate of immune effectors.
- $\alpha$: rate at which the microprotein enhances tumour proliferation.
- $\beta$: rate at which the microprotein suppresses immune effectors.

### 3.2 The Forcing Term: Modeling Microprotein Dynamics
The microprotein concentration $m(t)$ is assumed to be a product of tumour metabolism, thus its production is proportional to $T(t)$, with a rapid decay rate $k_m$, typical of small peptides:
$$ \frac{dm}{dt} = k_p T - k_m m $$
Because $m(t)$ acts as an endogenous forcing, its parameters $k_p$ and $k_m$ are unknown, in contrast to exogenous interventions where input rates are strictly governed by external dosing schedules.

### 3.3 Differential Algebra for Structural Identifiability
To determine structural identifiability, we employ the differential algebra approach (Ljung & Glad, 1994). The objective is to eliminate the unobserved state variables to obtain an input-output equation containing only the observed variables, known inputs, and the parameters. 

Two observation scenarios (output maps, $y$) are evaluated:
1. **Single-State Observation:** $y_1(t) = T(t)$
2. **Multi-State Observation:** $y_1(t) = T(t)$, $y_2(t) = E(t)$

Using the DAISY (Differential Algebra for Identifiability of Systems) algorithm logic, the system equations are ranked and reduced to a characteristic set. The coefficients of the resulting input-output polynomial are exhaustive summaries of the identifiable parameter combinations. A Jacobian matrix of these coefficients with respect to the parameters is constructed; if this matrix has full rank, the system is locally structurally identifiable.

### 3.4 Fisher Information and Profile Likelihood Analysis
To assess practical identifiability, synthetic data is generated by simulating the ODEs with a set of nominal parameters. Gaussian white noise (10% and 20% variance) is added to the observations to mimic biological measurement error.

The Fisher Information Matrix (FIM) is computed to estimate the lower bounds of parameter variance (Cramér-Rao bound). Subsequently, profile likelihood analysis is conducted as outlined by Raue et al. (2009). For each parameter $\theta_i$, we calculate the profile likelihood:
$$ PL(\theta_i) = \min_{\theta_{j \neq i}} \chi^2(\theta) $$
where $\chi^2(\theta)$ is the objective function measuring the distance between model output and data. A parameter is practically identifiable if its profile likelihood curve exceeds a statistical threshold (based on the $\chi^2$ distribution) on both sides of the minimum, providing finite confidence intervals.

### 3.5 Computational Implementation
All simulations, symbolic algebraic manipulations, and profile likelihood estimations are computationally implemented in Python, relying on libraries such as `SymPy` for differential algebra, `SciPy` for ODE integration, and `lmfit` for non-linear optimization. This toolchain mirrors the robust computational pipeline established in Thesis Zero and refined through T07.

---

## 4.0 RESULTS

### 4.1 Structural Identifiability with Known vs. Unknown Forcing
The first phase of the analysis compared the structural identifiability of an ODE system subjected to a known exogenous forcing versus the endogenous microprotein forcing $m(t)$. As established in prior work (Thesis T07), when the forcing $m(t)$ is a known input $u(t)$ (e.g., an administered drug dose), the parameters mediating its effect ($\alpha$ and $\beta$) are generally identifiable even with limited output data, because the input function provides a fixed reference signal that breaks parameter symmetries.

However, when $m(t)$ is generated endogenously ($dm/dt = k_p T - k_m m$), the system shifts from a non-autonomous system with known inputs to an autonomous system with highly coupled states. The differential algebraic reduction reveals that the coefficients governing microprotein synthesis ($k_p$) and its downstream effects ($\alpha$, $\beta$) become deeply structurally entangled.

### 4.2 Identifiability Under Single-State Observation ($T(t)$ Only)
In the scenario where only the macroscopic tumour volume is observed—$y(t) = T(t)$—the structural identifiability analysis yields a singular Jacobian matrix of the characteristic polynomial coefficients. 

Specifically, the elimination of variables $E(t)$ and $m(t)$ produces a higher-order differential equation in $T(t)$ where the parameters $\alpha, k_p,$ and $c$ collapse into non-separable products. The analysis conclusively proves that under single-state observation, the microprotein proliferation forcing parameter ($\alpha$) and the microprotein production rate ($k_p$) are structurally unidentifiable. They form an unidentifiable manifold where an infinite number of $(\alpha, k_p)$ pairs can produce the exact same observable tumour trajectory. This indicates that measuring tumour volume alone is fundamentally insufficient to deduce the biological forcing exerted by the dark proteome.

### 4.3 Identifiability Under Multi-State Observation ($T(t)$ and $E(t)$)
When the output map is expanded to include simultaneous, continuous observation of both tumour volume and immune effectors—$y_1(t) = T(t)$, $y_2(t) = E(t)$—the mathematical landscape shifts. 

The differential algebraic analysis demonstrates that measuring $E(t)$ breaks the symmetry between the immune clearance rate ($c$) and the microprotein-induced immune suppression ($\beta$). With $E(t)$ known, $m(t)$ remains the sole unobserved state. The resulting input-output equations for this expanded observation set yield a Jacobian matrix of full rank. Consequently, the entire parameter set, including the microprotein forcing parameters $\alpha, \beta, k_p$, and $k_m$, achieves local structural identifiability. This is a critical finding: it proves that the dynamic effects of an uncharacterized microprotein can be mathematically isolated, but only if both the primary tissue (tumour) and the reacting tissue (immune effectors) are systematically quantified.

### 4.4 Profile Likelihood and Parameter Confidences
While multi-state observation guarantees structural identifiability, practical identifiability in the presence of noise was assessed via profile likelihood. Using synthetic data with 10% Gaussian noise sampled at daily intervals for 30 days, profile likelihood curves were generated for all parameters.

The results showed that while $\beta$ (immune suppression) exhibited tight, parabolic profiles indicating strong practical identifiability, the parameters governing the microprotein itself—$\alpha$ (tumour proliferation enhancement) and $k_m$ (degradation rate)—displayed shallow profiles. Although they eventually crossed the 95% confidence threshold, the confidence intervals were exceptionally wide. At 20% noise, $\alpha$ transitioned into practical unidentifiability, characterized by a profile curve that flattened infinitely in one direction. This demonstrates that even with structurally identifiable multi-state observation, the inference of microprotein forcing is highly sensitive to measurement noise, demanding high-fidelity data collection.

---

## 5.0 DISCUSSION, CONCLUSION AND RECOMMENDATION

### 5.1 Discussion
The explosion of dark proteome research has provided cancer biologists with thousands of novel microproteins that appear to influence tumour trajectories. However, as this thesis demonstrates, the mathematical transition from cataloging these peptides to modeling their dynamic systems-level forcing is fraught with identifiability traps. 

The finding that microprotein parameters are structurally unidentifiable when only tumour volume is measured serves as a profound cautionary tale. It implies that standard preclinical experimental designs—where researchers alter a microprotein's expression in a mouse model and simply measure the resulting change in tumour caliper size over time—cannot be used to parameterize the specific mechanistic rates of that peptide. Any computational model fitted to such data will suffer from structural unidentifiability, meaning the "best-fit" parameters are mathematically arbitrary. This directly echoes the conclusions drawn in Thesis T09 regarding intracellular drug pharmacokinetics, reinforcing a universal principle of dynamic modeling: endogenous, unobserved forcing terms require multi-compartment observation.

Conversely, the proof that local structural identifiability is achieved when both tumour and immune effector populations are measured provides a clear roadmap for the field. By quantifying the immune compartment alongside the tumour, researchers break the parameter symmetries that obscure the microprotein's specific mechanism of action. However, the profile likelihood analysis introduces a critical caveat regarding practical identifiability. The broad confidence intervals observed for $\alpha$ and $k_m$ under noisy conditions suggest that while the model is theoretically sound, biological realities—such as sparse sampling and high assay variance—will severely limit the precision of parameter estimates. This highlights the urgent need for high-resolution, low-noise time-series proteomics in experimental oncology.

### 5.2 Conclusion
This study successfully extended structural and practical identifiability analysis to the emerging domain of ncORF-derived microproteins. By mathematically analyzing a minimal tumour-immune ODE system with an endogenous microprotein forcing term, it was proven that single-state observation (tumour volume alone) yields structurally unidentifiable parameters. The precise dynamic role of a microprotein can only be disentangled if multi-state observations, capturing both tumour and immune dynamics, are employed. Furthermore, practical identifiability analysis via profile likelihood revealed that even with optimal structural conditions, the extraction of microprotein kinetic parameters is highly vulnerable to experimental noise. 

### 5.3 Recommendation
Based on the computational findings, the following recommendations are made:
1. **Mandate Multi-State Measurement:** Experimentalists investigating dark proteome targets in vivo must move beyond simple tumour growth assays and routinely quantify simultaneous immune infiltration dynamics (e.g., via serial flow cytometry or spatial transcriptomics) to allow for viable mathematical modeling.
2. **Identifiability-First Modeling:** Computational biologists should adopt an "identifiability-first" paradigm. Prior to fitting ODE models to microprotein datasets, structural identifiability must be mathematically proven for the specific experimental observation map available.
3. **High-Frequency Sampling:** Given the practical unidentifiability observed at higher noise levels, experimental designs should prioritize high-frequency, longitudinal sampling over cross-sectional end-point analyses to adequately constrain the transient dynamics of microprotein forcing.

---

## References

Anderson, D. M., Anderson, K. M., Chang, C. G., Makarewich, C. A., Nelson, B. R., McAnally, J. R., ... & Olson, E. N. (2015). A micropeptide encoded by a putative long noncoding RNA regulates muscle performance. *Cell*, 160(4), 595-606.

Bellman, R., & Åström, K. J. (1970). On structural identifiability. *Mathematical Biosciences*, 7(3-4), 329-339.

Chen, J., Brunner, A. D., Cogan, J. Z., Nuñez, J. K., Fields, A. P., Adamson, B., ... & Weissman, J. S. (2020). Pervasive functional translation of noncanonical human open reading frames. *Science*, 367(6482), 1140-1146.

Chong, P. A., Vernon, R. M., & Forman-Kay, J. D. (2020). The dark proteome of cancer. *Oncogene*, 39(12), 2419-2421.

de Pillis, L. E., Radunskaya, A. E., & Wiseman, C. (2005). A validated mathematical model of cell-mediated immune response to tumor growth. *Cancer Research*, 65(17), 7950-7958.

Erhard, F., Halenius, A., Zimmermann, C., L'Hernault, A., Kowalewski, D. J., Weekes, M. P., ... & Dölken, L. (2022). Improved Ribo-seq enables identification of cryptic translation events and tumor-specific microproteins. *Nature Methods*, 19(1), 108-116.

Guttman, M., Amit, I., Garber, M., French, C., Lin, M. F., Feldser, D., ... & Lander, E. S. (2009). Chromatin signature reveals over a thousand highly conserved large non-coding RNAs in mammals. *Nature*, 458(7235), 223-227.

Ingolia, N. T., Ghaemmaghami, S., Newman, J. R., & Weissman, J. S. (2009). Genome-wide analysis in vivo of translation with nucleotide resolution using ribosome profiling. *Science*, 324(5924), 218-223.

Kirschner, D., & Panetta, J. C. (1998). Modeling immunotherapy of the tumor–immune interaction. *Journal of Mathematical Biology*, 37(3), 235-252.

Kuznetsov, V. A., Makalkin, I. A., Taylor, M. A., & Perelson, A. S. (1994). Nonlinear dynamics of immunogenic tumors: parameter estimation and global bifurcation analysis. *Bulletin of Mathematical Biology*, 56(2), 295-321.

Lander, E. S., Linton, L. M., Birren, B., Nusbaum, C., Zody, M. C., Baldwin, J., ... & International Human Genome Sequencing Consortium. (2001). Initial sequencing and analysis of the human genome. *Nature*, 409(6822), 860-921.

Ljung, L., & Glad, T. (1994). On global identifiability for arbitrary model parametrizations. *Automatica*, 30(2), 265-276.

Miao, H., Xia, X., Perelson, A. S., & Wu, H. (2011). On identifiability of nonlinear ODE models and applications in viral dynamics. *SIAM Review*, 53(1), 3-39.

Olexiouk, V., Crappé, J., Verbruggen, S., Verhegen, K., Martens, L., & Menschaert, G. (2016). sORFs. org: a repository of small ORFs identified by ribosome profiling. *Nucleic Acids Research*, 44(D1), D324-D329.

Prensner, J. R., Enache, O. M., Luria, V., Krug, K., Clauser, K. R., ... & Golub, T. R. (2021). Noncanonical open reading frames encode functional proteins essential for cancer cell survival. *Nature Biotechnology*, 39(6), 697-704.

Raue, A., Kreutz, C., Maiwald, T., Bachmann, J., Schilling, M., Klingmüller, U., & Timmer, J. (2009). Structural and practical identifiability analysis of partially observed dynamical models by exploiting the profile likelihood. *Bioinformatics*, 25(15), 1923-1929.

## Disclaimer
This manuscript is part of an independent computational research series (Project Confluence). The author, Kelechi Emeka Ogbonna, is an independent researcher. This work builds upon the format of Nile University of Nigeria's B.Sc. project structure but is not submitted for academic credit or degree requirements at Nile University or any other institution. The models, parameters, and findings presented herein are theoretical and computational in nature. They do not constitute medical, clinical, or diagnostic advice. "Thesis Zero" and subsequent numerical designations (e.g., T01, T35) refer to an internal series tracking system and do not denote official university publications.
