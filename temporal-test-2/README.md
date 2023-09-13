# Note: Testnet was succesfully launched on the morning of 8/31 and no more spots are available. 

# Temporal Public Testnet

## Generate a gentx on a server that has never run a Temporal node before:

Clone and install the node:

```
git clone https://github.com/temporal-zone/temporal.git
cd temporal
git checkout v0.4.0
make install
```

Restore your keys:

```
temporald keys add NAME_OF_KEY
temporald keys list
```

Copy your new temporal address

Init the node, add a genesis account and generate the gentx:

```
temporald init NODE_NAME --chain-id temporal-test-2 --default-denom utprl
temporald add-genesis-account TEMPORAL_ADDRESS 1100000000000utprl
```

Note: if you get an error that it `failed to to get address from Keybase`, try adding `--keyring-backend os`, unless when you restored your keys you explicitly specificed a different `keyring-backend`, then use that one.

```
temporald gentx NAME_OF_KEY 1000000000000utprl \
--chain-id temporal-test-2 \
--moniker="YOUR_VALIDATOR_NAME" \
--commission-rate 0.05 \
--commission-max-rate 0.10 \
--commission-max-change-rate 0.05 \
--details="XXXXXXXX" \
--identity YOUR_KEYBASE_ID \
--security-contact="XXXXXXXX" \
--website="XXXXXXXX"
```

Please then submit the gentx-VALIDATOR-NAME.json file to the gentx folder in this repo.

## Generate a gentx on a server that has run a Temporal node before:

Update the node to the newest version and install the new binary:

```
cd temporal
git fetch && git pull
git checkout v0.4.0
make install
```

Copy your temporal address:

```
temporald keys list
```

Init the node, add a genesis account and generate the gentx:

```
temporald init NODE_NAME --chain-id temporal-test-2 --default-denom utprl --overwrite
temporald add-genesis-account TEMPORAL_ADDRESS 1100000000000utprl
```

Note: if you get an error that it `failed to to get address from Keybase`, try adding `--keyring-backend os`, unless when you restored your keys you explicitly specificed a different `keyring-backend`, then use that one.

```
temporald gentx NAME_OF_KEY 1000000000000utprl \
--chain-id temporal-test-2 \
--moniker="YOUR_VALIDATOR_NAME" \
--commission-rate 0.05 \
--commission-max-rate 0.10 \
--commission-max-change-rate 0.05 \
--details="XXXXXXXX" \
--identity YOUR_KEYBASE_ID \
--security-contact="XXXXXXXX" \
--website="XXXXXXXX"
```

Please then submit the gentx-VALIDATOR-NAME.json file to the gentx folder in this repo.
