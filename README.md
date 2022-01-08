# Defa Periphery

The Defa periphery contracts, commonly known as the "Router", handles important checks regarding interacting with the [core DEX contracts](https://github.com/defaswap/defa-swap-core). This is related to the main functionality of the DEX which includes adding/removing liquidity and swapping tokens.

The periphery contracts are unique in that they don't hold any value, it just manages transferring the proper amount of tokens to the proper contracts for the core DEX contracts to properly do their work.

Because the periphery contracts hold no value, they can be easily upgraded and improved without requiring a DEX migration.

### Setting up a new DEX

Deploying a periphery contract to work with a new set of DEX core contracts requires an update to the contract code for [DeFaLibrary.sol](./contracts/libraries/DeFaLibrary.sol) in the `pairFor` function.

This function pre-computes a pair address before creation and requires that the `hex` value match the `INIT_CODE_PAIR_HASH` of the core pair contract. On the deployed factory that the periphery contract is intended to be linked to, there is a public variable `INIT_CODE_PAIR_HASH` that should be used to replace the `hex` value in `DefaLibrary.sol`. (Remember to remove the `0x` before the hash)

## Commands

The following assumes the use of `node@>=12`.

## Install Dependencies

`yarn`

## Compile Contracts

`yarn compile`

## Run Tests

`yarn test`
