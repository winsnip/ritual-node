# Ritual Node

## Links
- [Discord](https://discord.gg/cGHv6kRK)
- [Web](https://ritual.academy/nodes/setup/)
- [Twitter](https://x.com/ritualnet)

## System Requirements

- **RAM**: 16 GB
- **CPU**: 4 cores
- **Disk Space**: 500 GB

## Prequisitions

- **Docker**
- **Docker Compose**
- **EVM Wallet With ETH Token Base Mainnet Around $15**

## Installation ⚙️

```bash
sudo apt update -y && sudo apt upgrade -y && sudo apt -qy install curl git jq lz4 build-essential screen
```


# Clone Repository

```
git clone https://github.com/ritual-net/infernet-container-starter
```

```
cd infernet-container-starter
```

# Pull Image

```
docker pull ritualnetwork/hello-world-infernet:latest
```

# Node Configurations

```
nano deploy/config.json
```

```
RPC URL : https://mainnet.base.org/
```

```
Private Key : Enter your private key (throwaway wallet). Add “0x” to your key if it does not start with 0x.
```

```
Registry : 0x3B1554f346DFe5c482Bb4BA31b880c1C18412170
```

***Edit this too***
```
"trail_head_blocks": 3
"snapshot_sync": {
    "sleep": 3,
    "starting_sub_id": 160000,
    "batch_size": 800,
    "sync_period": 30
},
```

```
nano projects/hello-world/container/config.json
```

```
RPC URL : https://mainnet.base.org/
```

```
Private Key : Enter your private key (throwaway wallet). Add “0x” to your key if it does not start with 0x.
```

```
Registry : 0x3B1554f346DFe5c482Bb4BA31b880c1C18412170
```

***Edit this too***
```
"trail_head_blocks": 3
"snapshot_sync": {
    "sleep": 3,
    "starting_sub_id": 160000,
    "batch_size": 800,
    "sync_period": 30
},
```

# Change Registry Address

```
nano projects/hello-world/contracts/script/Deploy.s.sol
```

```
Registry : 0x3B1554f346DFe5c482Bb4BA31b880c1C18412170
```

# Edit Makefile

```
nano projects/hello-world/contracts/Makefile
```

```
Update sender’s address with your private key

Private Key : Enter your private key (throw away wallet). Add “0x” to your key if it does not start with 0x.
```

```
RPC URL : https://mainnet.base.org/
```

# Update Deployment Script

```
nano projects/hello-world/contracts/script/Deploy.s.sol
```

```
Address Registery : 0x3B1554f346DFe5c482Bb4BA31b880c1C18412170
```

# Edit Node Version

```
nano deploy/docker-compose.yaml
```

```
image: ritualnetwork/infernet-node:1.4.0
```

# Install Foundry

```
cd ..

make sure you out from folder infernet-container-starter
```

```
mkdir foundry && cd foundry
```

```
curl -L https://foundry.paradigm.xyz | bash
```

```
source ~/.bashrc
```

```
foundryup
```

```
![download foundry](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*edO-JsCQjAdyKn_4DCs-Hg.png)
```

# Install Dependencies

```
cd .. && cd infernet-container-starter/projects/hello-world/contracts
```

```
rm -rf lib/forge-std
```

```
forge install --no-commit foundry-rs/forge-std
```

```
ls lib/forge-std
```

```
foundryup
```

```
![install dependencies](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*j8rRRziGIBALAObSnAYK2g.png)
```

```
rm -rf lib/infernet-sdk
```

```
forge install --no-commit ritual-net/infernet-sdk
```

```
ls lib/infernet-sdk
```

```
if got error you can run command below :

git init -y

and rerun forge install --no-commit ritual-net/infernet-sdk
```

# Deploy Consumer Contract

```
docker compose -f infernet-container-starter/deploy/docker-compose.yaml up -d
```

```
make sure you at folder infernet-container-starter

project=hello-world make deploy-contracts
```

```
![deploy contract](https://ritual.academy/wp-content/uploads/2024/06/Run-saysgm.jpg)
```

```
Congratulations!
```

# Call Contract

```
![contract created](https://ritual.academy/wp-content/uploads/2024/06/New-Contract-Address.png)
```

```
Edit your CallContract.s.sol file by inserting the new contract address based on image above.
```

```
make sure you at folder infernet-container-starter

nano projects/hello-world/contracts/script/CallContract.s.sol
```

```
project=hello-world make call-contract
```

```
![Call Contract](https://ritual.academy/wp-content/uploads/2024/06/Call-Contract.jpg)
```

# Verify Node

```
docker logs infernet-node
```

***DONASI***

kalo mau bayarin kopi https://trakteer.id/Winsnipsupport/tip