
# FBA Tools
---
This repository contains Jupyter notebooks that use Flux Balance Analysis (FBA) to study metabolic networks. The notebooks focus on model exploration, simulation, and pathway visualization to support research and learning.

(Roozbeh H. Pazuki, 2026)

---

## Installation

Create and activate a virtual environment, update `pip`, then install dependencies from `requirment.txt`.

### Windows (PowerShell)

1. Create and activate the environment:
	```
	python -m venv .venv
	.\.venv\Scripts\Activate.ps1
	```
2. Update `pip` and install requirements:
	```
	python -m pip install --upgrade pip
	python -m pip install -r requirment.txt
	```
3. Start Jupyter:
	```
	jupyter notebook
	```

### macOS/Linux (bash/zsh)

1. Create and activate the environment:
	```
	conda create --name escher_1 
	conda activate escher_1
	conda install -n escher_1 -c conda-forge nodejs=14.20.1
	```
2. Update `pip` and install requirements:
	```
	python -m pip install --upgrade pip
	python -m pip install -r requirment.txt
	jupyter lab clean --all
	jupyter labextension install @jupyter-widgets/jupyterlab-manager
    jupyter labextension install escher@1.7.3
	jupyter lab build --dev-build=False --minimize=False
	```
3. Start Jupyter:
	```
	jupyter lab
	```

4. In case the Escher error, try this
```
conda run -n escher_1 python -m pip install --force-reinstall "escher==1.7.3"
conda run -n escher_1 python -m pip install --force-reinstall "markupsafe==2.0.1" "jinja2==2.11.3"
conda run -n escher_1 jupyter lab clean --all
conda run -n escher_1 jupyter lab build --dev-build=False --minimize=False
```
---


## Next time update


For the next time update, after you activate your Python environment, first downliad the latest version of the project by running
```
git pull
```
and next, the following command for the latest version of the library
```
pip install --upgrade --force-reinstall git+https://github.com/rpazuki/lab_utils.git#subdirectory=src
```

---

## Examples

- Escher pathway visualization: [Examples/FBA_on_LAB_Escher_pathways.ipynb](Examples/FBA_on_LAB_Escher_pathways.ipynb)
