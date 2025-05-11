# Bitcoin CPU Bruteforce

This is a simple Node.js tool for CPU-based bruteforce search of Bitcoin and Ethereum addresses.

## Structure

bitcoin-cpu-bruteforce/\
├── main/\
│ ├── index.js # main bruteforce script\
│ ├── target.txt # target addresses (Bitcoin or Ethereum)\
├── test-run/\
│ ├── test_run.js # simplified version for testing\
│ ├── test_target.txt # test target addresses\
├── output.txt # automatically generated results\

## How it works

This script performs a **partial key brute-force attack**, a common tactic used in Bitcoin puzzle challenges.

It works by:
- Randomly generating a **120-bit prefix** (30 bytes),
- Then **exhaustively iterating** over all possible **16-bit suffixes** (`0000` to `ffff`),
- Combining them to form a full **256-bit private key**.

For each generated key, it derives:
- Bitcoin addresses: P2PKH, P2SH, Bech32 (P2WPKH, nested), Taproot
- Ethereum addresses (from both compressed and uncompressed public keys)

Each address is then compared against the entries in `target.txt` or `test_target.txt`.

If a match is found, the private key and address are saved to `output.txt`.

This partial-key strategy drastically reduces the brute-force search space from `2^256` to `2^16` per random prefix, making it feasible to test billions of keys efficiently.

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
