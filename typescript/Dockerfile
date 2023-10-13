# Use the argocd base image
FROM node:20-alpine

# Add system packages required for native dependencies
RUN apk add --no-cache make gcc g++ python3 curl jq rsync

# Install yq
RUN curl -L https://github.com/mikefarah/yq/releases/download/v4.35.1/yq_linux_amd64 -o /usr/bin/yq && \
    chmod +x /usr/bin/yq

# Install cdk8s
RUN npm install -g @types/node @types/jest typescript cdk8s-cli cdk8s cdk8s-plus-27 constructs jest ts-jest ts-node

# Add your configuration file to the image
COPY ./plugin.yaml /home/argocd/cmp-server/config/plugin.yaml

RUN echo $HOME

# Create a custom global cache directory and set its permission
RUN mkdir -p /tmp/npm-cache && chown -R 999:0 /tmp/npm-cache

# Setting custom npm cache directory
RUN npm config -g set cache /tmp/npm-cache

# Environment variable for home directory
ENV HOME=/home/node

# Switch back to non-root user
USER 999

# Default Command to keep the container running
CMD ["tail", "-f", "/dev/null"]
