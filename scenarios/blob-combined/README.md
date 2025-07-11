# Combined Blob Testing

A randomized combination of all blob scenarios for comprehensive testing.

## Usage

```bash
spamoor blob-combined [flags]
```

## Configuration

### Base Settings (required)
- `--privkey` - Private key of the sending wallet
- `--rpchost` - RPC endpoint(s) to send transactions to

### Volume Control (either -c or -t required)
- `-c, --count` - Total number of transactions to send
- `-t, --throughput` - Transactions to send per slot
- `--max-pending` - Maximum number of pending transactions
- `--throughput-increment-interval` - Increment the throughput and pending limit every interval (in seconds). Useful for gradually increasing load over time.

### Transaction Settings
- `--basefee` - Max fee per gas in gwei (default: 20)
- `--tipfee` - Max tip per gas in gwei (default: 2)
- `--blobfee` - Max blob fee in gwei (default: 20)
- `--max-replace` - Maximum number of replacement transactions (default: 4)
- `--replace` - Seconds to wait before replacing a transaction (default: 30)
- `--rebroadcast` - Seconds to wait before rebroadcasting (default: 30)

### Blob Configuration
- `-b, --sidecars` - Maximum number of blob sidecars per transaction (default: 3)
- `--conflict-delay` - Milliseconds to wait before sending conflicting type-2 transaction (default: 0)

### Wallet Management
- `--max-wallets` - Maximum number of child wallets to use
- `--refill-amount` - ETH amount to fund each child wallet (default: 5)
- `--refill-balance` - Minimum ETH balance before refilling (default: 2)
- `--refill-interval` - Seconds between balance checks (default: 300)

### Client Settings
- `--client-group` - Client group to use for sending transactions

### Debug Options
- `-v, --verbose` - Enable verbose output
- `--log-txs` - Log all submitted transactions
- `--trace` - Enable tracing output

## Example

Send 1000 blob transactions with randomized behavior:
```bash
spamoor blob-combined -p "<PRIVKEY>" -h http://rpc-host:8545 -c 1000
```

Send 3 blob transactions per slot with 2-4 sidecars each:
```bash
spamoor blob-combined -p "<PRIVKEY>" -h http://rpc-host:8545 -t 3 -b 2 --max-pending 3
``` 