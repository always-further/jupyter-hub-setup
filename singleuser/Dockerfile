FROM python:3.11-slim

ENV DEBIAN_FRONTEND=noninteractive \
    PYTHONUNBUFFERED=1

# System deps and a minimal init (tini)
RUN apt-get update && apt-get install -y --no-install-recommends \
        tini git \
    && rm -rf /var/lib/apt/lists/*

# JupyterHub singleuser + JupyterLab + basic kernel
RUN pip install --no-cache-dir --upgrade pip \
    && pip install --no-cache-dir \
        jupyterhub==4.* \
        jupyterlab \
        ipykernel

# Create an unprivileged user matching Jupyter stacks conventions
RUN useradd -m -s /bin/bash -u 1000 jovyan \
    && chown -R jovyan:jovyan /home/jovyan

USER jovyan
WORKDIR /home/jovyan

# DockerSpawner will invoke jupyterhub-singleuser; keep CMD consistent
CMD ["jupyterhub-singleuser"]

