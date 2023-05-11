# Kintsugi CLI Application

This CLI application is designed to support smaller Vault Operators (VOs) participating in the Kintsugi ecosystem. Its purpose is to help manage exposures to multiple crypto assets, automate self-issuing, harvesting rewards, and farming BTC. By providing these capabilities, the application aims to make running small VOs more attractive, thereby increasing network issuance while maintaining decentralization.

## Features

- **Decentralized Wrapped BTC**: The application aims to create the most decentralized wrapped BTC token insured by collateral.
- **Encouraging Decentralization**: The network intends to attract high quantities of smaller VOs instead of a few whale accounts to promote decentralization.
- **Automated Management**: The CLI application automates various processes, including self-issuing, reward harvesting, and BTC farming.
- **Collateral Ratio Management**: The application helps VOs manage the collateral ratio, ensuring it stays within the desired range by monitoring the markets and reacting to price fluctuations of both KBTC and collateral assets such as KSM.
- **Increase Network Issuance**: By providing support to smaller VOs, the application aims to increase network issuance while maintaining a decentralized environment.

## Prerequisites

Before using the application, make sure you have the following prerequisites:

1. Node version 18 and later
2. Kintsugi vault fully set up
3. Sufficient KINT balance in your vault
4. Seed phrase of your vault
5. (for some scripts) Free KAR balance on Karura chain

## Installation

Follow these steps to install and set up the application:

1. Create a local seed phrase file somewhere on your filesystem, e.g., `mkdir ~/.private && touch ~/.private/seed.txt && vim ~/.private/seed.txt`
2. Change permissions to make the file readable only by the owner, e.g., `chmod 600 ~/.private/seed.txt`
3. Change the file owner to root, e.g., `sudo chown root seed.txt`
4. In the repository directory, create a local environment file: `cp .env.example .env`
5. Replace the seed path in the `.env` file with the absolute path to the seed phrase file created in step 1
6. Install the required libraries by running `yarn`

## Usage

## Demo
https://youtu.be/7yhKwmyIb3E

> :warning: Use this application at your own risk. We take no responsibility for any loss of funds.

> :warning: Poor performance may occur if the WSS RPC endpoints are busy or slow. Consider changing the `.env` RPC configuration if you experience performance issues.

To start the application, run the following command:
yarn start


## Scripts

The following scripts are available in the application:

- **Self Issuance Workflow**: Supports self-mint issue requests.
- **Harvest & Compound Workflow**: Enables the harvesting of rewards and compounding.
- **Rebalancing Vault with LP**: Facilitates vault rebalancing using LP.

Please exercise caution and conduct proper research before using any of these scripts.

## Example Output

Here's an example output from the application:

### Example Output
```
=============================
⚡️ Connected to: kintsugi-parachain v15
🔑 Signer address: a3aPvmjypKaDtjRgjjwppKKK082kseYR3SLwvPevL6j7wF67aFtV4
ℹ️  Current status: CLOSED 🔒
❓ Permission: OPEN ✅
🐤 Collateral: 114.98 KSM
🕰  Outstanding issue requests: 0.018862 kBTC
💰 Issued: 0.08938 kBTC
🤌  Collateral Ratio: 305.93%
🌱 Mint Capacity Remaining: 0.01470 kBTC
💸 KINT Balance Free: 1.39 KINT
=============================
Would you like to proceed with submitting a self-mint issue request? (yes/no) yes
What collateral ratio would you like to issue upto? (min/default: 261) 303
Txns built. Waiting...
Txns in unfinalized block: 0xbac3ec02c3f6407a12672922d8a5062426f6fc574ac0c9fb421e73f068e22c1 waiting...
Batched TXNs in finalized block: 0xbac3ec02c3f6407a1244db268d7267393f6fc574ac0c9fb421e73f068e22c1
Events posted in transaction:
        {"applyExtrinsic":2}: utility.ItemCompleted::[]
        {"applyExtrinsic":2}: tokens.Reserved::[{"token":"KINT"},"a3aPvmjypKaDtjHHABKeYR3SLw28282L6j7wF67aFtV4",61818848]
        {"applyExtrinsic":2}: vaultRegistry.IncreaseToBeIssuedTokens::[{"accountId":"a3aPvm89278283632CCkseYR3SLwvPevL6j7wF67aFtV4","currencies":{"collateral":{"token":"KSM"},"wrapped":{"token":"KBTC"}}},27000]
        {"applyExtrinsic":2}: vaultRegistry.RegisterAddress::[{"accountId":"a3aPvmjypKaDtjRgYbDL2CCkseYR3SLwvPevL6j7wF67aFtV4","currencies":{"collateral":{"token":"KSM"},"wrapped":{"token":"KBTC"}}},{"p2wpkHv0":"0xccfa75cf68b729278358273673b03f9c8d61bf1a"}]
        {"applyExtrinsic":2}: issue.RequestIssue::["0x3885ee30a254076f846c85ae2b2fea1707bbe7c3658283eacb200dd5640c974ad","a3aPvmjypKaDtjRgYbDL2CCkseYR3SLwvPevL6j7wF67aFtV4",26959,41,61818848,{"accountId":"a3aPvmjypKaDtjRgYbDL2CCkseYR3SLwvPevL6j7wF67aFtV4","currencies":{"collateral":{"token":"KSM"},"wrapped":{"token":"KBTC"}}},{"p2wpkHv0":"0xccfa75cf68283737515f7f188b03f9c8d61bf1a"},"0x02aca66424646b34d160257929382951b4cfcaed45fe19549c11256a15fa58839b"]
        {"applyExtrinsic":2}: utility.ItemCompleted::[]
        {"applyExtrinsic":2}: utility.ItemCompleted::[]
        {"applyExtrinsic":2}: utility.BatchCompleted::[]
        {"applyExtrinsic":2}: system.ExtrinsicSuccess::[{"weight":1625865000,"class":"Normal","paysFee":"Yes"}]
=============================
🔏 Issue Request submitted to vault a3aPvmjypKaDtjRgjjwppKKK082kseYR3SLwvPevL6j7wF67aFtV4
🔏 Destination vault address: bc1qena8tnmgkc72829lcc3vplnjxkr0c6jm3rwy
💳 Amount to send: 0.00026959 kBTC
✨  Done in 48.14s.
```

## Frequently Asked Questions

**Q: Is this application going to steal my funds?**

A: The application utilizes the official Parity `@polkadot/api` library to generate a signer key using your seed phrase. You can review the code and see how the seed phrase is used securely. The relevant code can be found in `utils/helpers.ts


