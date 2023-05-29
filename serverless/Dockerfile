FROM ubuntu:jammy

ARG GITHUB_TOKEN

ENV DEBIAN_FRONTEND=noninteractive
ENV DEBCONF_NONINTERACTIVE_SEEN=true

# NOTE: This is needed for credentials helper to work
ENV AWS_SDK_LOAD_CONFIG=true

# Prepare setup
RUN apt-get update
RUN apt-get install -y curl
RUN apt-get install -y jq
RUN apt-get install -y python3
RUN apt-get install -y python3-pip
RUN apt-get install -y bash
RUN apt-get install -y git
RUN apt-get install -y unzip
RUN apt-get install -y npm nodejs
RUN apt-get install -y docker
RUN apt-get install -y openssh-client
RUN apt-get clean
RUN rm -rf /var/lib/apt/lists


# Install AWS CLI
RUN cd /tmp && \
    curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install

# Install pre-commit
RUN pip3 install pre-commit

# Install Serverless
RUN npm install -g serverless@3.27.0

RUN npm cache clean -f

# Setup runner
RUN mkdir -p /runner
WORKDIR /runner
