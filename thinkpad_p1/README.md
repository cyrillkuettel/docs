sudo ubuntu-drivers autoinstall # should install the nvidia drivers
reboot
# check installation
nvidia-smi

# open nvidia settings
nvidia-setting
# select PRIME Profiles
# Set "Performance Mode"
reboot

# check the active GPU
glxinfo | grep "OpenGL renderer"



