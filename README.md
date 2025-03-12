## Foundry

**Foundry is a blazing fast, portable, and modular toolkit for Ethereum application development written in Rust.**

Foundry consists of:

-   **Forge**: Ethereum testing framework (like Truffle, Hardhat, and DappTools).
-   **Cast**: Swiss army knife for interacting with EVM smart contracts, sending transactions, and getting chain data.
-   **Anvil**: Local Ethereum node, akin to Ganache, Hardhat Network.
-   **Chisel**: Fast, utilitarian, and verbose Solidity REPL.

## Documentation

For more detailed information, visit the [Foundry Book](https://book.getfoundry.sh/).

## Usage

### Build

```shell
forge build
```

### Test

```shell
forge test
```

### Format

```shell
forge fmt
```

### Gas Snapshots

```shell
forge snapshot
```

### Anvil

```shell
anvil
```

### Deploy

```shell
forge script script/Counter.s.sol:CounterScript --rpc-url <your_rpc_url> --private-key <your_private_key>
```

### Cast

```shell
cast <subcommand>
```

### Help

```shell
forge --help
anvil --help
cast --help
```

# Foundry Simple Storage

This project demonstrates deploying a simple storage contract using Foundry. Below are the steps and commands used to run the script, handle errors, and encrypt the private key.

## Prerequisites

- Ensure you have Foundry installed.
- Make sure your Ethereum node is running and accessible at the specified RPC URL.

## Environment Setup

Create a `.env` file with the following content:

```
PRIVATE_KEY=your_private_key_here
RPC_URL=http://127.0.0.1:8545
```

Replace `your_private_key_here` with your actual private key.

## Environment Variables and Commands

### Using .env File

The `.env` file is used to store environment variables such as the private key and RPC URL. Here is an example of how it is set up:

```
PRIVATE_KEY=your_private_key_here
RPC_URL=http://127.0.0.1:8545
```

To load these variables into your shell session, use the following command:

```bash
source .env
```

### Commands Used

Here are some of the commands that were used during the process:

- **Running the Script with Environment Variables**:
  ```bash
  forge script script/DeploySimpleStorage.s.sol --rpc-url $RPC_URL --broadcast --private-key $PRIVATE_KEY
  ```
  This command uses the environment variables set in the `.env` file to deploy the contract.

- **Checking Environment Variables**:
  ```bash
  echo $RPC_URL
  echo $PRIVATE_KEY
  ```
  These commands are used to verify that the environment variables are correctly set.

- **Encrypting the Private Key**:
  ```bash
  cast wallet import defaultkey --interactive
  ```
  This command encrypts the private key and saves it securely.

### Common Issues

- **Incorrect Environment Variable Values**: Ensure that the values in the `.env` file are correct and that the file is sourced properly.
- **Connection Errors**: Verify that the Ethereum node is running and accessible at the specified RPC URL.

This section provides a summary of the different methods and commands used to manage environment variables and deploy contracts using Foundry.

## Running the Script

To deploy the `SimpleStorage` contract, use the following command:

```bash
forge script script/DeploySimpleStorage.s.sol --rpc-url $RPC_URL --broadcast --private-key $PRIVATE_KEY
```

### Common Errors

- **No such file or directory (os error 2):** Ensure the script file exists in the specified path.
- **Error sending request for URL:** Check if your Ethereum node is running and the RPC URL is correct.
- **Unexpected argument '-r':** Ensure the command syntax is correct.

## Encrypting the Private Key

To encrypt your private key, use the following command:

```bash
cast wallet import defaultkey --interactive
```

You will be prompted to enter your private key and a password. The keystore will be saved successfully with the address.

## Additional Information

- Transactions and sensitive values are saved in the `broadcast` and `cache` directories respectively.
- For more detailed command usage, refer to the Foundry documentation or use `forge script --help`. 

This README provides a simple guide to help you understand and manage the deployment process using Foundry. If you encounter any issues, ensure all paths and environment variables are correctly set and that your Ethereum node is operational.

## Using the Private Key with Forge Script

To deploy a contract using a private key stored in a keystore, you can use the following command:

```bash
forge script script/DeploySimpleStorage.s.sol --rpc-url $RPC_URL --account defaultkey --sender 0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266 --broadcast -vvvv
```

### Explanation:
- **--rpc-url $RPC_URL**: Specifies the RPC URL of the Ethereum node.
- **--account defaultkey**: Uses the account stored under the name `defaultkey` in the keystore.
- **--sender 0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266**: Specifies the sender's address.
- **--broadcast**: Broadcasts the transaction to the network.
- **-vvvv**: Sets the verbosity level to maximum for detailed output.

This command allows you to deploy contracts using a private key securely stored in a keystore, ensuring that sensitive information is not exposed directly in the command line.

## Interacting with Contracts Using Cast

To interact with a deployed contract from the terminal, you can use the `cast send` command. Here is an example:

```bash
cast send 0xCf7Ed3AccA5a467e9e704C703E8D87F634fB0Fc9 "store(uint256)" 123 --rpc-url $RPC_URL --account defaultkey
```

### Explanation:
- **0xCf7Ed3AccA5a467e9e704C703E8D87F634fB0Fc9**: The address of the deployed contract.
- **"store(uint256)"**: The function signature you want to call on the contract, in this case, a function named `store` that takes a `uint256` as an argument.
- **123**: The argument to pass to the function, in this case, the number `123`.
- **--rpc-url $RPC_URL**: Specifies the RPC URL of the Ethereum node.
- **--account defaultkey**: Uses the account stored under the name `defaultkey` in the keystore.

This command allows you to interact with smart contracts directly from the terminal, providing a convenient way to test and manage contract functions.
