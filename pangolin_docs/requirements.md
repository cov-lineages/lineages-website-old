---
layout: page
---

### Requirements

<strong>pangolin</strong> runs on MacOS and Linux. The conda environment recipe may not build on Windows (I haven't tested it), but can be run using the Windows subsystem for Linux.

1. Some version of conda, we use Miniconda3. Can be downloaded from [here](https://docs.conda.io/en/latest/miniconda.html)
2. Your query fasta file

### Dependencies

```
  - pandas>=1.0.1
  - wheel>=0.34
  - joblib>=0.11
  - PuLP>=2
  - scikit-learn==0.23.1
  - biopython=1.74
  - minimap2
  - pip=19.3.1
  - python=3.7
  - snakemake-minimal=5.13
  - pandas==1.0.1
  - git+https://github.com/cov-ert/datafunk.git
  - git+https://github.com/cov-lineages/pangoLEARN.git
```

> Recommended to install using conda


### [Next: Installation](./installation.html)