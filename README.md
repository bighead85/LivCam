LivCam
======

using raspistill web by TimJuni https://github.com/TimJuni/raspistillWeb

Changes due to utilising the PICE case by http://elsondesigns.com

Major changes are permentant camer flip to work with case, reboot and shut down buttons in menu.

Installation Notes (from TimJuni)
I'll provide a guide to install raspistillWeb based on the tutorial from the pyramid framework to install raspistillWeb in a seperate python environment, so that your systems python environment is not effected.

Make sure that your raspbian and your camera is working. Try to make a photo with raspistill to verify that your camera is working.

Install python2.7-dev (if not already on your system), virtualenv, setuptools and exif:

sudo apt-get install python2.7-dev python-virtualenv python-setuptools exif

Create a virtual environment for python (sudo not required and not recommended):

mkdir ~/Development (Or another directory)
cd ~/Development
virtualenv --no-site-packages env
cd env
Install raspistillWeb

git clone https://github.com/bighead85/LivCam.git
cd raspistillWeb
../bin/python setup.py develop

Run raspistillWeb

../bin/pserve development.ini
surf http://<adress of your pi>:6543


To run on start up: create the following .sh file
#!/bin/bash
cd /home/pi/path/to/Development/env/raspistillWeb
../bin/pserve development.ini

then at the end of 'crontab -e'

@reboot /home/pi/path/to/script.sh
