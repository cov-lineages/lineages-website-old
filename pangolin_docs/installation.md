---
layout: page
---

### Install pangolin

1. Clone this repository and ``cd pangolin``
2. ``conda env create -f environment.yml``
3. ``conda activate pangolin``
4. ``python setup.py install``
5. That's it

> Troubleshooting install see the [pangolin wiki](https://github.com/cov-lineages/pangolin/wiki)

<strong>Note</strong>: we recommend using pangolin in the conda environment specified in the ``environment.yml`` file as per the instructions above. If you can't use conda for some reason, bear in mind the data files are hosted in a separate repository at
- [<strong>cov-lineages/pangoLEARN</strong>](https://github.com/cov-lineages/pangoLEARN.git) <br>
you will need to pip install them alongside the other dependencies for pangolin (details found in [<strong>environment.yml</strong>](https://github.com/cov-lineages/pangolin/blob/master/environment.yml)).



### Check the install worked

Type (in the <strong>pangolin</strong> environment):

```
pangolin -v
pangolin -pv
```
and you should see the versions of <strong>pangolin</strong> and <strong>pangoLEARN</strong> data release printed respectively.

### Troubleshooting update
- If you have previously installed pangolin using ``pip``, you will need to update pangolin in the same way (``pip install .``)
- Try ``pip uninstall pangolin`` and then re-install with `python setup.py install`


### [Next: Updating pangolin](./updating.html)