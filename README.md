# 🚀 Union Node Setup Guide

Welcome to the Union Node setup guide. Follow these steps to run your own node on the Union network!

---

## 📋 Requirements

**Minimum Hardware:**
- **OS:** Linux (x86_64 or aarch64)
- **CPU:** 16+ cores or vCPUs
- **RAM:** 64GB+
- **Storage:** 500GB+

> 💡 Higher specs are better for stability.

---

## ⚙️ Install `uniond`

### Option 1: Prebuilt Binary
```bash
wget [link-to-binary]
chmod +x uniond
sudo mv uniond /usr/local/bin/
```

### Option 2: Docker
```bash
docker pull ghcr.io/unionlabs/uniond-release:v0.25.0
```

---

## 🛠️ Initialize Your Node

Set your node name and chain ID:
```bash
export MONIKER="your-node-name"
export CHAIN_ID="union-testnet-9"
uniond init $MONIKER --chain-id $CHAIN_ID
```

Download the `genesis.json`:
```bash
curl -o ~/.union/config/genesis.json https://union.build/genesis.json
```

Configure seed nodes and RPC endpoints in:
```bash
~/.union/config/config.toml
```

---

## 🚀 Start the Node

Run your node:
```bash
uniond start
```

For production, use **systemd** or **Docker Compose** for better process management.

---

## 💸 Get Testnet Tokens

Request tokens from the [Union Faucet](https://union.build/faucet).

---

## 🏛️ Become a Validator

Create your wallet:
```bash
uniond keys add my_wallet
```

Submit your validator transaction:
```bash
uniond tx staking create-validator \
  --from my_wallet \
  --amount 1000000muno \
  --pubkey $(uniond tendermint show-validator) \
  --moniker "your-node-name" \
  --chain-id $CHAIN_ID \
  --commission-rate "0.1" \
  --commission-max-rate "0.2" \
  --commission-max-change-rate "0.01" \
  --min-self-delegation "1"
```

> 🎉 Congratulations! You are now a Union network validator.

---

# 📚 Resources
- [Official Union Docs](https://docs.union.build/)
- [Union Discord](https://discord.gg/union)

---

_Stay synced, stay secure!_ 🌐
