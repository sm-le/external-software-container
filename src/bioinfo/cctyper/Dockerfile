FROM python:3.11-slim-bullseye
LABEL maintainer=smlee

# https://github.com/Russel88/CRISPRCasTyper?tab=readme-ov-file#cctyperhow: CRISPRCasTyper VERSION
ENV VERSION 1.8.0

# Install MultiQC
RUN apt-get update && \
    apt-get install -y \
    git && \
    pip install --quiet --upgrade pip && \
    pip install git+https://github.com/sm-le/cctyper-fork.git

RUN echo "export PATH=$PATH" > /etc/environment

CMD [ "python" ]