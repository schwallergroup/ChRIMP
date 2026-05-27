[![PyScaffold](https://img.shields.io/badge/-PyScaffold-005CA0?logo=pyscaffold)](https://pyscaffold.org/)

# ChRIMP

<img src="data/figures/chrimp_logo.png" alt="ChRIMP Logo" width="25%">

This repo is linked with the ChRIMP and MechSMILES paper released by the SchwallerGroup (More info below)

## Installation
The requirements needed to run the code in this repository smoothly is mentioned in `requirements.txt`.
We highly recommend to create a new environment to avoid any unexpected behavior:

```bash
conda create -n chrimp python=3.12
conda activate chrimp
```

The dependencies can be easily installed with:

```bash
pip install -r requirements.txt
```

Then install the package depending on your use case:

### Simple user

```bash
pip install .
```

### Developer

Install in editable mode so local changes are picked up without reinstalling:

```bash
pip install -e .
```

## Models
Models trained during this work can be found as follows:
```python
agent.load_model(
    tokenizer_path="SchwallerGroup/MechSMILES_tokenizer",
    model_path="SchwallerGroup/chrimp_<architecture>_<task>_<dataset><variant>",
)
```

Available model configurations:

| Component      | Options                                                      | Description                                                               |
|----------------|--------------------------------------------------------------|---------------------------------------------------------------------------|
| Architecture   | `T5`, `LLaMa`                                                | Model architecture                                                        |
| Task           | `min_min_1`<br>`equ_equ_n`<br>`equ_min_n`<br>`spe_min_n`     | Elementary steps<br>Equilibrated<br>Rxn w/o by-prod.<br>Rxn w/o stoichio. |
| Dataset        | `flower`, `mech-uspto-31k`, `pmechdb`                        | Training dataset                                                          |
| Variant        | (optional)                                                   | Can be left empty, additional details                                     |

[All available models](https://huggingface.co/models?sort=trending&search=SchwallerGroup%2Fchrimp)

**Example:**
```python
# Load a T5 model trained on reactions without by-products with the FlowER dataset
agent.load_model(
    tokenizer_path="SchwallerGroup/MechSMILES_tokenizer",
    model_path="SchwallerGroup/chrimp_T5_equ_min_n_flower",
)
```

## Notebooks
The notebooks of this repository are stored as `.py` files in the `notebooks` directory, and can be directly run as Python scripts.
However, they are "inflatable" to traditional `.ipynb` using `jupytext`. To convert them, you can run the following command:

```bash
jupytext --to notebook notebooks/<notebook_py_path>
```

If you happen to do changes to these notebooks in `.ipynb` format, you can convert them back to `.py` with the inverse command:

```bash
jupytext --set-formats ipynb,py:percent notebooks/<notebook_ipynb_path>
```

## Article

**Teaching Language Models Mechanistic Explainability Through Arrow-Pushing** ([ArXiv](https://arxiv.org/abs/2512.05722) | [PDF](https://arxiv.org/pdf/2512.05722))

**Citation:**
```bibtex
@article{neukomm2025teaching,
  title={Teaching Language Models Mechanistic Explainability Through Arrow-Pushing},
  author={Neukomm, Th{\'e}o A and Jon{\v{c}}ev, Zlatko and Schwaller, Philippe},
  journal={arXiv preprint arXiv:2512.05722},
  year={2025}
}
```

## Acknowledgements

This project has been set up using PyScaffold 4.6. For details and usage
information on PyScaffold see https://pyscaffold.org/.

