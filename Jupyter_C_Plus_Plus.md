##### https://www.learnopencv.com/xeus-cling-run-c-code-in-jupyter-notebook/

conda create -n xeus-cling
source activate xeus-cling
conda install -c conda-forge xeus-cling

######## If it doesn't works try the following one or both.


1. python -m ipykernel install --user --name myenv --display-name "name of the environment"
2. conda install xeus-cling notebook -c QuantStack -c conda-forge (https://github.com/jupyter-xeus/xeus-cling/issues/217)
