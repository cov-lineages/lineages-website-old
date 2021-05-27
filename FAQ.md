---
layout: page
---

<h1>Frequently asked questions</h1>

<strong>A set of FAQs related to lineages are available at [pango.network/faqs](https://www.pango.network/faqs/), the following are a list of FAQs related to the pangolin software tool and cov-lineages.org website.</strong>

## Where does the data come from?

The data used to inform pangolin assignments are the lineages hosted at [pango-designation](https://github.com/cov-lineages/pango-designation) matched to the latest GISAID data. We do not share GISAID data as per the data agreement and appropriate permissions have been given and acknowledgements for the teams that have worked to provide the original SARS-CoV-2 genome sequences to GISAID are also hosted [here](https://cov-lineages.org/gisaid_acknowledgements.html).

## How often is the website updated?

The website is updated on a daily basis with the latest lineage assignments using all full genome sequences on GISAID. 

## What support statistics are there?

<strong>pangolin 3.0</strong>

Full details about support statistics output in pangolin 3.0 can be found in the [pangolin documentation](https://cov-lineages.org/pangolin_docs/output.html).

<strong>pangolin 2.0</strong>

Recall and supporting statistics, hosted [here](https://github.com/cov-lineages/pangoLEARN/blob/master/pangoLEARN/data/lineagerecalls.txt), were generated using the same procedure as above to train a model using 75% of the data, while 25% of the data was used as testing data. Smaller lineages may have lower recall rates due to the very small sample sizes in the training and test set.

<strong>pangolin 1.0:</strong>

Of 9,843 GISAID sequences assigned lineages by hand (taking sequence, phylogeny and metadata into account), pangolin accurately assigns the lineage of 97.85% of those sequences. Of the sequences that were not recalled correctly, 74.5% had 0 bootstrap and 0 alrt. We're continuing to work to improve this recall rate, but recommend interpreting the pangolin output cautiously with due attention to the UFbootstrap and aLRT values. 

Given SARS-CoV-2 is relatively slow evolving for an RNA virus and there is still not a huge amount of diversity, missing or ambiguous data at key residues may lead to incorrect placement within the guide tree. We have a filter in place that by default with not call a lineage for any sequence with >50% N-content, but this can be made more conservative with the command line option `--max-ambig`.


## Why might a lineage assignment change?

A lineage assignment is a "best guess" at what the lineage of an unknown sequence may be based on available data. We report [pango-designation](https://github.com/cov-lineages/pango-designation) version numbers with the assignment and this indicates what data the inference engine bases the assignment on.

This assignment comes with a certain amount of noise. Our most recent estimates give an average 95.8% recall value for designated lineages, with some lineage having better recall and precision values than others. The accuracy of assignment may vary depending on a number of factors, including the number of sequences in that lineage (i.e. quantity of data), the amount of ambiguity in those sequences (i.e. quality of data) and how unique the defining SNPs are for that lineage (i.e. E484K may be associated with a number of different lineages).

The assignment may change as new designations are made and new releases of the model are tagged. It may be that your sequence gets included in a new lineage designation that didn't exist when you first ran your sequence through pangolin. The full list of designated sequences can be found at <a href="https://github.com/cov-lineages/pango-designation" style="color:#7351A3">github.com/cov-lineages/pango-designation</a>.


## I think my sequence has been incorrectly assigned, what can I do?

The vast majority of the time, an incorrect assignment is down to missing data. A given sequence may be lacking an informative SNP and this can lead to incorrect placement in the pangoLEARN decision tree, or incorrect placement in the UShER protobuf file if running in `--usher` mode (available from pangolin 3.0 onwards).

If you have a complete genome sequence and suspect there's something wrong with the assignment model, the model is informed by the data input from [pango-designation](https://github.com/cov-lineages/pango-designation). The lineages are all designated by hand based on evidence in the phylogenetic tree. If you believe a new sequence should be designated as something other than what it's being assigned, users can follow the instructions at [pango.network](https://www.pango.network/how-does-the-system-work/how-to-suggest-a-new-lineage/) to submit a lineage update or correction. This involves posting an issue to [pango-designation](https://github.com/cov-lineages/pango-designation) where the [Pango Network Team](https://www.pango.network/committees/committee-structure/) will respond to and address queries. 

## I've found a bug in the pangolin software, what can I do?

Please post an issue to the [pangolin](https://github.com/cov-lineages/pangolin) repository where we will answer any queries and try to fix any bugs you may have found!

