FROM python:3.11-slim-bullseye
LABEL maintainer=smlee

# https://github.com/MultiQC: MULTIQC VERSION
ENV VERSION 1.22

# Install MultiQC
RUN apt-get update && \
    apt-get install -y \
    git && \
    pip install --quiet --upgrade pip && \
    pip install git+https://github.com/MultiQC/MultiQC.git@v${VERSION}

RUN echo "export PATH=$PATH" > /etc/environment

CMD [ "python" ]