
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
	python3 -m venv .venv
	source .venv/bin/activate
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
---
## Examples

- Escher pathway visualization: [Examples/FBA_on_LAB_Escher_pathways.ipynb](Examples/FBA_on_LAB_Escher_pathways.ipynb)
