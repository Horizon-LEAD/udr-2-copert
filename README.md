# UDR-2-COPERT

## Description

Translates the data retrieved from the UDR model into the format accepted by the
[COPERT] model.

## Installation

The `requirements.txt` and `Pipenv` files are provided for the setup of an environment where the module can be installed. The package includes a `setup.py` file and it can be therefore installed with a `pip install .` when we are at the same working directory as the `setup.py` file. For testing purposes, one can also install the package in editable mode `pip install -e .`.

After the install is completed, an executable `udr-2-copert` will be available to the user.

Furthermore, a `Dockerfile` is provided so that the user can package the model.

To build the image the following command must be issued from the project's root directory:
```
docker build -t udr-2-copert:latest .
```

## Usage
The executable's help message provides information on the parameters that are needed.
```
$ udr-2-copert -h
usage: udr2copert [-h] [-v] udr_output Vehicle_Json_IN Climate_Json_IN year OUTDIR

UDR-to-COPERT Interface

positional arguments:
  udr_output       The Json output file from Echelon as input to the connector
  Vehicle_Json_IN  Vehicle json same as Copert v2 - exclude stock, mean_activity
  Climate_Json_IN  Climate json same as Copert v2
  year             Set the year
  OUTDIR           The output directory

optional arguments:
  -h, --help       show this help message and exit
  -v, --verbosity  Increase output verbosity (default: 0)
```

### Examples

```
python -m src.udr2copert \
  ./sample-data/input/output.xlsx \
  ./sample-data/input/vehicles.json \
  ./sample-data/input/climate.json \
  2023 \
  ./sample-data/output/

udr-2-copert \
  ./sample-data/input/output.xlsx \
  ./sample-data/input/vehicles.json \
  ./sample-data/input/climate.json \
  2023 \
  ./sample-data/output/
```

```
docker run --rm \
    -v ./sample-data:/data \
    udr-2-copert:latest \
    /data/input/udr_output.xlsx \
    /data/input/vehicles.json \
    /data/input/climate.json \
    2023 \
    /data/output/
```
