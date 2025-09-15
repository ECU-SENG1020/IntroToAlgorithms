FROM mambaorg/micromamba:latest

ARG USERNAME=vscode
ARG UID=1000
ARG GID=1000

# Install OS deps (customize)
USER root
RUN apt-get update && apt-get install -y --no-install-recommends git curl ca-certificates && rm -rf /var/lib/apt/lists/*

# Create non-root user
RUN groupadd -g ${GID} ${USERNAME} \
  && useradd -m -u ${UID} -g ${GID} -s /bin/bash ${USERNAME} \
  && mkdir -p /workspace && chown -R ${USERNAME}:${USERNAME} /workspace /opt/conda

USER ${USERNAME}
WORKDIR /workspace
ENV MAMBA_ROOT_PREFIX=/opt/conda

# (Don't create the env here so postCreateCommand can run as the container user)