# Start from a devcontainer with Python
FROM mcr.microsoft.com/devcontainers/python:3.12

# Install system dependencies (add those required by refineGEMs/SPECIMEN)
RUN apt-get update && apt-get install -y \
    git \
    curl \
    build-essential \
    unzip \
    wget \
    bzip2 \
    && rm -rf /var/lib/apt/lists/*

# Install Miniconda
ENV CONDA_DIR=/opt/conda
RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /tmp/miniconda.sh && \
    bash /tmp/miniconda.sh -b -p $CONDA_DIR && \
    rm /tmp/miniconda.sh
ENV PATH="$CONDA_DIR/bin:$PATH"


# Configure conda channels (avoid defaults to skip ToS issue)
RUN conda config --remove-key channels || true && \
    conda config --add channels conda-forge && \
    conda config --add channels bioconda

# Create conda environment with Python, Jupyter, refineGEMs, DIAMOND, and dependencies
RUN conda create -y -n tutorial python=3.12 \
    jupyter diamond && \
    conda clean -a
ENV CONDA_DEFAULT_ENV=tutorial
ENV PATH="$CONDA_DIR/envs/tutorial/bin:$PATH"

# Activate conda env for following commands
SHELL ["conda", "run", "-n", "tutorial", "/bin/bash", "-c"]

# Install SPECIMEN from GitHub
RUN pip install "specimen@git+https://github.com/draeger-lab/SPECIMEN@dev"

# Ensure Python kernel is available in Jupyter
RUN python -m ipykernel install --user --name=tutorial --display-name "Python (tutorial)"

# Set working directory
WORKDIR /workspaces

# Default command
CMD ["bash"]