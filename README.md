# FlightSurety

FlightSurety is a sample application project for Udacity's Blockchain course.

## Install

This repository contains Smart Contract code in Solidity (using Truffle), tests (also using Truffle), dApp scaffolding (using HTML, CSS and JS) and server app scaffolding.

To install, download or clone the repo, then:

`npm install`
`truffle compile`

## Solidity Verison 0.8.0

## Contract addresses
1. Address: `0x354316B4dA82529fB2682Bd436f1226c95a0bc2b`
[1 on Etherscan](https://rinkeby.etherscan.io/address/0x354316b4da82529fb2682bd436f1226c95a0bc2b)

2. Address: `0xE832F9f4683EdffeB5900D2c1073E9C249277E03` 
[2 on Etherscan](https://rinkeby.etherscan.io/address/0xe832f9f4683edffeb5900d2c1073e9c249277e03)

3. Address: `0x600Bc9610657b998e6b15232E74DDB3B54237AE7`
[3 on Etherscan](https://rinkeby.etherscan.io/address/0x600bc9610657b998e6b15232e74ddb3b54237ae7)

4. Address: `0x67a60770b6d7a212fA6926AA8c19b9369C21b2A7`
[4 on Etherscan](https://rinkeby.etherscan.io/address/0x67a60770b6d7a212fa6926aa8c19b9369c21b2a7)

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

# Configurations

Multiple internal settings have been set in the project and need to be adjusted :

- _tokenHolderMinBlockRequirement: default number of block before giving the ability to a token holder to participate in the community decision (default to 2 for testing purposes but should be a month equivalent in block number ) (plays a role to mitigate the risk of an EOA transfering his holding to gain more vote power )
- _proposalValidBlockNum: default number of block a setting amendment porposal (membership fee or insurance coverage ratio) is valid
- _defaultBlockNumBeforeRedeem: default number of block before giving the ability to a token holder to redeem it's holding for a cut of the funds profits
- _currentInsuranceCoverage : current insurance coverage ratio (default to 150 set in InsuranceCoverageAmenedmentProposal contract constructor)
- operationnal : operationnal state of the contracts (default to true)
- _authorizedFlightDelay : default number of time in seconds a flight can be late.

## Contract deployement workflow

1. deploy FlightSuretyApp
   - uint256 _tokenHolderMinBlockRequirement
   - uint256 _proposalValidBlockNum
2. deploy FlightSuretyOracle
   - uint64 _authorizedFlightDelay
3. deploy FlightSuretyData authorizing callers :
   - address _appContractAddress
   - address _oracleContractAddress
4. deploy OracleProviderRole authorizing callers :
   - address _appContractAddress
   - address _oracleContractAddress
5. deploy InsuranceProviderRole authorizing callers :
   - address _appContractAddress
6. deploy FlightSuretyShares authorizing callers :
   - address _appContractAddress
7. deploy InsuranceCoverageAmendmentProposal authroizing caller :
   - address _appContractAddress
   - uint256 _currentInsuranceCoverage
8. deploy MembershipFeeAmendmentProposal authorizing caller :
   - address _appContractAddress
   - uint256 _currentMembershipfee
9. initialize FlightSuretyApp referencing external contracts addresses :
   - address _flightSuretyData
   - address _insuranceCoverageAmendmentProposal
   - address _membershipFeeAmendmentProposal
   - address _insuranceProviderRole
   - address _oracleProviderRole
   - address _flighSuretyShares
10. initialize FlightSuretyOracle referencing external contracts addresses :
    - address _flightSuretyData
    - address _oracleProviderRole

## Config the app

In order to run the application you will need to create environnement files to refrences environnement variables and add the already deployed contract address to the supplychain contract abi.

```bash
# creating general environement file
echo -e "MNEMONIC=<YOUR MNEMONIC> PROVIDER_URL=<YOUR PROVIDER URL> SERVER_PORT=<SERVER PORT>" >> .env
```

## Quickstart (DEV ENVIRONNEMENT)

### Install dependencies

```bash
# install general dependencies
npm i
```

```bash
# install client dependencies
cd ./client/
npm i
```

```bash
# install server dependencies
cd ./server/
npm i
```

### Lauch the smart contract test

```bash
# lauch ganache-cli
ganache-cli
# install client packages
npm run test
```

### Deploy the smart contracts

```bash
# deploy the contracts to localhost network, exports the contracts abi to the client directory and seed the contract with n oracle providers accounts
npm run migrate-dev
```

### Lauch Ganache client

```bash
# lauch Ganache client with the specified amount of accounts
ganache-cli --accounts=20
```

### Running the app (development)

```bash
# running the client app in dev environement (hot reloading enabled)
cd ./client
npm run dapp
```

```bash
# running the server app in dev environement (hot reloading enabled)
cd ./server
npm run server
```

## Deployment (PROD ENVIRONNEMENT)

### Deploy the contract to ethereum rinkeby network

```bash
# deploy the contracts to rinkeby network
npm run migrate
```

### Build the app

```bash
# build the app
cd ./client
npm run build
```
