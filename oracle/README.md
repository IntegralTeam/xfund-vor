# Oracle
API backend that Oracle client contracts on Ethereum make requests to. The backend utulizes Solidity contract ABIs to generate types for interacting with Ethereum contracts.

### Commands
Oracle has only one command: `oracle start` to start your daemon  
This command also has flags:
```
    -c (--config) [oracle config path]       to specify your configuration file path  
    -k (--key)    [oracle access key]        to specify your decryption key on the fly  (inaccessible when running for the first time)
```
__NOTE: specifying --key flag is not the most secure solution if there is anyone who can access server running oracle.  
Anyways it may be very useful to run your oracle in the detached mode.__

### Configuration
__Please, create a configuration file before running oracle.__  
More info [here](./config/README.md)

### First run
1. Create your configuration file
2. Run `oracle start` to start your daemon and specify --config flag unless your configuration file is based at ./config.json
3. Oracle will ask you to create a new account and input 
   - account name 
   - oracle fee
   - who pays gas (provider: true | false)
   - a private key (or it will offer you to generate new)
4. After previous step oracle will generate an access key (we also call it token or secret)  
   (if you requested generation of a new private key, Oracle will also output it)  
---
   __WARNING: SAVE THIS KEYS AND KEEP IT IN SECRET.   
   Oracle access key is used to manage your Oracle and decrypt your private key storage while private key is used to access your oracle and coins.__
---
5. Set account name in your configuration file for future use
6. If you have coins on your wallet, your oracle will start, and you will be able to mange it via oracle-cli

### Not a first run
1. You can your oracle the same way as in "First run" 2d point and oracle will ask you to input your oracle access key  
or you can specify --key <oracle access key> flag to run your oracle immediately

### Running in background

Running your daemon in background to make it not to be associated with the terminal or login shell.  
__WARNING: Please, don't start your oracle as a daemon if it is the first run.__

#### You can use any tools to daemonize your Oracle.  

For example you can use `nohup`:  
`nohup orace start [flags]`

Or you can use `daemonize`:  
`daemonize [-a] [-c directory] [-e stderr] [-o stdout] [-p pidfile] [-l lockfile] [-u user] [-v] <path to your oracle>/oracle [arg] ...`  


#### Please, note that your oracle will shutdown if you reboot your host.

### Install
Installing oracle so it can be accessible from any directory  
with command like:  
`oracle start`
1. Clone repo to your machine with:  
   `git clone https://github.com/unification-com/xfund-vor`
2. Go to oracle-cli directory  
   `cd xfund-vor/oracle`
3. Run go install to compile and add CLI to your PATH (to make it accessible from anywhere)  
   `go install`
   
### Build
If you don't need oracle-cli to be installed to your PATH and want  
just to build it and make runnable with command like  
`<path to your binary>/oracle start`

1. Repeat steps 1 and 2 from Install paragraph
2. Run go build to build your CLI  
   `go build -o <preferred path to binary>/oracle .`
   

### Common issues

- Oracle fails after first run with new private key  
Please, top up your balance to pay gas for Oracle registration and try again.   
- Private key was previously used in Oracle, but when I try to add it as new, Oracle fails.
It is ok, you just need to open your keystore and manually set `"registered":true` next to your private key.