# Use the argocd base image
FROM node:20-alpine

# Add system packages required for native dependencies
RUN apk add --no-cache make gcc g++ python3 curl

# Install yq
RUN apk add --no-cache curl && \
    curl -L https://github.com/mikefarah/yq/releases/download/v4.35.1/yq_linux_amd64 -o /usr/bin/yq && \
    chmod +x /usr/bin/yq

# Install cdk8s
RUN npm install -g @types/node @types/jest typescript cdk8s-cli cdk8s cdk8s-plus-27 constructs jest ts-jest ts-node

RUN echo $HOME

# Fix NPM cache folder permissions
RUN mkdir -p /.npm && chown -R 999:0 /.npm

ENV HOME=/home/node

# Switch back to non-root user
USER 999

# Default Command to keep the container running
CMD ["tail", "-f", "/dev/null"]