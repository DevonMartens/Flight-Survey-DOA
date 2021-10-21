# FlightSurety

FlightSurety is a sample application project for Udacity's Blockchain course.

## Install

This repository contains Smart Contract code in Solidity (using Truffle), tests (also using Truffle), dApp scaffolding (using HTML, CSS and JS) and server app scaffolding.

To install, download or clone the repo, then:

`npm install`
`truffle compile`


## Contract addresses
1. 0x354316B4dA82529fB2682Bd436f1226c95a0bc2b
[1 on Etherscan](https://rinkeby.etherscan.io/address/0x354316b4da82529fb2682bd436f1226c95a0bc2b)

2. 0xE832F9f4683EdffeB5900D2c1073E9C249277E03 
[2 on Etherscan](https://rinkeby.etherscan.io/address/0xe832f9f4683edffeb5900d2c1073e9c249277e03)

3. 0x600Bc9610657b998e6b15232E74DDB3B54237AE7
[3 on Etherscan](https://rinkeby.etherscan.io/address/0x600bc9610657b998e6b15232e74ddb3b54237ae7)

4. [4 on Etherscan](0x67a60770b6d7a212fA6926AA8c19b9369C21b2A7)

## Develop Client

To run truffle tests:

`truffle test ./test/flightSurety.js`
`truffle test ./test/oracles.js`

To use the dapp:

`truffle migrate`
`npm run dapp`

To view dapp:

`http://localhost:8000`

## Develop Server

`npm run server`
`truffle test ./test/oracles.js`

## Deploy

To build dapp for prod:
`npm run dapp:prod`

Deploy the contents of the ./dapp folder


## Resources

* [How does Ethereum work anyway?](https://medium.com/@preethikasireddy/how-does-ethereum-work-anyway-22d1df506369)
* [BIP39 Mnemonic Generator](https://iancoleman.io/bip39/)
* [Truffle Framework](http://truffleframework.com/)
* [Ganache Local Blockchain](http://truffleframework.com/ganache/)
* [Remix Solidity IDE](https://remix.ethereum.org/)
* [Solidity Language Reference](http://solidity.readthedocs.io/en/v0.4.24/)
* [Ethereum Blockchain Explorer](https://etherscan.io/)
* [Web3Js Reference](https://github.com/ethereum/wiki/wiki/JavaScript-API)