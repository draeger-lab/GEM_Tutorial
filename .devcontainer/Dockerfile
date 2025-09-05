# Start from a devcontainer with Python
FROM mcr.microsoft.com/devcontainers/python:3.12

# Install system dependencies (add those required by refineGEMs/SPECIMEN)
RUN apt-get update && apt-get install -y \
    git \
    curl \
    build-essential \
    unzip \
    && rm -rf /var/lib/apt/lists/*

# Install DIAMOND
RUN curl -L https://github.com/bbuchfink/diamond/releases/download/v3.3.1/diamond-linux64.tar.gz \
    -o /tmp/diamond.tar.gz && \
    tar -xzf /tmp/diamond.tar.gz -C /usr/local/bin --strip-components=1 diamond && \
    rm /tmp/diamond.tar.gz && chmod +x /usr/local/bin/diamond

# Install SPECIMEN from GitHub (installs also refineGEMs plus dependencies)
RUN pip install "specimen@git+https://github.com/draeger-lab/SPECIMEN@dev"

# Add Jupyter notebook support
RUN pip install jupyter

# Add DIAMOND to PATH
ENV PATH="/opt/diamond:$PATH"

# Set default working dir
WORKDIR /workspaces
