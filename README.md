# ethereum-geth
Creating ethereum network using Geth

Ethereum node needs Client CLI to connect to the ethereum network. In this repo, Client CLI that will be used is Geth (Go Ethereum), a Go based software that will run node on the Ethereum network.

## Getting Started
These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Install Geth
To install geth, use this command
  ```
  sudo add-apt-repository -y ppa:ethereum/ethereum
  sudo apt-get update
  sudo apt-get install -y ethereum
  ```
Check version of geth
  ```
  geth version
  ```
## Deployment
### Node Creation
1. Create genesis.json file
2. Create chain using this command
    ```
    geth –nousb --datadir node2 init genesis.json
    ```
3. Get to the console node using this command
    ```
    geth –nousb --datadir node2 --networkid 42 console
    ```

### External Owned Account Creation
EOA can be created outside or inside console node.
- To create account inside console node, use this command
  ```
  personal.newAccount()
  ```
Geth software will ask for a paraphrase that will be use to encrypt/decrypt private key.

- To use the account for transactions, you will need to unlock your account using this command
  ```
  personal.unlockAccount(eth.accounts[0],<password>,15000)
  ```
Above command will make your account stay unlock for about 15 minutes

- To check balance of your account use this
  ```
  eth.getBalance(eth.accounts[0])
  ```

### Mining
- Start mining process
  ```
  miner.start()
  ```
- Stop mining process
  ```
  miner.stop()
  ```
- Check mining status
  ```
  eth.mining()
  ```
