

#### Dockerfile

```
FROM ubuntu:xenial

# For aws cli
RUN apt-get update \
    && apt-get install -y build-essential libssl-dev \
    && apt-get install -y git vim \
    && apt-get install -y wget curl

# https://github.com/creationix/nvm
#export NVM_DIR="$HOME/.nvm"
#[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
#[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.34.0/install.sh | bash

RUN mkdir -p /work/node-red
COPY node-red-settings.js /work/node-red
COPY flows.json /work/node-red
WORKDIR /work/node-red

ARG NVM_DIR="/root/.nvm"
ARG NODE_VERSION=8
RUN . $NVM_DIR/nvm.sh \
    && nvm install $NODE_VERSION \
    && nvm alias default $NODE_VERSION \
    && nvm use default \
    && mkdir -p /work/node-red \
    && npm install -g --unsafe-perm node-red \
    && npm install -g node-red-admin
```

