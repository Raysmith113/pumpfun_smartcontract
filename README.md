# Solana smart contract for pump.fun

> You can check frontend and backend repo as well.
> 
> https://github.com/m8s-lab/pump-fun-frontend
> 
> https://github.com/m8s-lab/pump-fun-backend

You can contact me if you want a better product.

## Available features
- All handled in smart contracts: 
Token creation and Raydium deposits are handled in the smart contract.

- Enable sniping: 
Add `Presale` phase before the launch to allow snipers.

- Raydium/Meteora migration: 
Token launchers can migrate their tokens to Raydium or Meteora as they wish after the curve is completed.

- Set curve limit and fee as stable price:
Calculate market cap in each swap instruction using oracle.

Telegram: https://t.me/microgift88

Discord: https://discord.com/users/1074514238325927956

## Test addresses and transactions
- Contract
https://solscan.io/account/Cu3ZCXsVh7xC64gWH23vjDeytWC6ZGcMRVYZAka92QTq?cluster=devnet
- Token launch tx
https://solscan.io/tx/sc1apfAXUkGHycbzPHzqcrKxEc4JVQj9zq6i26HjrRAHFR6QGPJYLLuhBRN42Gfk6Xhehji2yMHNViJUL9ga4pU?cluster=devnet
- Launched token address
https://solscan.io/token/5WFBKTKq8Ks6HDMZXEfqRTVX4oPop1Yv5kmyznJYp9hE?cluster=devnet
- Buy tx
https://solscan.io/tx/3kGJc35TScHs9YjrKqSeGjjGo3MHUjqTTdVoxp7GNUAKqB9eHsjhzWN6Se4ZjrCqC33wrUT4iZj11wZuK8sbbdeY?cluster=devnet
- Sell tx
https://solscan.io/tx/tMUqR8cYkYs9hNsA3GCmsj7HC83JdFX6naM13pgXYAY3rT6RZ5yEk9cWaXnVdTjk1josgByezjoLbuGxFD6CPQj?cluster=devnet
- Raydium migration tx
https://solscan.io/tx/2JC62ARcT3hopESk99gUQec9HVpdQwPHKnRoY9z7xiMUn4Xcoth3YnLdikuyozSXrp4Y8ez1oLCc2DM9wfyJSoYE?cluster=devnet


## Prerequites

Install Rust, Solana, and Anchor

Here's a useful link. https://anchor-lang.com/docs/installation

```bash
# check rust version
rustc --version

# check solana version
solana --version

# check anchor version
# should be 0.30.1
anchor --version

# check solana configuration
solana config get

# set solana rpc as devnet
solana config set --url devnet

# check wallet set in the config
solana balance

# generate new wallet if doesn't exist
solana-keygen new

# airdrop some devnet SOL
solana airdrop 5
```

Prepare the project
```bash
# clone the git repo
git clone https://github.com/...

# install node modules
yarn
```

## Quick Start

### Build the program

```bash
# build the program
# it will generate new keypair for the program if doesn't exist
# and it will make a build version
anchor build

# sync all keys in program
anchor keys sync

# build again if the program address in lib.rs is changed
anchor build

# you can get keypair and so file here
# ./target/deploy/pumpfun-keypair.json
# ./target/deploy/pumpfun.so
```

### Run tests on localnet

Set the cluster as localnet in `Anchor.toml`:
```bash
[provider]
cluster = "Localnet"
```

you can run the tests without having to start a local network:

```bash
anchor test --provider.cluster Localnet
```

### Test program on devnet

Set the cluster as devnet in `Anchor.toml`:
```bash
[provider]
cluster = "<DEVNET_RPC>"
```

Deploy program:
```bash
anchor deploy
```

#### Use CLI to test the program

Initialize program:
```bash
yarn script config
```

Launch a token:
```bash
yarn script launch
```

Swap SOL for token:
```bash
yarn script swap -t <TOKEN_MINT> -a <SWAP_AMOUNT> -s <SWAP_DIRECTION>
# <TOKEN_MINT>: You can get token mint when you launch a token
# <SWAP_AMOUNT>: SOL/Token amount to swap
# <SWAP_DIRECTION>: 0 - Buy token, 1 - Sell token
```

Migrate token to raydium once the curve is completed:
```bash
yarn script migrate -t <TOKEN_MINT>
# <TOKEN_MINT>: mint address of the token to be launched on the raydium
```
