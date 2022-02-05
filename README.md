# README

ftx websocket cpp with fixes

Fixes required locking the websocketpp version and updating boost installation location

## External

- `src/external/websocketpp`: websocketpp v0.8.0 forked from https://github.com/MuwazanaSA/websocketpp.git

## Build and Run

References
- https://github.com/ftexchange/ftx/issues/59

1. Build container
	```bash
	docker build -t ftxcc - < ./Dockerfile
	```
1. Open bash shell to container
	```bash
	docker run -it -v $(pwd):/ftxcc -w /ftxcc/bin ftxcc /bin/bash
	```
1. cmake and build
	```bash
	cmake ..
	make
	```
1. Run the websocket
	```bash
	cd ./src/example/ws_test
	```

### Example Output

Within container:

> root@xxxxxxxxxxxx:/ftxcc/bin# ./src/example/ws_test

```sh
msg: "{\"type\": \"error\", \"code\": 400, \"msg\": \"Not logged in\"}"
msg: "{\"type\": \"subscribed\", \"channel\": \"orderbook\", \"market\": \"BTC-PERP\"}"
msg: "{\"type\": \"subscribed\", \"channel\": \"ticker\", \"market\": \"BTC-PERP\"}"
msg: "{\"channel\": \"ticker\", \"market\": \"BTC-PERP\", \"type\": \"update\", \"data\": {\"bid\": 41570.0, \"ask\": 41571.0, \"bidSize\": 2.339, \"askSize\": 2.8949, \"last\": 41576.0, \"time\": 1644041458.39259}}"
...
msg: "{\"channel\": \"orderbook\", \"market\": \"BTC-PERP\", \"type\": \"partial\", \"data\": {\"time\": 1644041458.6191204, \"checksum\": 886602363, \"bids\": [[41570.0, 2.339], [41569.0, 1.2517]," ...
...

```

## Configure

1. Add your API keys to the clients
1. Run the examples:
	```bash
	./src/example/rest_test
	./src/example/ws_test
	```
