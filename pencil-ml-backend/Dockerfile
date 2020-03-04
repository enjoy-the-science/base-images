FROM continuumio/miniconda3

COPY ./environment.yml /etc/env/

RUN apt-get install -y curl

RUN conda update -n base -c defaults conda

RUN conda env update -f /etc/env/environment.yml && conda clean -afy

RUN find /opt/conda/ -follow -type f -name '*.a' -delete \
    && find /opt/conda/ -follow -type f -name '*.pyc' -delete \
    && find /opt/conda/ -follow -type f -name '*.js.map' -delete