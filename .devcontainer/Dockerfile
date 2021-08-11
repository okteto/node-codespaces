FROM okteto/okteto:1.13.4 as okteto
# [Choice] Node.js version: 14, 12, 10
ARG VARIANT="14-buster"
FROM mcr.microsoft.com/vscode/devcontainers/javascript-node:0-${VARIANT}

COPY --from=okteto /usr/local/bin/okteto /usr/local/bin/okteto
COPY --from=okteto /usr/local/bin/kubectl /usr/local/bin/kubectl
COPY --from=okteto /usr/local/bin/helm /usr/local/bin/helm