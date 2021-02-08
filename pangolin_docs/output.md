---
layout: page
---

### Output

Your output will be a csv file with taxon name and lineage assigned, one line corresponding to each sequence in the fasta file provided

Example:

| Taxon       | Lineage   | support | pangoLEARN_version |status | note |
| ----------- |:---------:|:----------:| :----------:|:----------:| :----------:|
| Virus1      |  B.1      | 80       | 2020-04-27 | passed_qc    | |
| Virus2      |  A.1      |  65      | 2020-04-27 | passed_qc    | |
| Virus3      |  A.3      |  100     | 2020-04-27 | passed_qc    | |
| Virus4      |  B.1.4    |  82      | 2020-04-27 | passed_qc    | |
| Virus5      | None      | 0       | 2020-04-27 | fail    |   N_content:0.80 |
| Virus6      | None      | 0       | 2020-04-27 | fail    |   seq_len:0 |
| Virus7      | None      | 0       | 2020-04-27 | fail    |   failed to map |
| Virus8      | B.1.1.7      | 1.0       | 2020-10-27 | passed_qc    |   12/17 B.1.1.7 SNPs |


### [Next: References](./references.html)