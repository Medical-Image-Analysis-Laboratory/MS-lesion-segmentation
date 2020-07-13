# Multiple sclerosis cortical and WM lesion segmentation at 3T MRI: a deep learning method based on FLAIR and MP2RAGE

This is the code repository of the Neuroimage: Clinical [paper](https://doi.org/10.1016/j.nicl.2020.102335).

## Overview
This software provide a multiple sclerosis cortical and white matter lesion segmentation. The input required are co-registered FLAIR and MP2RAGE volumes of the subject acquired at 3T. The code depends on the [NiftyNet framework](https://niftynet.readthedocs.io/) and it is based on [Tensorflow](https://www.tensorflow.org/). A GPU is required to train the network with new data, whereas a LINUX machine is sufficient for inference.

## Install
First clone the repository and pull the niftynet code in the submodule as follows <br />
`git clone  https://github.com/FrancescoLR/MS-lesion-segmentation/` <br />
`git submodule update --init` <br />

Optionally, install a Python virtual environment
```
# CPU compute
python3 -m venv niftynet-cpu --clear
# GPU compute
python3 -m venv niftynet-gpu --clear
```

Next, activate the environment and install the custom Niftynet and the required dependencies: <br />
```
source $(pwd)/niftynet-cpu/bin/activate
# for the GPU version, run `source $(pwd)/niftynet-gpu/bin/activate`
cd niftynet/
python -m pip install -r requirements-cpu.txt
# for the GPU version, run `python -m pip install -r niftynet/requirements-gpu.txt`
python -m pip install -e ./niftynet
deactivate
```

Before any use, the vitual environment needs to be activate
```
source $(pwd)/niftynet-cpu/bin/activate
# For the GPU version `source $(pwd)/niftynet-gpu/bin/activate`
```

Example command for inference, which follows the settings in the configuration file: <br />
`net_run inference -c path_to/config_file.ini  -a niftynet.application.segmentation_application.SegmentationApplication` <br />

Further instructions are present in the [NiftyNet website](https://niftynet.readthedocs.io/en/dev/). A configuration file and a trained model are provided in separate folders in the root directory.


## License
This software is released under the version 2.0 of the Apache License.

## Cite
If you use this code please cite the follwing references:

- Gibson, Eli, et al. "NiftyNet: a deep-learning platform for medical imaging." Computer methods and programs in biomedicine 158 (2018): 113-122. [doi](https://doi.org/10.1016/j.cmpb.2018.01.025)
- La Rosa, Francesco, et al. "Multiple sclerosis cortical and WM lesion segmentation at 3T MRI: a deep learning method based on FLAIR and MP2RAGE." NeuroImage: Clinical (2020): 102335. [doi](https://doi.org/10.1016/j.nicl.2020.102335)
- La Rosa, Francesco, Abdulkadir. Ahmed, Thiran, Jean-Philippe, Granziera, Cristina, & Bach Cuadra, Merixtell. (2020, July 7). Software: Multiple sclerosis cortical and WM lesion segmentation at 3T MRI: a deep learning method based on FLAIR and MP2RAGE (Version v1.0). [doi](https://doi.org/10.5281/zenodo.3932736)


