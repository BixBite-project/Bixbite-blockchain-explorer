# Bixbite Blockchain Explorer


## Compilation on Ubuntu 16.04

##### Compile latest Bixbite development version

Download and compile recent Bixbite into your home folder:

```bash
# first install Bixbite dependecines
sudo apt update

sudo apt install git build-essential cmake libboost-all-dev miniupnpc libunbound-dev graphviz doxygen libunwind8-dev pkg-config libssl-dev libcurl4-openssl-dev libgtest-dev libreadline-dev libzmq3-dev libsodium-dev

# go to home folder
cd ~

git clone --recursive https://github.com/BixBite-project/bixbite.git

cd bixbite/

make
```

##### Compile and run the explorer

Once the Bixbite is compiles, the explorer can be downloaded and compiled
as follows:

```bash
# go to home folder if still in ~/Bixbite
cd ~

# download the source code
git clone https://github.com/BixBite-project/Bixbite-blockchain-explorer.git

# enter the downloaded sourced code folder
cd Bixbite-blockchain-explorer

# make a build folder and enter it
mkdir build && cd build

# create the makefile
cmake ..

# altearnatively can use: cmake -DMONERO_DIR=/path/to/bixbite_folder ..
# if monero is not in ~/bixbite
#
# also can build with ASAN (sanitizers), for example
# cmake -DSANITIZE_ADDRESS=On ..

# compile
make
```

When compilation finishes executable `xmrblocks` should be created. Before running
please make sure that  `~/Downloads` folder exists and is writable.
Time zone library that explorer is using, puts there
its database of time zone offsets

To run it:
```
./xmrblocks
```

By default it will look for blockchain in its default location i.e., `~/.Bixbite/lmdb`.
You can use `--bc-path` option if its in different location.

Go to your browser: http://127.0.0.1:8081

## The explorer's command line options

```
xmrblocks, Onion Bixbite Blockchain Explorer:
  -h [ --help ] [=arg(=1)] (=0)         produce help message
  -t [ --testnet ] [=arg(=1)] (=0)      use testnet blockchain
  -s [ --stagenet ] [=arg(=1)] (=0)     use stagenet blockchain
  --enable-pusher [=arg(=1)] (=0)       enable signed transaction pusher
  --enable-mixin-details [=arg(=1)] (=0)
                                        enable mixin details for key images,
                                        e.g., timescale, mixin of mixins, in tx
                                        context
  --enable-key-image-checker [=arg(=1)] (=0)
                                        enable key images file checker
  --enable-output-key-checker [=arg(=1)] (=0)
                                        enable outputs key file checker
  --enable-json-api [=arg(=1)] (=1)     enable JSON REST api
  --enable-tx-cache [=arg(=1)] (=0)     enable caching of transaction details
  --show-cache-times [=arg(=1)] (=0)    show times of getting data from cache
                                        vs no cache
  --enable-block-cache [=arg(=1)] (=0)  enable caching of block details
  --enable-js [=arg(=1)] (=0)           enable checking outputs and proving txs
                                        using JavaScript on client side
  --enable-autorefresh-option [=arg(=1)] (=0)
                                        enable users to have the index page on
                                        autorefresh
  --enable-emission-monitor [=arg(=1)] (=0)
                                        enable Bixbite total emission monitoring
                                        thread
  -p [ --port ] arg (=8081)             default explorer port
  --testnet-url arg                     you can specify testnet url, if you run
                                        it on mainnet or stagenet. link will
                                        show on front page to testnet explorer
  --stagenet-url arg                    you can specify stagenet url, if you
                                        run it on mainnet or testnet. link will
                                        show on front page to stagenet explorer
  --mainnet-url arg                     you can specify mainnet url, if you run
                                        it on testnet or stagenet. link will
                                        show on front page to mainnet explorer
  --no-blocks-on-index arg (=10)        number of last blocks to be shown on
                                        index page
  --mempool-info-timeout arg (=5000)    maximum time, in milliseconds, to wait
                                        for mempool data for the front page
  --mempool-refresh-time arg (=5)       time, in seconds, for each refresh of
                                        mempool state
  -b [ --bc-path ] arg                  path to lmdb folder of the blockchain,
                                        e.g., ~/.bitmonero/lmdb
  --ssl-crt-file arg                    path to crt file for ssl (https)
                                        functionality
  --ssl-key-file arg                    path to key file for ssl (https)
                                        functionality
  -d [ --deamon-url ] arg (=http:://127.0.0.1:44041)
                                        Bixbite deamon url
```
