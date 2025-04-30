# 🛠️ Installing OpenLane on Ubuntu 24.04 LTS

This guide provides step-by-step instructions to install the OpenLane 1 on Ubuntu 24.04 LTS, along with all required dependencies such as Docker, Magic, and the Sky130 PDK.

## 📋 Table of Contents

1. [Prerequisites](#prerequisites)
2. [Install Required Packages](#install-required-packages)
3. [Install Docker](#install-docker)
4. [Clone and Set Up OpenLane](#clone-and-set-up-openlane)
5. [Verify Installation](#verify-installation)
6. [Run a Sample Design](#run-a-sample-design)
7. [Troubleshooting Tips](#troubleshooting-tips)
8. [Additional Resources](#additional-resources)

---

## Prerequisites

Ensure your system meets the following requirements:

- **Operating System**: Ubuntu 20.04 LTS or newer
- **Hardware**:
  - Quad-core CPU running at 2.0 GHz or higher
  - 8 GB RAM (16 GB recommended)
  - At least 100 GB of free disk space

---

## Install Docker

1. **Remove any old Docker versions**:

   ```bash
   sudo apt-get remove docker docker-engine docker.io containerd runc
   ```

2. **Install Docker Engine**:

   ```bash
   sudo apt install -y docker.io
   sudo usermod -aG docker $USER
   newgrp docker
   ```
 ##You must restart your operating system for the group permissions to apply.  

3. **Verify Docker installation**:

   ```bash
   sudo docker run hello-world
   ```

   You should see a message confirming Docker is installed correctly.

---
## Install Required Packages

Update your package database and install essential packages:

```bash
sudo apt-get update
sudo apt-get upgrade -y
sudo apt install -y build-essential python3 python3-venv python3-pip python3-tk curl make git
```

---
## Clone and Set Up OpenLane

1. **Clone the OpenLane repository**:

   ```bash
   cd ~
   git clone https://github.com/The-OpenROAD-Project/OpenLane.git
   cd OpenLane
   ```

2. **Build OpenLane**:

   ```bash
   make pull-openlane
   ```

   This step will download and build OpenLane along with the Sky130 PDK.

---

## Verify Installation

Run tests to verify the setup:

```bash
make
```

If all tests pass, OpenLane is set up correctly.

---

## Run a Sample Design

To run the included `spm` design:

```bash
./flow.tcl -design spm
```

This command will execute the full RTL-to-GDSII flow for the `spm` design.

---

## Troubleshooting Tips

- **Docker Permissions**: If you encounter permission issues with Docker, consider adding your user to the Docker group:

  ```bash
  sudo usermod -aG docker $USER
  newgrp docker
  ```

- **Python Dependencies**: If you face Python-related errors, ensure required packages like `click` and `pyyaml` are installed:

  ```bash
  python3 -m pip install click pyyaml
  ```

- **Magic Version Compatibility**: Ensure you're using Magic version 8.3.124 or higher, as older versions may not be compatible with the PDKs.

---

## Additional Resources

- [OpenLane Documentation](https://openlane.readthedocs.io/en/latest/getting_started/installation/installation_ubuntu.html)
- [OpenLane GitHub Repository](https://github.com/The-OpenROAD-Project/OpenLane)
- [Sky130 PDK Documentation](https://github.com/google/skywater-pdk)
- [OpenLane Installation Video Tutorial](https://www.youtube.com/watch?v=I57zcYhM1LA)

---
