Ethereum Network Intelligence API
============
[![Build Status][travis-image]][travis-url] [![dependency status][dep-image]][dep-url]

This is the backend service which runs along with ethereum and tracks the network status, fetches information through JSON-RPC and connects through WebSockets to [eth-netstats](https://github.com/XAILESFINANCE/netstats-dashboard) to feed information. For full install instructions please read the [wiki](https://github.com/ethereum/wiki/wiki/Network-Status).


## Prerequisite
* node
* npm


## Installation on an Ubuntu

```bash

# update packages
sudo apt-get update -y
sudo apt-get upgrade -y

# add node service
sudo npm install
sudo npm install pm2 -g

# create configuration
git clone https://github.com/XAILESFINANCE/eth-net-intelligence-api.git
cd eth-net-intelligence-api
cp app.json.example app.json
```

## Configuration

Configure the app modifying [app.json](/eth-net-intelligence-api/blob/master/app.json).

```json
"env":
	{
		"NODE_ENV"        : "production", // tell the client we're in production environment
		"RPC_HOST"        : "localhost", // eth JSON-RPC host
		"RPC_PORT"        : "8545", // eth JSON-RPC port
		"LISTENING_PORT"  : "30303", // eth listening port (only used for display)
		"INSTANCE_NAME"   : "", // whatever you wish to name your node
		"CONTACT_DETAILS" : "", // add your contact details here if you wish (email/skype)
		"WS_SERVER"       : "https://status.xvitesse.com", // path to eth-netstats WebSockets api server
		"WS_SECRET"       : "Contact support to get password", // WebSockets api server secret used for login
		"VERBOSITY"       : 2 // Set the verbosity (0 = silent, 1 = error, warn, 2 = error, warn, info, success, 3 = all logs)
	}
```

## Run

Run it using pm2:

```bash
cd ~/eth-net-intelligence-api
pm2 start app.json
```

