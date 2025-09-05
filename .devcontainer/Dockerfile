# Start from a devcontainer with Python
FROM mcr.microsoft.com/devcontainers/python:3.12

# Install system dependencies (add those required by refineGEMs/SPECIMEN)
RUN apt-get update && apt-get install -y \
    git \
    curl \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Install refineGEMs base (from PyPI)
RUN pip install refinegems==2.0.0b1

# Install dependencies that cannot be specified in pyproject.toml for refineGEMs
RUN pip install "model-polisher@git+https://github.com/draeger-lab/MPClient"
RUN pip install "masschargecuration@git+https://github.com/draeger-lab/MassChargeCuration"
RUN pip install "bofdat@git+https://github.com/draeger-lab/BOFdat"

# Install SPECIMEN from GitHub
RUN pip install "specimen@git+https://github.com/draeger-lab/SPECIMEN@v0.0.dev2"

# Add Jupyter notebook support
RUN pip install notebook jupyterlab ipykernel

# Set default working dir
WORKDIR /workspaces
