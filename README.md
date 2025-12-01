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

## Merge Holdings

```bash
daml script --dar .daml/dist/lunares-1.0.0.dar \
  --script-name Scripts.Merge:merge \
  --input-file /dev/stdin \
  --ledger-host localhost --ledger-port 6865 \
  <<< '{"party": "Alice"}'
```

## Create Transfer Request

```bash
daml script --dar .daml/dist/lunares-1.0.0.dar \
  --script-name Scripts.Transfer:createTransferRequest \
  --input-file /dev/stdin \
  --ledger-host localhost --ledger-port 6865 \
  <<< '{"sender": "Alice", "receiver": "Bob", "amount": "100.0"}'
```

## Accept Transfer Request

```bash
daml script --dar .daml/dist/lunares-1.0.0.dar \
  --script-name Scripts.Transfer:acceptTransferRequest \
  --input-file /dev/stdin \
  --ledger-host localhost --ledger-port 6865 \
  <<< '{"sender": "Alice", "receiver": "Bob", "requestCid": "<REQUEST_CID>", "holdingCid": "<HOLDING_CID>"}'
```

## Test Transfer Flow

```bash
daml script --dar .daml/dist/lunares-1.0.0.dar \
  --script-name Tests.Tests:testTransferFlow \
  --ledger-host localhost --ledger-port 6865
```

