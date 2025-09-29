# FiniteVolumeGPU

This is a HIP version of the [FiniteVolume code](https://github.com/babrodtk/FiniteVolumeGPU). It is a Python software package that implements several finite volume discretizations on Cartesian grids for the shallow water equations and the Euler equations. 

## Setup on LUMI-G
Here is a step-by-step guide on installing packages on LUMI-G

### Step 1: run conda-container
Installation via conda can be done as:
```
ml LUMI partition/G
ml lumi-container-wrapper
```
```
conda-containerize new --mamba --prefix MyCondaEnv conda_environment_lumi.yml
```
where the file `conda_environment_lumi.yml` contains packages to be installed.

### Step 2: Set the env. variable to search for binaries
```
export the bin path: export PATH="$PWD/MyCondaEnv/bin:$PATH"
```
### An alternative: Convert to a singularity container with cotainr
```
cotainr build my_container.sif --system=lumi-g --conda-env=conda_environment_lumi.yml
```

### Error when running MPI.
```
`MPI startup(): PMI server not found. Please set I_MPI_PMI_LIBRARY variable if it is not a singleton case.
```
This can be resolved by exporting this:
```
export I_MPI_PMI_LIBRARY=/opt/cray/pe/mpich/8.1.27/ofi/cray/14.0/lib/libmpi.so
```
### Install hip-python
```
python -m pip install -i https://test.pypi.org/simple/ hip-python==5.4.3.470.16
```

The testing was done with this specific version `hip-python==5.4.3.470.16`

 
