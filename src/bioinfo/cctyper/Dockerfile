FROM continuumio/miniconda3:latest
LABEL maintainer=smlee

RUN conda create -n cctyper -c conda-forge -c bioconda -c russel88 cctyper
RUN echo "source activate cctyper" > ~/.bashrc
ENV PATH /opt/conda/envs/cctyper/bin:$PATH
ENV CCTYPER_DB "/opt/conda/envs/cctyper/db"

CMD [ "python" ]