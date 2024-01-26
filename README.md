# santiment-network-node

```console
# update and docker installation
sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo docker run hello-world
```

```console
# necessary configurations:
sudo mkdir -p /opt/sanchain/readonly
cd /opt/sanchain/readonly

sudo git clone https://github.com/santiment/sanr-pos-network.git .
sudo mv env.example .env
sudo nano .env

# EXTERNAL_IP=Enter the IP address of the server - exit with CTRL X Y ENTER.
sudo ln -s docker-compose-readonly.yml docker-compose.yml
sudo docker compose up -d
