# The Weather Research & Forecasting Model (WRF) coupled with Energy Exascale Earth System Model (E3SM) Land Model (WRF-ELM)
================================================================================

## 1. To compile ELM with MPI, ParallelIO(PIO) and ESMF is needed

### Compile ParallelIO (PIO) library 

   1) Download the latest version from NCAR (https://github.com/NCAR/ParallelIO/releases)
   
   2) Unzip it
   
   3) Copy this `pio-build-perlmutter.sh` script to the parent directory of the unzipped code
   
   4) Update the file paths of unzipped code in pio-build-perlmutter.sh
   
   5) Run this `pio-build-perlmutter.sh` scrip (the -S should point to where the code is, and the -B should point to where you want it to build)
   
   6) After it builds successfully, change directory to the build folder and run `make` and then `make install`
 
### Compile ESMF:
   1) Download the archive for version 8.4.2 from https://github.com/esmf-org/esmf/releases/tag/v8.4.2
      
   2) Unzip it
      
   3) Copy this `esmf-build-perlmutter.sh` to inside the unzipped directory

   4) Update the file paths in esmf-build-perlmutter.sh

   5) Run the `esmf-build-perlmutter.sh` with the last line saying “make”

   6) Run it again but with the last line saying “make install”
 
   7) make ESMF accessible as a module:
      7.1) Copy this `esmf-perlmutter-modulefile` into a directory named `esmf`
      7.2) Update the name of this file to `perlmutter-8.4.2`
      7.3) Update the paths in the file to point to where you installed PIO and ESMF

## 2. Clone ELM and WRF code 
### Clone the WRF repository and checkout develop branch:
```
   git clone https://github.com/wrf-model/WRF.git WRF-ELM
   cd WRF-ELM
   git checkout develop
```

### Clone the ELM repository:
```
   git clone https://github.com/hhllbao93/E3SM.git ELM
   cd ELM
   ./manage_externals/checkout_externals 
```

## 3. Build ELM and its dependencies
### In your ELM directory, build ELM and its dependencies. Currently we only support build WRF-ELM on Perlmutter with gnu
    ./lilac/build_ctsm /PATH/TO/ELM/BUILD --machine perlmutter --compiler gnu

## 4. Building WRF with ELM
### Load the same modules and set the same environments as used for ELM build by sourcing elm_build_environment.sh for Bash:
```
    source elm_build_dir/elm_build_environment.sh
```
### Set makefile variables from ELM needed for the WRF build by setting the following environment. For example for Bash
```
export WRF_ELM_MKFILE=/glade/scratch/$USER/WRF-ELM/ELM/elm_build_dir/bld/elm.mk
```
### Compile the code using build_WRF.sh
```
    sh build_WRF.sh
```
