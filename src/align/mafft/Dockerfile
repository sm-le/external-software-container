FROM ubuntu:22.04
LABEL maintainer=smlee

# https://mafft.cbrc.jp/alignment/software/source.html::MAFFT VERSION
ENV VERSION=7.525

# Install MAFFT
RUN apt-get update && \
    apt-get install -y \
    wget \
    gcc \
    make && \
    cd /tmp && \
    wget -O mafft-${VERSION}-with-extensions-src.tgz https://mafft.cbrc.jp/alignment/software/mafft-${VERSION}-with-extensions-src.tgz && \
    tar -zxvf mafft-${VERSION}-with-extensions-src.tgz && \
    rm mafft-${VERSION}-with-extensions-src.tgz && \
    cd mafft-${VERSION}-with-extensions/core && \
    make clean && \
    make && \
    make install && \
    rm -rf /tmp/mafft-${VERSION}-with-extensions && \
    apt-get remove -y \
    wget \
    gcc \
    make && \
    apt-get autoremove -y && \
    apt-get clean 

ENTRYPOINT [ "/usr/local/bin/mafft" ]