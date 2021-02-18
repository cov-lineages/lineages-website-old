---
layout: page
title: Updating pangolin
---


### Updating pangolin

New feature: streamlined updating thanks to [Finlay Maguire](https://github.com/fmaguire)!

Note: This flag will update versions of pangolin and pangoLEARN to the latest tagged releases. Major releases that involve any changes to dependencies (like v2.3) will need to also update the pangolin environment using the instructions below.

<strong>Run:</strong>

```
pangolin --update
```

<strong>Alternatively:</strong>

1. ``conda activate pangolin``
2. ``git pull`` \
pulls the latest changes from github
3. ``python setup.py install`` \
re-installs pangolin.
4. ``conda env update -f environment.yml`` \
updates the conda environment (you're unlikely to need to do this, but just in case!)
5. ``pip install git+https://github.com/cov-lineages/pangoLEARN.git --upgrade`` \
updates if there is a new data release
6. ``pip install git+https://github.com/cov-lineages/lineages.git --upgrade`` \
updates if there is a new data release, this is the legacy data repo and is unlikely to have tagged releases in the future


### Troubleshooting update
- If you have previously installed pangolin using ``pip``, you will need to update pangolin in the same way (``pip install .``)
- Try ``pip uninstall pangolin`` and then re-install with `python setup.py install`

### [Next: Usage](./usage.html)