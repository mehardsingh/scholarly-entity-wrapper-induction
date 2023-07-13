# scholarly-entity-wrapper-induction
A wrapper induction tool to retrieve structured information from semi-structured web pages regarding scholarly entities like professors, researchers, etc.

## Variance Based Wrapper Induction

Wrapper induction using variance/frequency to separate information from "templated" portions of webpages. Creates "anchor points" to label content on webpages in an unsupervised fashion (no external labels of HTML elements required).

Run all cells in `WrapperInduction4.ipynb`.

Using **just three** training URLs, it can produce the following result for the unseen URL:

```
Input: https://math.illinois.edu/directory/profile/mando
```
```
Output:
{
    "External Links": [
        "Visit Website"
    ],
    "Biography": [
        "I am a mathematician specializing in algebraic topology.\u00a0 My research involves interactions between algebraic topology, algebraic geometry, and mathematical physics.\u00a0 I joined the University of Illinois in 1999, and served as chair of the Department of Mathematics from 2011 to 2016. I am currently the Associate Dean of the Sciences in the College of LAS."
    ],
    "Research Interests": [
        "Homotopy theory, formal groups, analysis on loop spaces, elliptic cohomology and representation theory."
    ],
    "Contact Information": [
        "2090 Lincoln Hall",
        "702 S. Wright Street, MC-448",
        "Urbana, IL 61801"
    ],
    "Additional Campus Affiliations": [
        "Associate Dean, College of Liberal Arts and Sciences"
    ],
    "Recent Publications": [
        "Ando, M.",
        ", Blumberg, A. J., & Gepner, D. (2018).",
        "Parametrized spectra, multiplicative thom spectra and the twisted umkehr map",
        ".",
        "Geometry and Topology",
        ",",
...
    "College of Liberal Arts & Sciences\nDepartment of Mathematics": [
        "College of Liberal Arts & Sciences\nDepartment of Mathematics"
    ]
}
```

## HITS Algorithm Based Template Labelling

Uses a novel variation of HTIS with spaCy semantic word embeddings to create labels for HTML header elements. Run all cells in `hits_algorithm.ipynb`.

## Gibson (Hashing) Wrapper Induction

Based on "The Volume and Evolution of Web Page Templates" by Gibson, Punera, and Tomkins. Template-hash counts with both pure text and DOM trees. For pure text, run all cells in `gibson_text.ipynb`. For DOM trees, run all cells in `gibson_dom.ipynb`.

```
Input: https://math.illinois.edu/directory/profile/palbin
```
```
Output: 
{
    "research": [
        "My research is in geometric analysis. I am particularly interested in analytic representations of topological invariants, analysis on non-compact or singular spaces, spectral geometry, heat kernels, and Dirac operators."
    ],
    "publications": [
        ", Rochon, F., & Sher, D. (2022). A CHEEGER\u2013M\u00dcLLER THEOREM FOR MANIFOLDS WITH WEDGE SINGULARITIES. Analysis and PDE, (3), 567-642. https://doi.org/10.2140/apde.2022.15.567, & Quan, H. (2022). Sub-Riemannian Limit of the Differential Form Heat Kernels of Contact Manifolds. , (8), 5818-5881. https://doi.org/10.1093/imrn/rnaa270, Rochon, F., & Sher, D. (2021). Resolvent, heat kernel, and torsion under degeneration to fibered cusps. , (1314), 1-138. https://doi.org/10.1090/memo/1314 (2020). Poincar\u00e9-Lovelock metrics on conformally compact manifolds. , , [107108]. https://doi.org/10.1016/j.aim.2020.107108, Rochon, F., & Sher, D. (2018). Analytic torsion and R-torsion of Witt representations on manifolds with cusps. , 167(10), 1883-1950. https://doi.org/10.1215/00127094-2018-0009View all publications on Illinois Experts"
    ],
    "education": [
        "PhD Mathematics, Stanford, 2005"
    ],
    "students": [],
    "teaching": [],
    "contact": [
        "Department of Mathematics\r",
        "237A Illini Hall, MC-382\r",
        "1409 W. Green Street\r",
        "Urbana, IL 61801"
    ]
}
```