FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

ARG KUBECTL_VERSION=v1.36.0
ARG KIND_VERSION=v0.32.0
ARG HELM_VERSION=v4.2.1
ARG KUSTOMIZE_VERSION=v5.8.1

RUN apt-get update && \
    apt-get install -y \
      curl \
      wget \
      git \
      jq \
      unzip \
      ca-certificates && \
    rm -rf /var/lib/apt/lists/*

# kubectl
RUN curl -fsSL \
    https://dl.k8s.io/release/${KUBECTL_VERSION}/bin/linux/amd64/kubectl \
    -o /usr/local/bin/kubectl && \
    chmod +x /usr/local/bin/kubectl

# kind
RUN curl -fsSL \
    https://kind.sigs.k8s.io/dl/${KIND_VERSION}/kind-linux-amd64 \
    -o /usr/local/bin/kind && \
    chmod +x /usr/local/bin/kind

# helm
RUN curl -fsSL https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

# kustomize
RUN curl -fsSL \
    https://github.com/kubernetes-sigs/kustomize/releases/download/kustomize%2F${KUSTOMIZE_VERSION}/kustomize_${KUSTOMIZE_VERSION}_linux_amd64.tar.gz \
    -o /tmp/kustomize.tar.gz && \
    tar -xzf /tmp/kustomize.tar.gz -C /usr/local/bin && \
    rm /tmp/kustomize.tar.gz

# yq
RUN wget -qO /usr/local/bin/yq \
    https://github.com/mikefarah/yq/releases/latest/download/yq_linux_amd64 && \
    chmod +x /usr/local/bin/yq
