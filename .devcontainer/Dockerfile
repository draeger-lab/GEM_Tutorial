# Start from a devcontainer with Python
FROM mcr.microsoft.com/devcontainers/python:3.12

# Install system dependencies (add those required by refineGEMs/SPECIMEN)
RUN apt-get update && apt-get install -y \
    git \
    curl \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Install SPECIMEN from GitHub (installs also refineGEMs plus dependencies)
RUN pip install "specimen@git+https://github.com/draeger-lab/SPECIMEN@dev"

# Add Jupyter notebook support
RUN pip install jupyter

# Set default working dir
WORKDIR /workspaces
