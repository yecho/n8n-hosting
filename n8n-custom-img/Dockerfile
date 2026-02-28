FROM n8nio/n8n:latest

USER root

# Reinstall apk-tools: TODO always check the alpine version used for n8n:latest and according apk-tools.*apk
RUN wget -q https://dl-cdn.alpinelinux.org/alpine/v3.22/main/aarch64/apk-tools-2.14.9-r3.apk && \
    tar -xzf apk-tools-2.14.9-r3.apk -C / && \
    rm apk-tools-2.14.9-r3.apk

# Install Python and Node.js dependencies
RUN apk add --update --no-cache python3 py3-pip nodejs npm

# Install the Angular CLI globally so 'ng' is available in the shell
RUN npm install -g @angular/cli@latest

# Add node path
ENV PATH="$PATH:/opt/nodejs/node-v24.13.1/bin"

# Ensure the n8n user (node) has permission to use the project folder
RUN mkdir -p /home/node/project && chown -R node:node /home/node/project

USER node

RUN python -m venv n8n-env && source n8n-env/bin/activate
