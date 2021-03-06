# ethereum-geth
Creating ethereum network using Geth with different machine

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
To avoid mining process add empty data blocks to the chain, use preload json file when running console command

### Interconnect Node
1. Create another nodes on the different machine
2. Open console node1, check enode info as the representation of node address
    ```
    admin.nodeInfo.enode
    ```
3. Add peer of node 1 on node 2 console using this command
    ```
    admin.addPeer(<enodeID>)
    ```
   change IP in enode ID using your IP machine on node 1
4. Check peer using this command
    ```
    admin.peers
    ```
5. To remove peer use this command
    ```
    admin.removePeer(<enodeID>)
    ```

### Sending Transactions
- To send transaction between two different machine use this command 
    ```
    > eth.sendTransaction({ from: eth.accounts[0], to: <public address of second EOA> , value: web3.toWei(5,"ether"), gas:0xEEE00 , data: "0x00"})
    ```
- Check transaction details using this command
    ```
    eth.getTransaction(<hash transaction>)
    ```
