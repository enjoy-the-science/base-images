FROM continuumio/miniconda3

COPY ./environment.yml /etc/env/

RUN apt-get install -y curl

RUN conda update -n base -c defaults conda

# We're installing heavy deps separately to avoid oversized FS layers
RUN conda install cudnn==7.6.5
RUN conda install ffmpeg==4.0
RUN conda install mkl==2019.5
RUN conda install qt==5.9.7
RUN conda install cudatoolkit==10.0.130
RUN conda install pytorch==1.3.1

RUN conda env update -f /etc/env/environment.yml
RUN conda clean -afy

RUN find /opt/conda/ -follow -type f -name '*.a' -delete \
    && find /opt/conda/ -follow -type f -name '*.pyc' -delete \
    && find /opt/conda/ -follow -type f -name '*.js.map' -delete