# Lunares

Creates a Bank and two parties (Alice and Bob). Creates LNRD token and provides scripts to mint and view balances.

## Run

```bash
daml start
```

## Mint LNRD

```bash
daml script --dar .daml/dist/lunares-1.0.0.dar \
  --script-name Scripts.Mint:mint \
  --input-file /dev/stdin \
  --ledger-host localhost --ledger-port 6865 \
  <<< '{"recipient": "Alice", "amount": "1000.0"}'
```

## View Balance

```bash
daml script --dar .daml/dist/lunares-1.0.0.dar \
  --script-name Scripts.Balance:balance \
  --input-file /dev/stdin \
  --ledger-host localhost --ledger-port 6865 \
  <<< '{"party": "Alice"}'
```

