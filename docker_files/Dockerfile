# Use the official Python image as the base, specifying version 3.8.17
FROM python:3.8.17-slim

# Install necessary dependencies
RUN apt-get update && apt-get install -y \
    wget \
    curl \
    build-essential \
    && apt-get clean


# Set the working directory
WORKDIR /app

# Copy the Pipfile and Pipfile.lock (if you have a Pipfile.lock already)
COPY Pipfile /app/

# Install pipenv
RUN pip install pipenv

# Generate Pipfile.lock
RUN pipenv lock

# Install dependencies using pipenv with verbose output
RUN pipenv install --system --deploy --verbose

# Copy the rest of the project files
COPY . /app

# Install JupyterLab
RUN pip install jupyterlab

# Configure JupyterLab to disable token authentication
RUN mkdir -p /root/.jupyter && echo "c.NotebookApp.token = ''" >> /root/.jupyter/jupyter_notebook_config.py

# Default command to run Jupyter Lab
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--allow-root", "--no-browser"]
