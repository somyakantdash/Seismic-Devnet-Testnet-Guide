# Contract Deploy & Interaction Full-Guide

### Offical Docs Guide - https://docs.seismic.systems/appendix/devnet

## Deploy an Encrypted Contract

1️⃣ Dependencies for WINDOWS & LINUX & VPS
```
sudo apt update && sudo apt install -y build-essential
sudo apt install cargo -y
```

2️⃣ Install Rust
```
curl https://sh.rustup.rs -sSf | sh  
. "$HOME/.cargo/env"
rustc --version
```
In Github Codespace
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
```
source $HOME/.cargo/env
```

3️⃣ Install JQ

**Windows or VPS by WSL/Ubuntu** 
```
sudo apt install -y jq
jq --version
```

**Mac**
```
brew install jq
```

4️⃣ Download Some Files
```
curl -L \
     -H "Accept: application/vnd.github.v3.raw" \
     "https://api.github.com/repos/SeismicSystems/seismic-foundry/contents/sfoundryup/install?ref=seismic" | bash
source ~/.bashrc
```

5️⃣ Run sfoundryup
```
sfoundryup
```
- This may Take Some time between 5m to 60m or more

6️⃣ Clone Repository
```
git clone --recurse-submodules https://github.com/SeismicSystems/try-devnet.git
cd try-devnet/packages/contract/
```

7️⃣ Deploy contract
```
bash script/deploy.sh
```
- A wallet is automatically created, and its details (address and faucet URL) are displayed.
- Then Get Faucet in ur Address & Proceed it

Faucet: https://faucet-2.seismicdev.net/
- U get ur address already just put it & get a faucet

## Interact with an Encrypted Contract

1️⃣ Navigate to Home Directory
```
cd $home
```

2️⃣ Install Bun
```
curl -fsSL https://bun.sh/install | bash
```

3️⃣ Install Node Dependencies
```
cd try-devnet/packages/cli/
bun install
```

4️⃣ Send Transactions
```
bash script/transact.sh
```

## How to Get your Wallet Private Key

1️⃣ Check the Keystore File
```
cd try-devnet/packages/contract/
ls
```
Look for a file named something like wallet.json or keystore.json.

2️⃣ Extract Private Key Using jq

If the wallet details are in a JSON file, use jq to extract the private key
```
cat wallet.json | jq -r '.privateKey'
```
```
cat keystore.json | jq -r '.privateKey'
```
- Replace wallet.json with the actual filename if different

```
sfoundryup --help
```
```
sfoundryup wallet export-private-key
```
