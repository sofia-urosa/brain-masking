# Automatic Brain Masking

## Table of contents

* [Description](#description)
* [Requirements](#requirements)
* [Limitations](#limitations)
* [Usage](#usage)
* [Setup](#setup)

## Description

Deep learning based project for the automatic masking of a fetal brain. It can take either individual NIfTI files or the contents
of a specified directory.

Currently only a U-net based model is available.

Depending on the input provided (a file or a directory), this tool will recusively look for all .nii files. 
It will save a new mask with the name name_mask.nii for each .nii file found on the path provided. and it 
will skip those files that end with mask.nii unless specified otherwise with the --remasking flag.


## Requirements

- Python 3
- pip

The following can be installed with the requirements.txt file:

- opencv-python-headless==4.7.0.68
- MedPy==0.4.0
- scikit-image==0.19.3
- keras==2.11.0
- tensorflow==2.11.0
- tqdm==4.64.1
- numpy==1.24.1

## Usage

Its recommended that you create a virtual environment to prevent mixing dependencies. If you don't know how to create one,
check out the [setup](#setup) section.

Once you have a virtual environment with all the requirements installed, you can run this tool with the command:

    (env_name)$ python individual_brain_mask.py [-h] [--remasking] [--no-remasking] [--post-processing] \
                        [--no-post-processing] [--match MATCH [MATCH ...]] [--dilation_footprint SHAPE SIZE] \
                        target_file [target_file ...]
                        
Where:
   
|              Argument             | Description                                                                                                                                              |
|:---------------------------------:|----------------------------------------------------------------------------------------------------------------------------------------------------------|
|           `target_file`           | Input path. Required.                                                                                                                                    |
|                `-h`               | Show help message and exit                                                                                                                               |
|           `--remasking`           | Indicates that images already masked should be remasked, rewritting all **_mask.nii* files found. Defaults to  *false*.                                 |
|          `--no-remasking`         | Indicates to skip images that end with **_mask.nii*                                                                                                      |
|        `--post-processing`        | Indicates that the predicted mask should be post processed (morphological closing and dilation). Defaults to  *true*.                                    |
|       `--no-post-processing`      | Indicates that the predicted mask should *not* be post processed                                                                                         |
|             `--match`             | Specify if only files with certain words should be masked. Not case sensitive.                                                                           |
| `--dilation_footprint SHAPE SIZE` | Specify the shape and size of the footprint used for dilation. Shapes available are  **disk** and **square**. If none specified, default is **disk 2**. |

## Limitations
- Unet can currently only work with 256x256 images

## About this model



## Setup

Create a new environment and activate it. VENV 
The environments name should appear at the beginnig of the shell 
surrounded by parentheses

Download the source code, cd into your desired location

    (env_name)$ git clone **
    (env_name)$ cd brain-masking

Install requirements from requirements.txt

    (env_name)$ pip install -r requirements.txt
