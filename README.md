# Automatic Brain Masking

Deep learning based proyect for the automatic masking of a fetal brain.
Takes as input either the contents of the images directory or a directory marked with
"--target_dir=path_to_dir"

Currently only a unet based model can be used.
A mask rcnn model is available but only for use with a GPU, 
so all relevant maskrcnn parts have been commented out 

It takes as input a path to a directory, and recursivly looks for all .nii files
for each file it will save a new mask with the name name_mask.nii on the path of the original image
it will skip files that end with mask.nii.

### Requirementes
- Python 3
- pip

Following can be installed with the requirements.txt file
- tqdm==4.29.1
- opencv_python_headless==4.0.0.21
- numpy==1.16.2
- MedPy==0.3.0
- Keras==2.2.4

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

    (env_name)$ git clone https://github.com/FNNDSC/brain-masking-tool
    (env_name)$ cd brain-masking-tool

install requirements from requirements.txt

    (env_name)$ pip install -r requirements.txt

to run the masking tool

    (env_name)$ python brain_mask.py --target_dir = path_to_dir

if no --target_dir is specified it will target the images directory, where you can also include images.
you will have to activate the environment everytime you would like to use the tool

### limitation
- Unet can currently only work with 256x256 images
