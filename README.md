## Overview

Suite3D is a volumetric cell detection algorithm, generally applicable to any type of multi-plane functional 2p imaging where you see cells on multiple planes. For an overview of the algorithms, [see our recent preprint](https://www.biorxiv.org/content/10.1101/2025.03.26.645628v1). Note that the algorithms are still in an "early beta" phase, and you might run into a few kinks - please reach out to Ali (ali.haydaroglu.20@ucl.ac.uk, or by creating issues on this repository) and I'll be happy to help you get up and running. 

## Installation
If the cloning line doesn't work, try: git clone --recurse-submodules https://github.com/alihaydaroglu/suite3d

```
git clone --recurse-submodules git@github.com:alihaydaroglu/suite3d.git
conda env create -f environment.yml
conda activate suite3d-gpu
```
If installation gets stuck around "Solving Environment", you should use libmamba ([explanation](https://conda.github.io/conda-libmamba-solver/libmamba-vs-classic/)), install it using the [instructions here](https://www.anaconda.com/blog/a-faster-conda-for-a-growing-community). Also, set the conda channel priority to be strict: `conda config --set channel_priority strict`. It's important that you don't forget the `-e` in the pip command, this allows the suite2p installation to be editable.

## Updating
Everytime you do `git pull`, you should also do `git submodule update` to pull the latest version of my suite2p branch, which is a submodule of this repo. 
If you find this annoying, you can [make git do it automatically](https://stackoverflow.com/questions/4611512/is-there-a-way-to-make-git-pull-automatically-update-submodules)

## Usage
Run a jupyter notebook in this envinronment, either by running `jupyter notebook` in the suite3d-gpu conda environment or running a jupyter server from a different conda env and selecting this environment for the kernel ([see here](https://medium.com/@nrk25693/how-to-add-your-conda-environment-to-your-jupyter-notebook-in-just-4-steps-abeab8b8d084)). Make sure you use the correct environment!

Then, run the Demo notebook.


## UI only installation
If you want to only visualize results on your local laptop, you can install a lightweight script that doesn't have any of the computational dependencies. 

```
git clone --recurse-submodules git@github.com:alihaydaroglu/suite3d.git
conda create -y -n s3d-vis -c conda-forge python=3.9
conda activate s3d-vis
pip install "napari[pyqt5]"
pip install notebook
conda install pyqtgraph
conda install -c conda-forge matplotlib
```

## Docker

There is a Dockerfile in this repo that successfully builds (`docker build - < Dockerfile`). I don't know anything about Docker, but I would love to have this successfully run in a container. If you manage to get that working let me know! Ideally, this would also include some sort of X host to run napari (https://napari.org/stable/howtos/docker.html#base-napari-image), presumably there is a way to merge the napari-xpra docker image into this one to make that work. 

## Sample Data
Use [this](https://liveuclac-my.sharepoint.com/:f:/g/personal/ucqfhay_ucl_ac_uk/EuQX2PFw13xHhILvRux29AQB48tXCxBJQ7z6JfHee25pfw?e=HmBlAc) for the standard 2p imaging demo, recorded in mouse CA1, courtesy of Andrew Landau. 

Sample LBM data coming soon! 
