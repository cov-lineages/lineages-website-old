---
layout: page
---

<h1>Frequently asked questions</h1>

## What if I think I've discovered a new lineage?

There are detailed instructions on what to do if you think you've found a new lineage in the [Pango designation guide](https://cov-lineages.org/lineage_designation.html).

## Where do you find SNPs associated with a given lineage?

The model trains coefficients for each input parameter, for each potential lineage assignment. A particularly large coefficient in a particular lineage’s sigmoid function indicates a stronger association between that location and that lineage. A particularly negative coefficient in a particular lineage’s sigmoid function indicates the opposite. In other words, we can pick up SNPs that are strongly associated with or strongly negatively associated with a given lineage. This information is hosted for download from the [pangoLEARN](https://github.com/cov-lineages/pangoLEARN) data repository.

## Where does the data come from?

<strong>pangolin</strong> runs a multinomial logistic regression model trained against lineage assignments based on GISAID data.

Legacy <strong>pangolin</strong> runs using a guide tree and alignment hosted at [<strong>cov-lineages/lineages</strong>](https://github.com/cov-lineages/lineages.git). Some of this data is sourced from GISAID, but anonymised and encrypted to fit with guidelines. Appropriate permissions have been given and acknowledgements for the teams that have worked to provide the original SARS-CoV-2 genome sequences to GISAID are also hosted [here](https://cov-lineages.org/gisaid_acknowledgements.html).


## How often is the website updated?

The website is updated on a daily basis with up-to-date lineage assignments using all full genome sequences on GISAID. 

## What support statistics are there?
<strong>Pre-pangolin 2.0:</strong>

Of 9,843 GISAID sequences assigned lineages by hand (taking sequence, phylogeny and metadata into account), pangolin accurately assigns the lineage of 97.85% of those sequences. Of the sequences that were not recalled correctly, 74.5% had 0 bootstrap and 0 alrt. We're continuing to work to improve this recall rate, but recommend interpreting the pangolin output cautiously with due attention to the UFbootstrap and aLRT values. 

Given SARS-CoV-2 is relatively slow evolving for an RNA virus and there is still not a huge amount of diversity, missing or ambiguous data at key residues may lead to incorrect placement within the guide tree. We have a filter in place that by default with not call a lineage for any sequence with >50% N-content, but this can be made more conservative with the command line option `--max-ambig`.

<strong>pangolin 2.0 onwards:</strong>

Recall and supporting statistics, hosted [here](https://github.com/cov-lineages/pangoLEARN/blob/master/pangoLEARN/data/lineagerecalls.txt), were generated using the same procedure as above to train a model using 75% of the data, while 25% of the data was used as testing data. Smaller lineages may have lower recall rates due to the very small sample sizes in the training and test set.

<section>
    <h2>Why might a lineage designation change?</h2>
    <p>A lineage designation is made taking the genome sequence data and associated epidemiological data into account. As different labs from different countries around the  world are producing data at different rates, we may only have part of the picture at a given time point when lineages are designated.</p> 
    <p>The example schema below doesn't reflect a real lineage, but aims to demonstrate this exact situation. We see at time point 1 what looks like a clear geographic distinction, even potentially an introduction event from one location to another with evidence of onward spread reflected in the internal nodes within the pink clade. At time point 2, new data has come to light that shows the events may not be as straightforward as that. There doesn't appear to be a single introduction event, and it's even unclear whether there has been onward spread. This now no longer fits what we would describe as a lineage. This is a simple example, but shows how new data can change the narrative around a cluster of sequences.</p>
    <img src="./assets/images/new_data_new_light.svg" style="max-width:80%"  class="center">
</section>

## Why might a lineage assignment change?

A lineage assignment is a "best guess" at what the lineage of an unknown sequence may be. 

This assignment comes with a certain amount of noise. Our most recent estimates give an average 95.8% recall value for designated lineages, with some lineage having better recall and precision values than others. These statistics may vary depending on a number of factors, including the number of sequences in that lineage (i.e. quantity of data), the amount of ambiguity in those sequences (i.e. quality of data) and how unique the defining SNPs are for that lineage (i.e. E484K may be associated with a number of different lineages). 

The assignment may change as new designations are made and new releases of the model are tagged. It may be that your sequence gets included in a new lineage designation that didn't exist when you first ran your sequence through pangolin. The full list of designated sequences can be found at <a href="https://github.com/cov-lineages/pango-designation" style="color:#7351A3">github.com/cov-lineages/pango-designation</a>.
