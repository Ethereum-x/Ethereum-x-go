`` `
ETX full node machine configuration:
    Minimum configuration:
        CPU: 4 core
        Memory: 8G
        Hard disk: 100G high-speed hard disk
        Network: 2M
    
    Recommended configuration:
        CPU: 8 core
        Memory: 16G
        Hard Drive: 200G SSD (Solid State Drive)
        Network: 5M +

        
1. Node file download
    etx download address: wget https://github.com/Ethereum-x/Ethereum-x-go/releases/download/etx-v1.0/etx-v1.0-stable-linux.zip
    
2. Genesis file download:
    wget https://github.com/Ethereum-x/Ethereum-x-go/blob/master/docs/etx-genesis.json
    
    Keep etx and etx-genesis.json in the same directory
    
3. Unzip
    unzip etx-v1.0-stable-linux.zip

4. Give getx executable permissions:
    sudo chmod 777 getx

5. Enter the decompression directory and start (command explanation, please refer to Appendix 1 for details)
    The first time you run getx, you need to use the genesis file: etx-genesis.json
    Execute on the command line: ./getx --datadir ~ / etx / data init ./etx-genesis.json

6. Start the node and enter the console mode:
    ./getx --rpc --datadir ~ / etx / data --rpcport 8888 --networkid 66666 --port 61918 --rpcapi "personal, eth, net, web3" --rpccorsdomain "*" --wsport 8588- wsapi "personal, eth, net, web3" --wsorigins "*" console
    
    At this step, do not add --mine instruction, there is no mining account, otherwise it will report an error.
    
7. Generate mining address, password "12345", can be modified to set by yourself
    Enter the command in the console: personal.newAccount ("12345")

8. Normally execute the node startup program, if it is running in the background, please use the suspend operation
    If you want to mine, please add --mine command.
    The console runs:
    ./getx --rpc --datadir ~ / etx / data --rpcport 8888 --networkid 66666 --port 61918 --rpcapi "personal, eth, net, web3" --rpccorsdomain "*" --wsport 8588- wsapi "personal, eth, net, web3" --wsorigins "*" --mine

    Suspend running in the background:
    nohup ./getx --rpc --datadir ~ / etx / data --rpcport 8888 --networkid 66666 --port 61918 --rpcapi "personal, eth, net, web3" --rpccorsdomain "*" --wsport 8588- -wsapi "personal, eth, net, web3" --wsorigins "*" --mine >> getx.log &

ETX related operation commands:
eth: contains some methods related to the operation of the blockchain
net: contains the following methods to view the p2p network status
admin: contains some methods related to managing nodes
miner: contains some methods for starting & stopping mining
personal: mainly contains some methods for managing accounts
txpool: contains some methods to view the transaction memory pool
web3: contains the above objects, and also contains some unit conversion methods

Appendix I
command
   account Manage account
   attach starts an interactive JavaScript environment (by connecting to a remote node)
   bug Open a window to report bugs
   console starts an interactive JavaScript environment
   copydb copy a datadir, you need to specify the path of another datadir
   dump dumps the specified block from the blockchain
   dumpconfig display configuration information
   export Export block information to a file
   import Import block information from a file
   init initializes a new genesis block
   js execute the specified js file
   license display license information
   makecache generate ethash verification information cache? (used for testing)
   makedag generates ethash mining DAG (for testing)
   monitor monitor, display node indicators
   removedb Remove blockchain and state database
   version Print the version number
   wallet manage Ethereum wallet
   help, h displays all commands and help information

Ethereum options
ETHEREUM OPTIONS:
  --config value TOML configuration file
  --datadir "/home/karalabe/.ethereum" specify the datadir location
  --keystore Specify keystore location (default in datadir)
  --nousb close monitoring usb wallet
  --networkid value network identifier (number, 1 = Frontier, 2 = Morden (not used), 3 = Ropsten, 4 = Rinkeby) (default: 1)
  --testnet test network: the test network preset to the proof-of-work mode
  --rinkeby test network: the test network preset to the proof-of-stake model
  --syncmode "fast" block synchronization mode ('fast', 'full', "light")
  --ethstats value URL of ethstats server (nodename: secret @ host: port)
  --identity value custom node name
  --lightserv value Maximum allowed percentage of lightweight node services requests (0-90) (default: 0)
  --lightpeers value The maximum number of lightweight nodes allowed to access (default: 20)
  --lightkdf reduces the amount of memory and cup usage when generating keys

developer option
DEVELOPER CHAIN ​​OPTIONS:
  --dev Start a proof-of-stake network, save money in advance to the developer account, and start mining
  --dev.period value Block processing time ?, in development mode (0 = mining when transaction is processed) (default: 0)


ETHASH algorithm related options
ETHASH OPTIONS:
  --ethash.cachedir Store the ethash verification cache directory (directory: in datadir
  --ethash.cachesinmem value The number of ethash stored in memory, every 16mb (default 2)
  --ethash.cachesondisk value The percentage of ethash caches cached on disk (default: 3)
  --ethash.dagdir "/home/karalabe/.ethash" Directory address for storing ethash mining DAG, default (home directory)
  --ethash.dagsinmem value Number of recent ethash mining DAGs to keep in memory (1 + GB each) (default: 1)
  --ethash.dagsondisk value Number of recent ethash mining DAGs to keep on disk (1 + GB each) (default: 2)


Transaction pool related options
TRANSACTION POOL OPTIONS:
  --txpool.nolocals prohibit price exemption for locally submitted transactions
  --txpool.journal value Disk journal for local transaction to survive node restarts (default: "transactions.rlp")
  --txpool.rejournal value Time interval to regenerate the local transaction journal (default: 1h0m0s)
  --txpool.pricelimit value Minimum gas price limit to enforce for acceptance into the pool (default: 1)
  --txpool.pricebump value Price bump percentage to replace an already existing transaction (default: 10)
  --txpool.accountslots value Minimum number of executable transaction slots guaranteed per account (default: 16)
  --txpool.globalslots value Maximum number of executable transaction slots for all accounts (default: 4096)
  --txpool.accountqueue value Maximum number of non-executable transaction slots permitted per account (default: 64)
  --txpool.globalqueue value Maximum number of non-executable transaction slots for all accounts (default: 1024)
  --txpool.lifetime value Maximum total non-executed transaction queue time (default: 3h0m0s)


Performance tuning options
PERFORMANCE TUNING OPTIONS:
  --cache value how much to allocate to internal cache (megabytes) (minimum 16MB / database requirement)