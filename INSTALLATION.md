<h1> Installation guide </h1>

<h2> Dependencies </h2>


* You will either need [Go-ethereum](https://github.com/ethereum/go-ethereum/wiki/Building-Ethereum) or [Parity](https://github.com/paritytech/parity#simple-one-line-installer-for-mac-and-ubuntu)
  we will be using the parity client in this guide

* If you are planning to build Raiden from source, as we'll in this guide- You need to have `solc`- The Ethereum's solidity compiler installed.
  Refer to [this](http://solidity.readthedocs.io/en/latest/installing-solidity.html) documentation for the installation steps. 
  
* You will also need to installed [system dependencies of pythapp](https://github.com/ethereum/pyethapp/#installation-on-ubuntudebian) 


* The lastest master branch of Raiden isn't compatible with Python2, You need to have Python3 installed in your system

<h2> Installing Raiden from source </h2>

* Clone the Github's Repository

 `git clone https://github.com/raiden-network/raiden.git`
 
* Navigate to the directory
 
  `cd raiden`

* It’s advised to create a [virtualenv](http://docs.python-guide.org/en/latest/dev/virtualenvs/) for Raiden and install all python dependencies there.

* After setting up the virtualenv, proceed to install the dependencies for Raiden

`pip install --upgrade -r requirements.txt`

`python3 setup.py develop`


* Run the Parity Client and let it sync with the Ropsten testnet

You will need ports 8545, 8546 and 8180 open if you are trying to run parity remotely.

`parity --chain ropsten --bootnodes "enode://076bba608093d171bfdbb905b76aa089e2d746eaf263a2c604dfa143ba609548fdff5d734081a617f48a6802df7a71a4ee48f2175d89d17d333be3e747c87e72@138.197.111.208:30303" --jsonrpc-cors* --unsafe-expose`

If some problem arises or some bootnodes are dead, have a look at [Ropsten Readme](raiden-network.readthedocs.io/en/stable/overview_and_guide.html)

* After syncing Ropsten, Create an account on the Ropsten testnet by syncing to the URL that Parity shows, It is usually

`http://127.0.0.1:8180`

* Create an account on Parity and fill it in with some test ether :beer: :beer: from ` http://faucet.ropsten.be:3001/ ` ,launch Raiden with the path of your keystore supplied: 

`raiden --keystore-path ~/.local/share/io.parity.ethereum/keys/test --gas-price 10000000000`

use the `--api-address` flag if you want to costomize the IP and port raiden will listen on

* Select the Ethereum account when prompted, and type in the account’s password.

* For running the web ui, make sure you have nodejs installed, and then:

`python setup.py compile_webui`

Lauch raiden again with the aforementioned command
