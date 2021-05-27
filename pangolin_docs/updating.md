---
layout: page
title: Updating pangolin
---


# Updating

## For major releases:

Navigate to your local pangolin repository on the command line.

1. ``conda activate pangolin``
2. ``git pull`` \
pulls the latest changes from github
3. ``conda env update -f environment.yml`` \
updates the conda environment 
4. ``pip install .`` \
re-installs pangolin.

## For minor releases:

```
pangolin --update
```
Note: This flag will update versions of pangolin and pangoLEARN to the latest tagged releases. Major releases that involve any changes to dependencies (like v2.3) will need to also update the pangolin environment using the instructions below.

Update flag thanks to [Finlay Maguire](https://github.com/fmaguire)!

## Troubleshooting update

- If you have previously installed pangolin using ``pip``, you will need to update pangolin in the same way (``pip install .``)
- Try ``pip uninstall pangolin`` and then re-install with `python setup.py install`


### [Next: Usage](./usage.html)