FROM ubuntu:22.04
LABEL maintainer=smlee
# https://www.bioinformatics.babraham.ac.uk/projects/download.html#fastqc AND
# https://github.com/s-andrews/FastQC/releases::FASTQC VERSION
ENV VERSION 0.12.1
ENV PACKAGES unzip default-jre perl wget
# Install FastQC
RUN apt-get update && \
    apt-get install -y \
    ${PACKAGES} && \
    cd /opt && \
    wget -O fastqc-v${VERSION}.zip https://www.bioinformatics.babraham.ac.uk/projects/fastqc/fastqc_v${VERSION}.zip && \
    unzip fastqc-v${VERSION}.zip && \
    rm fastqc-v${VERSION}.zip && \
    cd FastQC && \
    chmod +x fastqc && \
    apt-get remove -y \
    unzip && \
    apt-get autoremove -y && \
    apt-get clean 

# export path
ENV PATH /opt/FastQC:${PATH}

RUN echo "export PATH=$PATH" > /etc/environment

