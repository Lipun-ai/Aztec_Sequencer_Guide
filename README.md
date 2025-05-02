<div align="center">

# 👨🏻‍💻 **Aztec Sequencer Guide** 👨🏻‍💻

</div>

# 🖥️ Device/System Requirements 

![image](https://github.com/user-attachments/assets/9e7e78a8-ddeb-4e0b-90a8-46f2ab5886b3)



# Pre-Requirements 🛠

- Docker & Docker Compose

   🔺(Let run your docker in background if u are using local Device)

- Aztec Tool

- Sepolia Rpc URL



# Install All Require Dependecies

```
sudo apt-get update && sudo apt-get upgrade -y
```

* Install Node.js 

```
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash - && sudo apt update && sudo apt install -y nodejs
```

* Other Packages

```
sudo apt install curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev  -y
```


# Install Docker & Docker Compose


```
sudo apt update && sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

```
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```
sudo apt update && sudo apt install -y docker-ce && sudo systemctl enable --now docker
```

```
sudo usermod -aG docker $USER && newgrp docker
```


```
sudo curl -L "https://github.com/docker/compose/releases/download/$(curl -s https://api.github.com/repos/docker/compose/releases/latest | jq -r .tag_name)/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && sudo chmod +x /usr/local/bin/docker-compose
```


*  Verify installation

```
docker --version && docker-compose --version
```



# Install the Aztec CLI

```
bash -i <(curl -s https://install.aztec.network)
```


* Lets Config it to your corrent Shell/Path

```
echo 'export PATH="$HOME/.aztec/bin:$PATH"' >> ~/.bashrc
```

```
source ~/.bashrc
```

* Verify the Installation with-

```
aztec -h
```


* Set the correct version for the testnet

```
aztec-up alpha-testnet
```


# Load your wallet with Sepolia Faucet 

https://sepolia-faucet.pk910.de/



# Allow Incoming connections on Ports 

```
sudo ufw allow 22
sudo ufw allow ssh
sudo ufw enable
```

```
sudo ufw allow 40400
sudo ufw allow 8080
```


#  Start Your Sequencer 🍥


```
aztec start --node --archiver --sequencer \
  --network alpha-testnet \
  --l1-rpc-urls Alchemy_Sepolia_RPC \
  --l1-consensus-host-urls DRPC_eth-beacon_sepolia_RPC \
  --sequencer.validatorPrivateKey 0xYourPrivateKey \
  --sequencer.coinbase YourAddress \
  --p2p.p2pIp Your_ip
```


* Replace `Alchemy_Sepolia_RPC` with your actual one!         -From https://dashboard.alchemy.com/

![image](https://github.com/user-attachments/assets/3ccd2f62-57ab-4452-a1da-4ba9a1bf5924)


* Replace `DRPC_eth-beacon_sepolia_RPC` with your actual one            -From https://drpc.org/dashboard

![image](https://github.com/user-attachments/assets/7c73dc77-e67a-4cbe-9636-18f7e4a591f0)

* Replace `0xYourPrivateKey` with your actual EVM wallet pvt key    🔺 (dont forget to add 0x at starting)

* Replace `YourAddress` with your actual evm wallet address

* Replace `Your_ip` with your `External IP`  ... 

     -U can get External IP by running  `curl ifconfig.me`


* It will take few times to download and Sync! 🥶

![Screenshot 2025-05-02 164041](https://github.com/user-attachments/assets/17dd3df2-3136-4dd0-8dde-70cf19291503)


* The Successfull Running Should Look like this 👇


![Screenshot 2025-05-02 172143](https://github.com/user-attachments/assets/73292689-ff6f-4c35-a74d-34bb0e427a9b)







