FROM ubuntu:22.04
LABEL maintainer=smlee

# https://github.com/COMBINE-lab/salmon/releases::SALMON VERSION
# https://github.com/COMBINE-lab/salmon/blob/master/docker/Dockerfile::SALMON DOCKER BUILD
ENV VERSION 1.10.1
ENV PACKAGES gcc make g++ libboost-all-dev liblzma-dev libbz2-dev ca-certificates zlib1g-dev libcurl4-openssl-dev \
             cmake curl unzip autoconf apt-transport-https ca-certificates gnupg software-properties-common wget
# Install Salmon
RUN apt-get update && \
    apt-get install -y \
    ${PACKAGES} && \
    wget -O salmon-v${VERSION}.tar.gz https://github.com/COMBINE-lab/salmon/archive/refs/tags/v${VERSION}.tar.gz && \
    tar -zxvf salmon-v${VERSION}.tar.gz && \
    rm salmon-v${VERSION}.tar.gz && \
    cd salmon-${VERSION} && \
    mkdir build && \
    cd build && \
    cmake .. -DCMAKE_INSTALL_PREFIX=/usr/local/salmon && \
    make && \
    make install && \
    apt-get remove -y \
    ${PACKAGES} && \
    apt-get autoremove -y && \
    apt-get clean 

ENV PATH /usr/local/salmon/bin:${PATH}
ENV LD_LIBRARY_PATH /usr/local/salmon/lib:${LD_LIBRARY_PATH}

RUN echo "export PATH=$PATH" > /etc/environment
RUN echo "export LD_LIBRARY_PATH=$LD_LIBRARY_PATH" > /etc/environment

ENTRYPOINT [ "/usr/local/salmon/bin/salmon" ]


