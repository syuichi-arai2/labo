FROM ubuntu:latest
  
# update
RUN apt-get -y update && apt-get install -y \
sudo \
wget \
vim \
libsm6 \
libxext6 \
libxrender-dev \
libglib2.0-0
  
#install anaconda3
WORKDIR /opt
# download anaconda package and install anaconda
# archive -> https://repo.continuum.io/archive/
RUN wget https://repo.continuum.io/archive/Anaconda3-2019.10-Linux-x86_64.sh && \
sh /opt/Anaconda3-2019.10-Linux-x86_64.sh -b -p /opt/anaconda3 && \
rm -f Anaconda3-2019.10-Linux-x86_64.sh
# set path
ENV PATH /opt/anaconda3/bin:$PATH

# update pip and conda
RUN pip install --upgrade pip

WORKDIR /
RUN mkdir /work

# install OpenCV
RUN pip install opencv-python

# install jupyterlab
ENTRYPOINT ["jupyter", "lab","--ip=0.0.0.0","--allow-root", "--LabApp.token=''"]
