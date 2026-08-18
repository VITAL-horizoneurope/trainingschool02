# VITAL Training School 2 Tutorials with Docker

## Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Tutorials Overview](#tutorials-overview)
- [Development Notes](#development-notes)
- [CI/CD](#cicd)

## Features

- **Multi-Language Support**: Examples in **Python** and **C++**.
- **Containerized Environment**: Fully Dockerized setup for consistent development and deployment.
- **Scientific Libraries**: Pre-configured with **VItA**, **VTK**, **OpenCOR**, **PETSc**, and more.
- **Jupyter Lab Integration**: Interactive notebooks for tutorials and experimentation.
- **Automated CI/CD**: GitHub Actions workflow for building and publishing Docker images.

## Prerequisites

To run this project, you need to have **Docker** and **Docker Compose** installed on your system.
### git
Make sure you have git installed on your laptop: https://git-scm.com/
### Server to run graphical applications (X server)
- **Windows**: download VcXsrv from https://vcxsrv.com/ and follow the installation instructions.
- **Mac**: download and install XQuartz from https://www.xquartz.org/. After installation:
  - Open XQuartz.
  - Go to Settings (or Preferences) > Security.
  - Check the box: "Allow connections from network clients".
  - Restart XQuartz: You must completely quit and restart XQuartz for this change to take effect.
  - Open your Mac terminal and run:
    ```bash
    xhost +localhost
    ```

*Note*: Ensure you run this server before running the Docker container.


### Installing Docker & Docker Compose

- **Windows**:
  - Install [Docker Desktop for Windows](https://docs.docker.com/desktop/install/windows-install/).
  - Ensure WSL 2 is enabled for better performance.
  - *Note*: Ensure you run Docker before running the container.

- **Mac**:
  - Install [Docker Desktop for Mac](https://docs.docker.com/desktop/install/mac-install/).
  - Supports both Intel and Apple Silicon chips.
  - *Note*: Ensure you run Docker before running the container.

- **Linux**:
  - Install [Docker Engine](https://docs.docker.com/engine/install/) for your distribution.
  - Install the [Docker Compose plugin](https://docs.docker.com/compose/install/linux/).
  - *Note*: Ensure your user is added to the `docker` group to run commands without `sudo`.
    ```bash
    sudo usermod -aG docker $USER
    newgrp docker
    ```
    To test it, run:
    ```bash
    docker run hello-world
    ```
  - To launch GUI applications (Fiji/ImageJ and ilastik) from inside the Docker container, on a terminal (on your physical machine) run:
    ```bash
    xhost +local:docker
    ```

### Potential errors:

If you get the following error when installing docker in Ubuntu:

`E: Conflicting values set for option Signed-By regarding source https://download.docker.com/linux/ubuntu/ jammy: /etc/apt/keyrings/docker.gpg != /etc/apt/keyrings/docker.asc
E: The list of sources could not be read.`

Then try:

`sudo rm /etc/apt/sources.list.d/docker.list`

Then run 

`sudo apt update`


## Getting Started

To start the environment locally for development:

1.  Clone the [trainingschool02](https://github.com/VITAL-horizoneurope/trainingschool02) GitHub repository (``refactored`` branch) and enter the tutorials directory:
    ```bash
    git clone -b refactored https://github.com/VITAL-horizoneurope/trainingschool02.git
    cd trainingschool02/Tutorials_with_Docker
    ```

2.  Run the following command (pull and run the latest images from GitHub Container Registry):
    - **Linux and Windows**:
    ```bash
    docker compose -f docker-compose.prod.yml up -d
    ```
    - **Mac**:
    ```bash
    docker compose -f docker-compose.prod.mac.yml up -d
    ```

3.  Access Jupyter Lab:
    - Open your browser and navigate to the URL displayed in the terminal (usually `http://127.0.0.1:8888/lab`).
    - The token will be provided in the improved launch logs.

4. To shut down the Container and the Network that were created specifically by the *.yml file:
    - **Linux and Windows**:
    ```bash
    docker compose -f docker-compose.prod.yml down
    ```
    - **Mac**:
    ```bash
    docker compose -f docker-compose.prod.mac.yml down
    ```
*Note*: Since you are not building the Docker images locally in your machine, restart from step 2 everytime you shut down the Container or your machine.

## Tutorials Overview

- **tutorial_2_5_Argus_Ghitti_Davis**: From anatomical images to functional models (Tutorial 2); Generation and calibration of computational cardiovascular models (Tutorial 5).
- **tutorial_4_Hoogeveen_Hermeling**: From devices to datasets, data recording & processing (available to run outside Docker as well, in ``trainingschool02/Day2_Hermeling_Hoogeveen/``).
- **tutorial_6_Giudici**: Arterial constitutive modelling (available to run outside Docker as well, in ``trainingschool02/Day4_Giudici_Tutorial6/``).
- **tutorial_6_MasoTalou_SharifzadehKermani**: Microvascular modelling & VItA integration. Please visit https://github.com/AlirezaSharif/vital_multiscale.

## Development Notes

### Local Development

To start the environment locally for development, **build** and start the container:
```bash
docker compose up --build
```

### Rebuilding C++ Examples

If you need to rebuild C++/VItA examples, ensure you are in the correct build directory within the container.
1.  Open a terminal in Jupyter Lab (or attach to the running container).
2.  Navigate to the build directory (e.g., inside `tutorial_6_MasoTalou_SharifzadehKermani/vital_multiscale` or similar if applicable, checking structure).
    *Note: Specific build paths may vary based on the tutorial's internal structure.*

## CI/CD

This repository is equipped with a GitHub Actions workflow that automatically builds and publishes the Docker image to the GitHub Container Registry (GHCR) when a new release tag (e.g., `v1.0.0`) is pushed.

For detailed setup and usage instructions, please refer to [GITHUB_SETUP.md](GITHUB_SETUP.md).
