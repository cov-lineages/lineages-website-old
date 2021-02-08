---
layout: page
---


### Usage

1. Activate the environment ``conda activate pangolin``
2. Run ``pangolin <query>``, where ``<query>`` is the name of your input file


### Full usage

```
pangolin: Phylogenetic Assignment of Named Global Outbreak LINeages

positional arguments:
  query                 Query fasta file of sequences to analyse.

optional arguments:
  -h, --help            show this help message and exit
  -o OUTDIR, --outdir OUTDIR
                        Output directory. Default: current working directory
  --outfile OUTFILE     Optional output file name. Default: lineage_report.csv
  -d DATADIR, --datadir DATADIR
                        Data directory minimally containing a fasta alignment
                        and guide tree
  --tempdir TEMPDIR     Specify where you want the temp stuff to go. Default:
                        $TMPDIR
  --no-temp             Output all intermediate files, for dev purposes.
  --decompress-model    Permanently decompress the model file to save time
                        running pangolin.
  --max-ambig MAXAMBIG  Maximum proportion of Ns allowed for pangolin to
                        attempt assignment. Default: 0.5
  --min-length MINLEN   Minimum query length allowed for pangolin to attempt
                        assignment. Default: 10000
  --panGUIlin           Run web-app version of pangolin
  --verbose             Print lots of stuff to screen
  -v, --version         show program's version number and exit
  -pv, --pangoLEARN-version
                        show pangoLEARN's version number and exit
  --update              Automatically updates to latest release of pangolin
                        and pangoLEARN, then exits
  ```

### [Next: Output](./output.html)