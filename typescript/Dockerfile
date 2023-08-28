# Use the argocd base image
FROM node:20-alpine

# Add system packages required for native dependencies
RUN apk add --no-cache make gcc g++ python3 curl

# Install cdk8s
RUN npm install -g typescript cdk8s-cli cdk8s cdk8s-plus-27 constructs @types/node @types/jest jest ts-jest ts-node

# Switch back to non-root user
USER 999
