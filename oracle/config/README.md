# Oracle configuration

Oracle uses oracle configuration file to specify your oracle settings. It is a simple json file, which you can write
yourself or use bootstrapped one.

Config file has these fields:

| Parameter        | Subparameter | Type                     | Default value   | Description                                            |
|------------------|--------------|--------------------------|-----------------|--------------------------------------------------------|
| contract_address |              | string                   |                 | hash address of VORCoordinator contract	            |
| eth_http_host    |              | string                   |                 | ethereum node HTTTP addess:port	                    |
| check_duration   |              | int                      | 15              | time to wait between requests to blockchain (seconds)  |
| network_id       |              | int64                    |                 | ethereum network id                                    |
| serve            |              | map/dict ({"key":value}) |                 | oracle serve parameters                                |
|                  | host         | string                   | 0.0.0.0         | oracle API server host                                 |
|                  | port         | int32                    | 8445            | oracle API server port                                 |
| first_block      |              | int64                    | 1               | the block to start from                                |
| log_file         |              | string                   | oracle.log      | log file for output                                    |
| gas_price_limit  |              | int64                    | 1000000         | max gas price                                          |
| keystorage       |              | map/dict ({"key":value}) |                 | keystorage parameters                                  |
|                  | file         | string                   | ./keystore.json | path to your keystore.json                             |
|                  | account      | string                   |                 | account to use to serve oracle                         |
| database         |              | string                   | ./oracle.db     | sqlite database store path                             |

NOTE: 
- some parameters are nested, don't forget about it, please
- don't forget that integer types mustn't have any quotes.


Here is the example of oracle configuration file:
```json
{
  "contract_address": "0x642F433756aD97Dc249A142F71BCbB84d5F5e79D",
  "eth_http_host": "http://192.168.1.2:7545",
  "network_id": 5777,
  "serve": {
    "host": "0.0.0.0",
    "port": 8445
  },
  "first_block": 1,
  "log_file": "./log.log",
  "keystorage": {
    "file": "./keystore.json",
    "account": "oracle"
  },
  "gas_price_limit": 1000000,
  "database": "./oracle.db",
}
```