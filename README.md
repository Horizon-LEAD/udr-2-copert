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
usage: udr-2-evco2 [-h] udr_output vehicle_type_flag out_dir

UDR-2-COPERT

Translates the data retrieved from the UDR model into the format accepted by the COPERT model.

positional arguments:
  udr_output         The path of the UDR output (xlxs)
  Vehicle_Json_IN    The JSON file describing the vehicles
  Climate_Json_IN    The JSON file describing the climate
  Year               Year input
  out_dir            The output directory

options:
  -h, --help         show this help message and exit
```

### Examples
```
docker run --rm \
    -v $PWD/sample-data:/data \
    registry.gitlab.com/inlecom/lead/models/udr-2-copert:latest \
    /data/input/udr_output.xlsx \
    /data/input/vehicles.json \
    /data/input/climate.json \
    2023 \
    /data/output/
```
