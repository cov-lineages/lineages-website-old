---
layout: page
---

# Output

pangolin outputs a csv file with taxon name and lineage assigned, one line corresponding to each sequence in the fasta file provided. The following descriptions relate to pangolin 3.0 onwards.

## CSV column headers

### taxon
The name of an input query sequence. Note that spaces and commas in sequence names (not a good idea to have these characters in sequence names in general) get replaced by underscores. 

### lineage
The most likely lineage assigned to a given sequence based on the inference engine used and the SARS-CoV-2 diversity [designated](https://github.com/cov-lineages/pango-designation). This assignment may be is sensitive to missing data at key sites. 

### conflict
In the pangoLEARN decision tree model, a given sequence gets assigned to the most likely category based on known diversity. If a sequence can fit into more than one category, the conflict score will be greater than 0 and reflect the number of categories the sequence could fit into. If the conflict score is 0, this means that within the current decision tree there is only one category that the sequence could be assigned to.

### ambiguity_score
This score is a function of the quantity of missing data in a sequence. It represents the proportion of relevant sites in a sequnece which were imputed to the reference values. A score of 1 indicates that no sites were imputed, while a score of 0 indicates that more sites were imputed than were not imputed. This score only includes sites which are used by the decision tree to classify a sequence.

### scorpio_call
If a query is assigned a constellation by scorpio this call is output in this column. The full set of constellations searched by default can be found at [the constellations repository](https://github.com/cov-lineages/constellations).

### scorpio_support
The support score is the proportion of defining variants which have the alternative allele in the sequence. 

### scorpio_conflict
The conflict score is the proportion of defining variants which have the reference allele in the sequence. Ambiguous/other non-ref/alt bases at each of the variant positions contribute only to the denominators of these scores

### version
A version number that represents both the pango-designation number and the inference engine used to assign the lineage. For example:
- PANGO-1.2 indicates an identical sequence has been previously designated this lineage, and has so gone through manual curation. The number 1.2 indicates the version of [pango-designation](https://github.com/cov-lineages/pango-designation) that this assignment is based on.
- PLEARN-1.2 indicates that this sequence is different from any previously designated and that the pangoLEARN model was used as an inference engine to predict the most likely lineage based on the given version of [pango-designation](https://github.com/cov-lineages/pango-designation).
- PUSHER-1.2 indicates that this sequence is different from any previously designated and that UShER was used as an inference engine with fast tree placement and parsimony-based lineage assignment, based on a guide tree (protobuf) file built from the data in a given [pango-designation](https://github.com/cov-lineages/pango-designation) release version.

### pangolin_version
The version of [pangolin](https://github.com/cov-lineages/pangolin) software running.

### pangoLEARN_version
The dated version of the [pangoLEARN](https://github.com/cov-lineages/pangoLEARN) model installed.

### pango_version
The version of [pango-designation](https://github.com/cov-lineages/pango-designation) lineages that this assignment is based on.

### status
Indicates whether the sequence passed the QC thresholds for minimum length and maximum N content.

### note
If any conflicts from the decision tree, this field will output the alternative assignments. If the sequence failed QC this field will describe why. If the sequence met the SNP thresholds for scorpio to call a constellation, it'll describe the exact SNP counts of Alt, Ref and Amb (Alternative, reference and ambiguous) alleles for that call.

## Example output

|taxon                              |lineage  |conflict|ambiguity_<br>score|scorpio_<br>call|scorpio_<br>support|scorpio_<br>conflict|version   |pangolin_<br>version|pangoLEARN_<br>version|pango_version|status   |note                                                      |
|-----------------------------------|---------|--------|---------------|------------|---------------|----------------|----------|----------------|------------------|-------------|---------|----------------------------------------------------------|
|Virus1                          |B.1.617.1|NA     |NA            |            |               |                |PANGO-1.2|2.4.2           |2021-05-10        |1.2          |passed_qc|                                                          |
|Virus2                               |B.1.1.7  |0.0     |1.0            |B.1.1.7     |0.695700       |0.130400        |PLEARN-1.2|2.4.2           |2021-05-10        |1.2          |passed_qc|scorpio call:<br>Alt alleles 16;<br>Ref alleles 3;<br>Amb alleles 4|
|Virus3                         |A        |NA     |NA            |            |               |                |PANGO-1.2|2.4.2           |2021-05-10        |1.2          |passed_qc|                                                          |
|Virus4                          |B        |0.0     |1.0            |            |               |                |PLEARN-1.2|2.4.2           |2021-05-10        |1.2          |passed_qc|                                                          |
|Virus5                            |B.1.314  |0.0     |1.0            |            |               |                |PLEARN-1.2|2.4.2           |2021-05-10        |1.2          |passed_qc|                                                          |
|Virus6 |None     |NA      |NA             |            |NA             |NA              |PLEARN-1.2|2.4.2           |2021-05-10        |1.2          |fail     |seq_len:18000                                             |
|Virus7                 |None     |NA      |NA             |            |NA             |NA              |PLEARN-1.2|2.4.2           |2021-05-10        |1.2          |fail     |seq_len:0                                                 |
|Virus8              |None     |NA      |NA             |            |NA             |NA              |PLEARN-1.2|2.4.2           |2021-05-10        |1.2          |fail     |seq_len:2997                                              |
|Virus9            |None     |NA      |NA             |            |NA             |NA              |PLEARN-1.2|2.4.2           |2021-05-10        |1.2          |fail     |N_content:0.98                                            |
|Virus10       |None     |NA      |NA             |            |NA             |NA              |PLEARN-1.2|2.4.2           |2021-05-10        |1.2          |fail     |N_content:1.0                                             |
|Virus11               |None     |NA      |NA             |            |NA             |NA              |PLEARN-1.2|2.4.2           |2021-05-10        |1.2          |fail     |failed_to_map                                             |



### [Next: References](./references.html)