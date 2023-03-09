# Automatic Brain Masking

Deep learning based proyect for the automatic masking of a fetal brain.
Takes as input either the contents of the directory specified or the individual image.

Currently only a unet based model can be used. 

This version can handle either folders by looking recursively for all .nii files or individual .nii files. For each file it will save a new mask with the name name_mask.nii on the path of the original image, and it will skip those files that enf with mask.nii.

### About this branch

This branch has 2D dilation added. You can modify the shape and size of the dilation footprint by using the flag --dilation_footprint. Shapes allowed are square and disk.

### Requirementes
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

### instalation

recommended install virtualenvwrapper
Make a virtual environment as to not mix dependencies
    
    $ pip install virtualenv virtualenvwrapper

Then, create a directory for your virtual environments e.g.:
    
    $ mkdir ~/python-envs

You might want to add to your .bashrc file these two lines:

    export WORKON_HOME=~/python-envs
    source /usr/local/bin/virtualenvwrapper.sh

(Note depending on distro, the virtualenvwrapper.sh path might be

    /usr/share/virtualenvwrapper/virtualenvwrapper.sh

Then you can source your .bashrc and create a new Python3 virtual environment:

    $ source .bashrc
    $ mkvirtualenv --python=python3 python_env

To activate or "enter" the virtual env:

    $ workon python_env

To deactivate virtual env:

    $ deactivate

Create a new environment and activate it
the environments name should appear at the beginnig of the shell 
surrounded by parentheses

Download the source code, cd into your decired location

    (env_name)$ git clone **
    (env_name)$ cd brain-masking-tool

install requirements from requirements.txt

    (env_name)$ pip install -r requirements.txt

to run the masking tool

    (env_name)$ python individual_brain_mask.py path_to_dir [OPTION] [OPTION]
    
for usage help run

    (env_name)$ python individual_brain_mask.py path_to_dir -h

If no input is specified it will target the images directory, where you can also include images.
you will have to activate the environment everytime you would like to use the tool.

### limitation
- Unet can currently only work with 256x256 images
