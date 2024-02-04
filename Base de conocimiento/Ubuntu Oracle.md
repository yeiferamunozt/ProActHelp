Servidor de producción - 144.22.129.225

```shell
sudo useradd -m -s /bin/bash -G sudo adminserver
sudo -u adminserver mkdir /home/adminserver/.ssh
sudo cat ~/.ssh/authorized_keys | sudo -u adminserver xargs -I{} bash -c "echo {} > /home/adminserver/.ssh/authorized_keys"
sudo chmod 700 /home/adminserver/.ssh
sudo chmod 600 /home/adminserver/.ssh/authorized_keys
sudo passwd adminserver
```

```shell
# Inatall tmux
sudo apt update
sudo apt install tmux -y
echo 'set -g default-terminal "xterm-256color"' > ~/.tmux.conf
echo 'set -g mouse on' >> ~/.tmux.conf
```

Install docker

### Uninstall old versions[](https://docs.docker.com/engine/install/ubuntu/#uninstall-old-versions)

Older versions of Docker went by the names of `docker`, `docker.io`, or `docker-engine`. Uninstall any such older versions before attempting to install a new version:

``` shell
sudo apt-get remove docker docker-engine docker.io containerd runc
```

### Install using the repository[](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)

#### Set up the repository

1.  Update the `apt` package index and install packages to allow `apt` to use a repository over HTTPS:

```shell
sudo apt-get update
sudo apt-get install \
ca-certificates \
curl \
gnupg \
lsb-release
```

2.  Add Docker’s official GPG key:
  
```shell
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

3.  Use the following command to set up the repository:

```shell
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

#### Install Docker Engine

1.  Update the `apt` package index:
  
```shell
sudo apt-get update
```

2. Install Docker Engine, containerd, and Docker Compose.

To install the latest version, run:

```shell
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
```

# Docker Engine post-installation steps

To create the `docker` group and add your user:

1.  Create the `docker` group.

```shell
sudo groupadd docker
```

2.  Add your user to the `docker` group.

```shell
sudo usermod -aG docker $USER
```

## Configure Docker to start on boot with systemd[](https://docs.docker.com/engine/install/linux-postinstall/#configure-docker-to-start-on-boot-with-systemd)

Many modern Linux distributions use [systemd](https://docs.docker.com/config/daemon/systemd/) to manage which services start when the system boots. On Debian and Ubuntu, the Docker service starts on boot by default. To automatically start Docker and containerd on boot for other Linux distributions using systemd, run the following commands:

```shell
sudo systemctl enable docker.service
sudo systemctl enable containerd.service
```

To stop this behavior, use `disable` instead.

```shell
sudo systemctl disable docker.service
sudo systemctl disable containerd.service
```

Lucky2018.
