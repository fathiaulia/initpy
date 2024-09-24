FROM vicamo/pyenv:3.11-slim-bullseye

# Install necessary packages
RUN apt-get update && \
    apt-get install -y curl git && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Create non-root user and set up the home directory
RUN useradd -m -s /bin/bash dqlab

# Switch to the non-root user
USER dqlab
WORKDIR /home/dqlab/workspace

# Install Poetry
RUN curl -sSL https://install.python-poetry.org | python3 -
    
# Set Poetry configuration
ENV PATH="/home/dqlab/.local/bin:$PATH"

# Define entrypoint when container start
ENTRYPOINT ["/bin/bash", "-c", "cd /home/dqlab/workspace && exec /bin/bash"]
