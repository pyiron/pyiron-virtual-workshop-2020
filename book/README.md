# pyiron virtual workshop 2020: Workflows for atomistic simulations

Tutorials, exercises, and solutions for the pyiron workshop 2020.

## Things to do before the workshop

For this workshop, you will need to have pyiron installed on your workstation. While 
pyiron is platform independent, Linux is required to run certain external 
simulation codes like LAMMPS and Sphinx. For windows users, it is recommended that you install the linux 
subsystem for windows. More details [here](https://docs.microsoft.com/en-us/windows/wsl/install-win10). THe Debian distribution of Linux is recommended although Ubuntu works fine as well. If you are a Mac user, you will only be able to run LAMMPS examples (which is still fine!)

### Installing conda

While pyiron can be installed in several ways, installation via conda is recommended for this workshop since this
ensures that you are working with the latest and stable version of pyiron. As a 
first step, follow [this guide](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html#) 
to install miniconda (recommended) or anaconda. Using the Linux/Mac or linux subsystem terminal on windows, conda can be installed as follows.
Choose the appropriate 64 bit or 32 bit installer available [here](https://docs.conda.io/en/latest/miniconda.html#linux-installers). 
For example, the 64 bit executable for linux can be installed as follows:

```
sudo apt-get install wget
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
chmod +x Miniconda3-latest-Linux-x86_64.sh
./Miniconda3-latest-Linux-x86_64.sh
source ~/.bashrc
```

#### Creating a new conda environment

After installing conda, it is recommended to create a new conda environment to install the required packages for the workshop

`conda create --name pyiron_workshop python=3.7 -y`

To activate this conda environment, type

`source activate pyiron_workshop`

or for MacOS

`conda activate pyiron_workshop`

Please install all packages and run the notebooks only after you have activated this environment. 
After the workshop is over, this environment can be deactivated `source deactivate` or `conda deactivate`.
If you want to run the notebooks later, just reactivate the environment.

### Installing pyiron and other packages using conda-forge

Once you've activated the `pyiron_workshop` environment, install the necessary packages using

`conda install -y -c conda-forge git pyiron nglview lammps nodejs=13.13.0 jupyterlab`

If you are using Linux (or Linux subsystem for windows), you can also use SPHINX

`conda install -y -c conda-forge sphinxdft=2.6.1=h6ced99e_5`

Further, to get nglview working smoothly on jupyter notebooks, the following commands need to be typed

```
jupyter nbextension install nglview --py --sys-prefix
jupyter nbextension enable nglview --py --sys-prefix
jupyter labextension install @jupyter-widgets/jupyterlab-manager --no-build
jupyter labextension install nglview-js-widgets
jupyter labextension install @jupyterlab/toc
```

### Configuring pyiron

Type the following lines to configure pyiron and dowload the necessary resources (binaries and potentials)

```
cd
printf "[DEFAULT]\nTOP_LEVEL_DIRS = ${HOME}\nRESOURCE_PATHS = ${HOME}/resources" > ${HOME}/.pyiron
git clone https://github.com/pyiron/pyiron-resources.git ${HOME}/resources
```
