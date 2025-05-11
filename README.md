# Bitcoin CPU Bruteforce

This is a simple Node.js tool for CPU-based bruteforce search of Bitcoin and Ethereum addresses.

## Structure

bitcoin cpu bruteforce/
├── main/
│ ├── index.js # main bruteforce script
│ ├── target.txt # target addresses (Bitcoin or Ethereum)
├── test-run/
│ ├── test_run.js # simplified version for testing
│ ├── test_target.txt # test target addresses
├── output.txt # automatically generated results

## How it works

The script generates random private keys, derives their public addresses, and checks if they match any in the `target.txt` or `test_target.txt` files.

If a match is found, the private key and address are saved to `output.txt`.

## Usage

Navigate to the directory and run:

node main/index.js


For testing with a smaller set:

node test-run/test_run.js


## Requirements

- Node.js v22
- Dependencies: install via npm
```bash
npm install bitcoinjs-lib tiny-secp256k1 secp256k1 bech32 bs58check ethereum-cryptography
```

## Notes

- All results are saved in `output.txt` (in the root folder).
- Ensure that `target.txt` or `test_target.txt` contain addresses, one per line.

---

This project is for educational and research purposes only.
The author does not condone any illegal use, including unauthorized access to third-party wallets.