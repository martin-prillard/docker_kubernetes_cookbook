# Docker & Kubernetes Cookbook

This repository contains Jupyter notebooks for learning Docker and Kubernetes concepts.

## Prerequisites

- Python 3.8 or higher
- uv (fast Python package installer) - [Installation instructions](https://github.com/astral-sh/uv#installation)
- Docker Desktop (for macOS/Windows) or Minikube (for Linux/macOS/Windows)
- kubectl (Kubernetes command-line tool)

## Setting up Kubernetes

You can use either Docker Desktop or Minikube to run a local Kubernetes cluster.

### Option 1: Docker Desktop (Recommended for macOS/Windows)

1. **Install Docker Desktop**
   - Download from [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
   - Install and launch Docker Desktop

2. **Enable Kubernetes**
   - Open Docker Desktop
   - Go to Settings → Kubernetes
   - Check "Enable Kubernetes"
   - Click "Apply & Restart"
   - Wait for Kubernetes to start (you'll see a green indicator)

3. **Verify Installation**
   ```bash
   kubectl cluster-info
   kubectl get nodes
   ```

### Option 2: Minikube (Cross-platform)

1. **Install Minikube**
   - macOS (using Homebrew):
     ```bash
     brew install minikube
     ```
   - Linux/Windows: Follow instructions at [https://minikube.sigs.k8s.io/docs/start/](https://minikube.sigs.k8s.io/docs/start/)

2. **Install kubectl**
   - macOS (using Homebrew):
     ```bash
     brew install kubectl
     ```
   - Linux/Windows: Follow instructions at [https://kubernetes.io/docs/tasks/tools/](https://kubernetes.io/docs/tasks/tools/)

3. **Start Minikube**
   ```bash
   minikube start
   ```

4. **Verify Installation**
   ```bash
   kubectl cluster-info
   kubectl get nodes
   ```

## Setting up Python Environment

1. **Install uv** (if not already installed)
   - macOS/Linux:
     ```bash
     curl -LsSf https://astral.sh/uv/install.sh | sh
     ```
   - Windows:
     ```powershell
     powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
     ```
   - Or using Homebrew (macOS):
     ```bash
     brew install uv
     ```

2. **Create virtual environment and install dependencies**
   ```bash
   uv venv
   ```

3. **Activate the virtual environment**
   - macOS/Linux:
     ```bash
     source .venv/bin/activate
     ```
   - Windows:
     ```bash
     .venv\Scripts\activate
     ```

4. **Install dependencies**
   ```bash
   uv pip install -e .
   ```
   
   Or using uv sync (if you have a lockfile):
   ```bash
   uv sync
   ```

## Launching JupyterLab

1. **Make sure your virtual environment is activated**

2. **Start JupyterLab**
   ```bash
   jupyter lab
   ```

3. **Open notebooks**
   - JupyterLab will open in your default web browser
   - Navigate to the notebook files:
     - `intro_kubernetes.ipynb` - Introduction to Kubernetes
     - `dockercoins_docker.ipynb` - Docker examples
     - `dockercoins_kubernetes.ipynb` - Kubernetes examples

## Using the Notebooks

- The notebooks contain interactive examples and exercises
- Make sure your Kubernetes cluster is running before executing Kubernetes-related cells
- Some notebooks may require additional setup or resources - follow the instructions within each notebook

## Troubleshooting

### Kubernetes cluster not accessible
- **Docker Desktop**: Ensure Kubernetes is enabled in Settings → Kubernetes
- **Minikube**: Run `minikube status` to check if it's running. If not, run `minikube start`

### kubectl not found
- Ensure kubectl is installed and in your PATH
- For Minikube, you may need to run: `minikube kubectl -- get nodes` (or configure kubectl: `eval $(minikube docker-env)`)

### JupyterLab not starting
- Ensure your virtual environment is activated
- Verify jupyterlab is installed: `uv pip list | grep jupyterlab`
- Try reinstalling: `uv pip install --upgrade jupyterlab`

## Resources

- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Docker Documentation](https://docs.docker.com/)
- [JupyterLab Documentation](https://jupyterlab.readthedocs.io/)

