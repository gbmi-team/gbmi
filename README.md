# Guarantees-Based Mechanistic Interpretability

## Setup

The code can be run under any environment with Python 3.9 and above.

We use [poetry](https://python-poetry.org) for dependency management, which can be installed following the instructions [here](https://python-poetry.org/docs/#installation).

To build a virtual environment with the required packages, simply run

```bash
poetry config virtualenvs.in-project true
poetry install
```

Notes
- On some systems you may need to set the environment variable `PYTHON_KEYRING_BACKEND=keyring.backends.null.Keyring` to avoid keyring-based errors.
- The first line tells poetry to create the virtual environment in the project directory, which allows VS Code to find the virtual environment.
- If you are using caches from other machines, if you see errors like "dbm.error: db type is dbm.gnu, but the module is not available", you can probably solve the issue by following instructions from [StackOverflow](https://stackoverflow.com/a/49597001/377022):
    - `sudo apt-get install libgdbm-dev python3-gdbm`
    - If you are using `conda` or some other Python version management, you can inspect the output of `dpkg -L python3-gdbm` and copy the `lib-dynload/_gdbm.cpython-*-x86_64-linux-gnu.so` file to the corresponding `lib/` directory associated to the python you are using.

## Running notebooks

To open a Jupyter notebook, run

```bash
poetry run jupyter lab
```

If this doesn't work (e.g. you have multiple Jupyter kernels already installed on your system), you may need to make a new kernel for this project:

```bash
poetry run python -m ipykernel install --user --name=gbmi
```

## Reproducing the plots and numbers in the figures

You can run
```bash
poetry run python notebooks/max_of_4_all_models.py
```
to produce the data, and the plots can be seen with
```bash
poetry run python notebooks/max_of_4.py
```
There are also corresponding `.ipynb` files for each of these.

See also [`.github/workflows/ci.yml`](./.github/workflows/ci.yml).

You can delete `notebooks/.cache` to regenerate all the proofs and analyses from scratch rather than loading them from cache.
