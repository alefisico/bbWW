# bbWW

This package works on top of [coffea4bees](https://gitlab.cern.ch/cms-cmu/coffea4bees). 

## Instructions:

```
git clone ssh://git@gitlab.cern.ch:7999/cms-cmu/coffea4bees.git
cd coffea4bees/python/
git clone ssh://git@gitlab.cern.ch:7999/algomez/bbWW.git --recursive
cd bbWW/
git clone https://github.com/mcremone/decaf.git -b UL --depth 1
cd ../data/
ln -s ../bbWW/decaf/analysis/data/jsons/
```

## Set Environment at LPC

This code has been tested at the cmslpc, and to simplify the setup, it can be used with the container needed to run on lpc condor computers. To set this container under `coffea4bees/`:
```
curl -OL https://raw.githubusercontent.com/CoffeaTeam/lpcjobqueue/main/bootstrap.sh
bash bootstrap.sh
```
This creates two new files in this directory: `shell` and `.bashrc`. _Additionally, this package contains a `set_shell.sh file`_ which runs the `./shell` executable with the coffea4bees container. This container is based on the `coffeateam/coffea-dask:latest` container including some additional python packages. 
```
source set_shell.sh
```

Remember to run this previous command (aka set your environment) *every time you want to run something*.


## Set Environment in local machine (Ubuntu)

You can set a minimal configuration using a conda environment, for local tests. Keep in mind that this enviroment does **NOT** contained all the packages installed in the container. 

First install [conda-miniforge](https://github.com/conda-forge/miniforge) in your computer (if you haven't done it). If you dont have a cern/fnal account, you can clone the packages from the github repositories:
```
git clone git@github.com:alefisico/coffea4bees.git
cd coffea4bes/python/
git clone git@github.com:alefisico/bbWW.git
```
Then create the conda environment, using the `environment.yml` file in `coffea4bees/`:
```
cd coffea4bees/   ### if you are not there
conda create env --file=environment.yml
```

Then dont forget to set your environment everytime you want to run something:
```
conda activate coffea4bees
```
