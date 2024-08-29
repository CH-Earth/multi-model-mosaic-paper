# Technical note: How many models do we need to simulate hydrologic processes across large geographical domains? 


[![DOI](https://zenodo.org/badge/849451863.svg)](https://zenodo.org/doi/10.5281/zenodo.13515768)



Analysis code for the paper:

```
Technical note: How many models do we need to simulate hydrologic processes across large geographical domains? 
Wouter J. M. Knoben, Ashwin Raman, Gaby J. Gründemann, Mukesh Kumar, Alain Pietroniro, Chaopeng Shen,
Yalan Song, Cyril Thébault, Katie van Werkhoven, Andrew W. Wood, and Martyn P. Clark
```

## Data requirements
This section outlines data requirements to run this notebook.

### CAMELS data
From the CAMELS data set (Newman et al., 2014; Addor et al., 2017), download:
- The file with topography attributes, `camels_topo.txt` 
- Observed streamflow files `basin_timeseries_v1p2_metForcing_obsFlow.zip`

Direct URLs:
- Main: https://gdex.ucar.edu/dataset/camels/file.html
- Topo: https://gdex.ucar.edu/dataset/camels/file/camels_topo.txt
- Qobs: https://gdex.ucar.edu/dataset/camels/file/basin_timeseries_v1p2_metForcing_obsFlow.zip

### Modeling results
From the "Brief Analysis" data repository (Knoben et al., 2019), download:
- Button: `Complete download (zip, 44.6 GiB)`

Direct URL:
- https://data.bris.ac.uk/datasets/tar/2zutxh2qeep6y2cy6scwgk9eqj.zip

### Boundaries
From the "North American Atlas - Political Boundaries" (Commission for Environmental Cooperation, 2022), download:
- Button: `SHAPEFILE`

Direct URL:
- http://www.cec.org/files/atlas_layers/0_reference/0_01_political_boundaries/politicalboundaries_shapefile.zip


### Computational environment
The analysis uses both R and Python libraries. The main code is in Python, and the relevant R libraries are configured within the notebook, using Python's `r2py` library.

Note: it is assumed that your system has Python and R installs, and (depending on which package manager you use) that the system already contains the installation requirements for the packages listed in `requirements.txt`. If none of this makes sense to you, there are guides available online that will help you navigate this.

#### Python
To prepare for running the notebook:
1. Create a new virtual environment
2. Active the virtual environment
3. Install the required Python packages, given in `requirements.txt`
4. Install the new virtual environment as a notebook kernal:
5. Launch the notebook
6. Ensure the notebook is running on the kernel installed in step (4).

Steps 1-5 will look something like this:

```
#!/bin/bash

# Define where the virtual environment should go
venv_path="/path/to/venv/"
venv_name="mmm_python_r_venv"

# Create a virtual environment
python3 -m venv $venv_path/$venv_name

# Activate the virtual environment
source $venv_path/$venv_name/bin/activate

# Update essentials
pip install --upgrade pip setuptools wheel

# Install the required packages
pip install -r requirements.txt

# Ensure venv is available as notebook kernel
python -m ipykernel install --user --name=$venv_name

# Launch Jupyter notebook
jupyter lab
```

When Jupyter Lab launches, load the notebook. The kernel can (typically) be set in the top right of the notebook, and also through `Kernel` > `Change Kernel...`.

#### R
The `gumboot` R library (Clark and Shook, 2021) is installed in the first three computational cells in the notebook. Note that the 

```
%%R
install.packages("gumboot")
```
cell will open up a small popup window where you'll need to select a download mirror to obtain `gumboot` from.

The next few cells in the notebook will run a small test case to ensure `gumboot` was properly installed.

#### Notebook
Ensure the paths currently stored in the notebook are updated to point to the file locations on your system. In order, these are:
- `camels_topo`
- `camels_flow`
- `brief_folder`
- `border_path`

With this, the notebook should be ready to run.

## References
Addor, N., Newman, A. J., Mizukami, N., and Clark, M. P. (2017): Catchment attributes for large-sample studies, https://doi.org/10.5065/D6G73C3Q.

Clark, M. and Shook, K. (2021): gumboot: Bootstrap Analyses of Sampling Uncertainty in Goodness-of-Fit statistics, https://github.com/CH-Earth/
gumboot, r package version 1.0.1.

Commission for Environmental Cooperation (CEC). 2022. “North American Atlas – Political Boundaries”. Statistics Canada, United States Census Bureau, Instituto Nacional de Estadística y Geografía (INEGI). Ed. 3.0, Vector digital data [1:10,000,000]. Available at http://www.cec.org/north-american-environmental-atlas/political-boundaries-2021/. Accessed 2023-12-20.

Knoben, W., Woods, R., Freer, J., Peel, M., and Keirnan Fowler (2019): Data from "A brief analysis of conceptual model structure uncertainty using
36 models and 559 catchments", https://doi.org/10.5523/BRIS.2ZUTXH2QEEP6Y2CY6SCWGK9EQJ.

Newman, A., Sampson, K., Clark, M. P., Bock, A., Viger, R. J., and Blodgett, D. (2014): A large-sample watershed-scale hydrometeorological
dataset for the contiguous USA, https://doi.org/10.5065/D6MW2F4D.

## Funding
This project received funding under award NA22NWS4320003 from the NOAA Cooperative Institute Program. The statements, findings, conclusions, and recommendations are those of the author(s) and do not necessarily reflect the views of NOAA.
