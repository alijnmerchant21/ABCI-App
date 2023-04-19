# ABCI-App

This ABCI application is based on CometBFT tutorial for [Creating an application in Go](https://docs.cometbft.com/v0.37/guides/go)

The application is based on ABCI++ and hence consolidates - `BeginBlock`, `EndBlock` and `DeliverTX` into `FinalizeBlock`.

## Run this application

**Clone the repo**

**From the root of your project, run:** <br>
`go run github.com/cometbft/cometbft/cmd/cometbft@v0.38.0-alpha.1 init --home /tmp/cometbft-home `

**Rebuild the app:** <br>
`go build -mod=mod`

**Run:** <br>
`./kvstore -kv-home /tmp/badger-home`

**We need to start CometBFT service and point it to our application. 
Open a new terminal window and cd to the same folder where the app is running. 
Then execute the following command:** <br>
`go run github.com/cometbft/cometbft/cmd/cometbft@v0.38.0-alpha.1 node --home /tmp/cometbft-home --proxy_app=127.0.0.1:5000`

**Using the application:** <br>
`curl -s 'localhost:26657/broadcast_tx_commit?tx="cometbft=rocks"'`

**Query TX** <br>
`curl -s 'localhost:26657/abci_query?data="cometbft"'`
