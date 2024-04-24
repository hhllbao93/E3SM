# WRF-ELM
The Weather Research & Forecasting Model (WRF) coupled with Energy Exascale Earth System Model (E3SM) Land Model

## Configuring to compile ELM
================================================================================

To compile ELM with MPI, You will need to install PIO and ESMF using the following steps.

### Compile ParallelIO (PIO) library 
Download the archive for version 2.5.9 from here
Unzip it
Copy this `pio-build-perlmutter.sh` script to the parent directory of the unzipped code
Update the file paths
Run this `pio-build-perlmutter.sh` scrip (the -S should point to where the code is, and the -B should point to where you want it to build
After it builds successfully, you’ll need to change directory to the build folder and run `make` and then `make install`
 
### Compile ESMF:
Download the archive for version 8.4.2 from here
Unzip it
Copy this `esmf-build-perlmutter.sh` to inside the unzipped directory
Update the file paths
Run the `esmf-build-perlmutter.sh` with the last line saying “make”
Run it again but with the last line saying “make install”
 
### make ESMF accessible as a module:
Copy this `esmf-perlmutter-modulefile` into a directory named `esmf`
Update the name of this file to `perlmutter-8.4.2`
Update the paths in the file to point to where you installed PIO and ESMF


For questions about the model, use [Github Discussions](https://github.com/E3SM-Project/E3SM/discussions)

Table of Contents 
--------------------------------------------------------------------------------
- [Quick Start](#quickstart)
- [Supported Machines](#supportedmachines)
- [Running](#running)
- [Contributing](#contributing)
- [Acknowledge](#acknowledge)
- [License](#license)

Quick Start
--------------------------------------------------------------------------------
The [Quick Start](https://e3sm.org/model/running-e3sm/e3sm-quick-start/) page 
includes instructions on obtaining the necessary code and input data for model 
setup and execution on a supported machine.

Supported Machines 
--------------------------------------------------------------------------------
E3SM is a high-performance computing application and generally requires a
capable compute cluster to run a scientifically validated case at a useful
simulation speed.

To run E3SM, it is recommended that you obtain time on a 
[Supported Machine](https://e3sm.org/model/running-e3sm/supported-machines/).

Running
--------------------------------------------------------------------------------
Please refer to [Running E3SM](https://e3sm.org/model/running-e3sm/) 
 for instructions on running the model. 

Contributing
--------------------------------------------------------------------------------
Please refer to [Contributing](CONTRIBUTING.md) for details on our code development
process.

Acknowledgement
--------------------------------------------------------------------------------
The Energy Exascale Earth System Model (E3SM) Project should be acknowledged in
publications as the origin of the model using
[these guidelines](https://e3sm.org/resources/policies/acknowledge-e3sm/).

In addition, the software should be cited.  For your convenience,
the following BibTeX entry is provided.
```TeX
@misc{e3sm-model,
	title = {{Energy Exascale Earth System Model (E3SM)}},
	author = {{E3SM Project}},
	abstractNote = {{E3SM} is a state-of-the-art fully coupled model of the {E}arth's 
		climate including important biogeochemical and cryospheric processes.},
	howpublished = {[Computer Software] \url{https://dx.doi.org/10.11578/E3SM/dc.20230110.5}},
	url = {https://dx.doi.org/10.11578/E3SM/dc.20230110.5},
	doi = {10.11578/E3SM/dc.20230110.5},
	year = 2023,
	month = jan,
}
```

License
--------------------------------------------------------------------------------
The E3SM model is available under a BSD 3-clause license.
Please see [LICENSE](LICENSE) for details.

