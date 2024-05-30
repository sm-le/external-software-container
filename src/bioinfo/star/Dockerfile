FROM ubuntu:22.04
LABEL maintainer=smlee

# https://github.com/alexdobin/STAR::STAR VERSION
ENV VERSION 2.7.11b
ENV PACKAGES gcc make g++ wget xxd zlib1g-dev libgomp1
# Install star
RUN apt-get update && \
    apt-get install -y \
    ${PACKAGES} && \
    mkdir -p /home/bin && \
    cd /home/bin && \
    wget -O STAR-v${VERSION}.tar.gz https://github.com/alexdobin/STAR/archive/${VERSION}.tar.gz && \
    tar -zxvf STAR-v${VERSION}.tar.gz && \
    rm STAR-v${VERSION}.tar.gz && \
    cd STAR-${VERSION}/source && \
    make STAR && \
    cp STAR /usr/local/bin && \
    cd /home/bin && \
    rm -rf STAR-${VERSION} && \
    apt-get autoremove -y

# export path
ENV PATH /usr/local/bin:${PATH}
RUN echo "export PATH=$PATH" > /etc/environment