# Use the argocd base image
FROM argoproj/argocd:v2.6.14 as argocd-base

# Install NodeJS and npm
USER root
RUN apt-get update && \
    apt-get install -y curl && \
    curl -sL https://deb.nodesource.com/setup_20.x | bash - && \
    apt-get install -y nodejs

# Install cdk8s
RUN npm install -g typescript cdk8s-cli cdk8s cdk8s-plus-27 constructs @types/node @types/jest jest ts-jest ts-node

# Switch back to non-root user
USER 999
