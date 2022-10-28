# Network Threat Hunting Workshop - BSides Orlando

Welcome to BSides Orlando and today's training!

The entirety of the instructions will be available in this GitHub Repo. To save a copy for reference:
- `git clone https://github.com/Oofles/network-threat-hunting-workshop.git`

## 1. OS Requirements and Setup

There are multiple ways to build the local environment, the following instructions will walk through 4 different options: 
- Option 1: Linux OS
- Option 2: Windows with WSL
- Option 3: Windows with Virtual Machine
- Option 4: MacOS 

Quick-Start Prerequisites:
- Linux machine or VM is preferred
- Docker
- Git

### Option 1: Linux OS

These instructions are built assuming a Debian based architecture (like Ubuntu). If you are using a RHEL based OS like CentOS, the same instructions can be followed by replacing `apt` with `yum` or `dnf`.

1. Install prerequisites
```bash
sudo apt update
sudo apt install git docker.io
```

### Option 2: Windows with WSL

Windows Subsystem for Linux (WSL) allows you to install a full Linux distribution inside Windows without the need for dual-boot. Requirements for WSL:
- Windows 10 version 2004 or higher
- Windows 11

1. Open PowerShell and install WSL (This will automatically install Ubuntu as well)
```powershell
wsl --install
```

>Note: This will require a reboot.

2. Open the Ubuntu app and update 
```bash
sudo apt update && sudo apt upgrade
sudo apt install git
```

3. Install Docker Desktop for Windows
- Navigate to: https://docs.docker.com/desktop/install/windows-install/
- Download the installer and follow the instructions


### Option 3: Windows with Virtual Machine

Friends don't let friends use VirtualBox.

1. Install VMWare Workstation Player
- https://customerconnect.vmware.com/en/downloads/details?downloadGroup=WKST-PLAYER-1624&productId=1039&rPId=91446

2. Download the latest version of Ubuntu 20.04 (Choose the VMware Image)
- https://www.linuxvmimages.com/images/ubuntu-2004/

3. Import the image and start

4. Update and Install prereqs
```bash
sudo apt update && sudo apt upgrade
sudo apt install git
```

### Option 4: MacOS 

Good luck... I don't have a Mac anymore to test on. You should be able to simply install Docker for Mac and use Mac's basic command-line features since it's still a *nix based OS. 

## 2. Setup environment

>Note: If using WSL, you may not need to use `sudo`.

1. Clone the repo
```bash
mkdir ~/bsidesorlando-th
cd ~/bsidesorlando-th
git clone https://github.com/Oofles/network-threat-hunting-workshop.git
```

2. Pull down the containers:
```bash
docker pull oofles/th-kibana
docker pull oofles/th-elasticsearch
```

3. Create and start the containers
```
sudo docker network create th-elastic
sudo docker run --name th-kibana --net th-elastic -p 5601:5601 -e "ELASTICSEARCH_HOSTS=http://th-elasticsearch:9200" oofles/th-kibana
sudo docker run --name th-elasticsearch --net th-elastic -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" oofles/th-elasticsearch
```

## 3. Modules
The instructions for the various modules are below:

- [1-Email Header Analysis](1-Email_Header_Analysis.md)
- [2-Bidirectional C2](2-Bidirectional_C2.md)
- [3-Lateral Movement](3-Lateral_Movement.md)
- [4-Exfiltration](4-Exfiltration.md)
