# AI-Generated NFTs on Stacks

## Overview

This Clarity smart contract implements a unique Non-Fungible Token (NFT) system for AI-generated tokens on the Stacks blockchain. The contract allows for the creation, evolution, and transfer of AI-generated NFTs with dynamic metadata stored on IPFS.

## Features

- AI-Generated NFT Minting
- Dynamic NFT Evolution
- Metadata Tracking
- Evolution History Preservation
- Ownership Management

## Contract Functions

### Minting
- `mint(token-id, metadata-uri)`: Create a new AI-generated NFT
  - Only callable by contract owner
  - Validates token ID and URI
  - Stores initial metadata and evolution stage

### Evolution
- `evolve-nft(token-id, new-metadata-uri)`: Evolve an existing NFT
  - Only callable by contract owner
  - Increases evolution stage
  - Updates metadata and tracks evolution history

### Transfer
- `transfer(token-id, recipient)`: Transfer NFT to a new owner
  - Only callable by current token owner

## Read-Only Functions

- `get-token-metadata(token-id)`: Retrieve NFT metadata
- `get-evolution-stage(token-id, stage)`: Get metadata for a specific evolution stage
- `get-evolution-history(token-id)`: Retrieve initial evolution data
- `get-token-owner(token-id)`: Find the current owner of a token

## Key Constraints

- Maximum of 1,000,000 tokens
- Metadata stored as UTF-8 string (max 256 characters)
- Evolution stages tracked with block height
- Basic URI validation

## Error Handling

The contract includes several error codes for different scenarios:
- `err-owner-only`: Unauthorized access
- `err-not-token-owner`: Transfer by non-owner
- `err-token-exists`: Preventing duplicate minting
- `err-token-not-found`: Invalid token lookup
- `err-invalid-token-id`: Token ID out of bounds
- `err-invalid-uri`: Malformed metadata URI

## Deployment Considerations

- Ensure IPFS/Arweave URIs are reliable
- Contract owner manages minting and evolution
- Implement additional access controls as needed

## Example Workflow

1. Mint an initial AI-generated NFT
2. Evolve the NFT through multiple stages
3. Transfer ownership to another principal
4. Retrieve metadata and evolution history

## Security Notes

- Only contract owner can mint and evolve tokens
- Basic input validation implemented
- Recommend additional security audits

## Technical Requirements

- Stacks Blockchain
- Clarity Smart Contract Language
- IPFS/Arweave for metadata storage
