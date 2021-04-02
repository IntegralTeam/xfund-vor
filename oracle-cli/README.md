# Oracle-CLI
A CLI manage your Oracle service
### Commands
Use `oracle-cli help` command to get all commands, you might see this:
```
CLI to manage your Oracle.

Note:
 You need to run "oracle start -c [config_path | optional] -k [key | optional]" to start your daemon before using CLI.

Usage:
  oracle-cli [flags]
  oracle-cli [command]

Available Commands:
  about              List info about your oracle
  changefee          Change Oracle fee
  help               Help about any command
  register           Register your new Oracle
  setproviderpaysgas Set who pays gas
  settings           Oracle CLI settings command
  stop               Stop oracle
  withdraw           Withdraw your xFUND

Flags:
  -h, --help   help for oracle-cli

Use "oracle-cli [command] --help" for more information about a command.
```


### Install
Installing oracle-cli so it can be accessible from any directory  
with command like:  
`oracle-cli about`
1. Clone repo to your machine with:  
`git clone https://github.com/unification-com/xfund-vor`
2. Go to oracle-cli directory  
`cd xfund-vor/oracle-cli`
3. Run go install to compile and add CLI to your PATH (to make it accessible from anywhere)  
`go install`

### Build
If you don't need oracle-cli to be installed to your PATH and want  
just to build it and make runnable with command like  
`<path to your binary>/oracle-cli about`

1. Repeat steps 1 and 2 from Install paragraph
2. Run go build to build your CLI  
`go build -o <preferred path to binary>/oracle-cli .`
   
### First run
Please check if you have an __oracle key__ and oracle is running before using __oracle-cli__

1. Set up your CLI with command:  
`oracle-cli settings`  
   CLI will let you choose what parameter to change (but it is a first run, so you will need to set all of them)
```
Current oracle-cli settings:
        Oracle Host:
        Oracle Port:
        Key: ...

Okay, let's configure your CLI
What do you want to do?
1 - Set HTTP/cli Oracle Key
2 - Set Oracle host address
3 - Set Oracle host port
0 - Exit
Action: 1

Oracle host key (ex.: rod0gbc3mhyxdiah2vwialx1q3osk5cw): <your oracle key>

Okay, let's configure your CLI
What do you want to do?
1 - Set HTTP/cli Oracle Key
2 - Set Oracle host address
3 - Set Oracle host port
0 - Exit
Action: 2

Oracle host address (ex.: 127.0.0.1): <your oracle worker address>

Okay, let's configure your CLI
What do you want to do?
1 - Set HTTP/cli Oracle Key
2 - Set Oracle host address
3 - Set Oracle host port
0 - Exit
Action: 3

Oracle host port (ex.: 8888): <your oracle worker port>

Okay, let's configure your CLI
What do you want to do?
1 - Set HTTP/cli Oracle Key
2 - Set Oracle host address
3 - Set Oracle host port
0 - Exit
Action: 0
```   

2. Check your oracle status using  
   - root command: `oracle-cli` (has to output: `Oracle status:  alive`)
   - about command: `oracle-cli about` (has to output some information about your oracle)
   
