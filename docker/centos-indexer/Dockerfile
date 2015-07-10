FROM            quay.io/mozilla/b2g-build:0.2.9
#FROM            centos:centos6
MAINTAINER      Kendall Libby <klibby@mozilla.com>

# Install system dependencies in a single layer
ADD         system-setup.sh     /tmp/system-setup.sh
RUN         ["/tmp/system-setup.sh"]

ENV         PATH        /builds/dxr-build-env/venv/bin:/builds/dxr-build-env/clang/bin:$PATH
env         LD_LIBRARY_PATH=/builds/dxr-build-env/dxr/trilite:$LD_LIBRARY_PATH
#
# Install DXR in a single layer
ADD         dxr-setup.sh        /tmp/dxr-setup.sh
RUN         ["/tmp/dxr-setup.sh"]

# Set variable normally configured at login, by the shells parent process, these
# are taken from GNU su manual
ENV         HOME        /home/jenkins
ENV         SHELL       /bin/bash
ENV         USER        jenkins
ENV         LOGNAME     jenkins

# Declare default working folder
WORKDIR     /builds/dxr-build-env

# Set a default command useful for debugging
CMD ["/bin/bash", "--login"]