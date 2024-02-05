### Initialize Chain

```bash
wget https://github.com/crossfichain/crossfi-node/releases/download/v0.1.1/mineplex-2-node._v0.1.1_linux_amd64.tar.gz && tar -xf mineplex-2-node._v0.1.1_linux_amd64.tar.gz
git clone https://github.com/crossfichain/mainnet.git
./mineplex-chaind start --home ./mainnet
```

## Run a validator

1. Sync your node using instruction above
2. Create your key by running `./mineplex-chaind--home ./mainnet keys add my_validator`
3. Get address from commands output and top in up with some amount of MPX
3. Run transaction to create a validator:
```bash
./mineplex-chaind --home ./mainnet tx staking create-validator \
  --amount=1000000000000000000mpx \
  --pubkey=$(./mineplex-chaind --home ./mainnet tendermint show-validator) \
  --moniker="My Fist Validator" \
  --chain-id="mineplex-mainnet-1" \
  --commission-rate="0.10" \
  --commission-max-rate="0.20" \
  --commission-max-change-rate="0.01" \
  --min-self-delegation="1000000" \
  --gas="auto" \
  --gas-prices="10000000000000mpx" \
  --gas-adjustment=1.5 \
  --from=my_validator
```
4. Check out your validator in https://xfiscan.com/