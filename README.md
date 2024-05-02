# Solana Lamport and SPL Token Transfer Program

This Solana program facilitates the transfer of SOL (native currency, measured in lamports) and SPL (Solana Program Library) tokens. It provides two separate methods: one for transferring SOL (lamports) and another for SPL tokens.

## Features

- **Lamport Transfer**: Send SOL from one account to another.
- **SPL Token Transfer**: Move SPL tokens between associated token accounts.

## Methods

### `transfer_lamports`
Transfers SOL from a signer's account to a recipient's account.

#### Arguments:
- `ctx: Context<TransferLamports>`: A context that includes the signing accounts necessary for the lamport transfer.
- `amount: u64`: The number of lamports to be transferred.

### `transfer_spl_tokens`
Handles the transfer of SPL tokens from one account to another.

#### Arguments:
- `ctx: Context<TransferSpl>`: The context that holds the required accounts for the SPL token transfer.
- `amount: u64`: The quantity of tokens to transfer.

## Accounts

### For `transfer_lamports`
- `from`: The sender's account, which must be a signer.
- `to`: The recipient's account where lamports will be deposited.
- `system_program`: Reference to the System Program.

### For `transfer_spl_tokens`
- `from`: The authority account initiating the transfer, must sign the transaction.
- `from_ata`: The sender's SPL token account.
- `to_ata`: The receiver's SPL token account.
- `token_program`: Reference to the Token Program.

## Usage Instructions

1. Install the required tools, including the Anchor CLI and Solana CLI.
2. Clone this repository and navigate to its root directory.
3. Deploy the smart contract to the Solana blockchain:

```bash
anchor build
anchor deploy