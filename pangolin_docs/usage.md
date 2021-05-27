---
layout: page
---
# Usage

### Simple usage

By default pangolin will run the pangoLEARN model to assign the most likely lineage out of all [currently designated lineages](https://cov-lineages.org/lineage_designation_list.html) and scorpio to assign specific [lineages of interest](https://github.com/cov-lineages/constellations/tree/main/constellations/definitions) by presence of constellations. 

1. Activate the environment ``conda activate pangolin``
2. Run ``pangolin <query>``, where ``<query>`` is the name of your input file


### UShER mode

pangolin 3.0 can optionally run a fast parsimony-based lineage assignment using [UShER](https://github.com/yatisht/usher) as the inference engine.

1. Activate the environment ``conda activate pangolin``
2. Run ``pangolin --usher <query>``, where ``<query>`` is the name of your input file


### Output alignment

In the process of lineage assignment, pangolin creates an alignment using [minimap2](https://github.com/lh3/minimap2) to map against an early, anonymised reference SARS-CoV-2 sequence and then using [gofasta](https://github.com/cov-ert/gofasta) to generate a fasta file from that mapping with the non-coding regions masked out with N's. For convenience (I know I certainly find it very useful for quickly generating a SARS-CoV-2 alignment), pangolin has a flag that will output this alignment in addition to the lineage report instead of writing it to temp. The exact parameters can be found at source [here](https://github.com/cov-lineages/pangolin/blob/a6e5c46c4ddd50a9e647abccf70e544fa18898cb/pangolin/scripts/pangolearn.smk#L47). 

1. Activate the environment ``conda activate pangolin``
2. Run ``pangolin --alignment <query>``, where ``<query>`` is the name of your input file


### Full usage options

```
pangolin: Phylogenetic Assignment of Named Global Outbreak LINeages

positional arguments:
  query                 Query fasta file of sequences to analyse.

optional arguments:
  -h, --help            show this help message and exit
  -o OUTDIR, 
  --outdir OUTDIR
                        Output directory. Default: current working directory
  --outfile OUTFILE     Optional output file name. Default: lineage_report.csv
  --alignment           Optional alignment output.
  -d DATADIR, 
  --datadir DATADIR
                        Data directory minimally containing a fasta alignment and guide tree
  --tempdir TEMPDIR     Specify where you want the temp stuff to go. Default: $TMPDIR
  --no-temp             Output all intermediate files, for dev purposes.
  --decompress-model    Permanently decompress the model file to save time running pangolin.
  --usher               Use UShER model instead of default pangoLEARN
  --usher-tree 
  USHER_PROTOBUF
                        UShER Mutation Annotated Tree protobuf file to use instead of --usher default from pangoLEARN repository or --datadir
  --max-ambig MAXAMBIG  Maximum proportion of Ns allowed for pangolin to attempt assignment. Default: 0.3
  --min-length MINLEN   Minimum query length allowed for pangolin to attempt assignment. Default: 25000
  --verbose             Print lots of stuff to screen
  -t THREADS, 
  --threads THREADS
                        Number of threads
  -v, 
  --version         show pangolin's version number and exit
  -pv, 
  --pangoLEARN-version
                        show pangoLEARN's version number and exit
  -dv, 
  --pango-designation-version
                        show pango-designation version number and exit
  --update              Automatically updates to latest release of pangolin and pangoLEARN, then exits

  ```

### [Next: Output](./output.html)