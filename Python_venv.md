# Python venv

![Static Badge](https://img.shields.io/badge/Python-red) 
![Static Badge](https://img.shields.io/badge/Virtual_environment-white)


# Overview
In this repo we will see how to
[x] Set up a new virtual environment in python.
[x] Activate/Deactivate it.
[x] Install and check the environment is properly filled.
[x] Export to a requirements.txt and install all the libraries of the txt file.


# Installation

To install venv type the following command in your terminal with the corresponding **python version**.

```bash
sudo apt install python3.12-venv
```


# Creation of a new venv

1- Go to your working directory

2- Create a new venv

```bash
python3.12 -m venv env_name
#example
python3.12 -m venv ts_env
```

This will create a folder in your working directory called env_name. A virtual env is basically this. 
It is a folder where all the libraries will be installed.
If you want to delete an enrironment, just delete the folder.




# Activation/Deactivation of the new env
## Activation

```bash
source env_name/bin/activate
#example
source ts_env/bin/activate
```


## Deactivation

```bash
deactivate
```

## Check and requirement.txt
To check the libraries installed in the venv pip list command will return all the libraries intalled in it.

```bash
pip list
```
Usually, we want to export the libraries list to a requirements.txt.
This can be done simply by the following command

```bash
pip freeze > requirements.txt
```

Later, to install the libraries of this txt file, it will be done via
```bash
pip install -r requirement.txt
```
