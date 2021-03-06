![license](https://img.shields.io/github/license/iotaledger/iri.svg)

## KOTA

The KOTA repository is the main [IOTA-iri](https://github.com/iotaledger/iri) Reference Implementation and the embodiment of the IOTA network specification. 

This is a full-featured [[IOTA]](https://iota.org/) node with a convenient JSON-REST HTTP interface.
It allows users to become part of the [[IOTA]](https://iota.org) network as both a transaction relay
and network information provider through the easy-to-use [[API]](https://iota.readme.io/reference).

It is specially designed for users seeking a fast, efficient and fully-compatible network setup.

Running an IRI node also allows light wallet users a node to directly connect to for their own wallet transactions.

* **Latest release:** 1.4.2.4 Release
* **License:** GPLv3

# Articles
- [steemit 0](https://steemit.com/kr/@kilu83/iota)
- [steemit 1](https://steemit.com/kr/@jruit/iota)

# How to get started

The IOTA network is an independent peer-to-peer network with a first-user, friend-to-friend, network structure:

- As a 'first-user' network, to access the data streams and APIs that other users provide, you must first exchange your IP and port configuration with a current user.

- As a 'friend-to-friend' network, you have the privilege of joining new users into the network through your node
by adding them to your approved neighbors list — ensuring that you both broadcast to them and also receive their broadcasts.

You can **find neighbors** quickly at both our [[Discord Community]](https://discord.gg/7Gu2mG5) and [[forum.iota.org]](https://forum.iota.org/).
 
Everyone will be welcoming and very happy to help you get connected.
If you want to get tokens for your testcase, please just ask in one of the communication channels.

### Compiling yourself  

Make sure to have Maven and Java 8 installed on your computer.

#### To compile & package
```
$ git clone https://github.com/piction-network/KOTA.git
$ cd iri
$ mvn clean compile
$ mvn package
```

This will create a `target` directory in which you will find the executable jar file that you can use.

### How to run IRI 

#### Locally

Running IRI is quick and easy, and you can usually run it without admin rights.
Below is a list of command line options.

At a minimum, the port must be specified on the command-line — e.g., '`-p 14265`' 
or in the `iota.ini` file — e.g., '`PORT = 14265`'.

If the '`iota.ini`' file exists, it will be read.
The port and all the command line options below take precedence over values specified in the ini config file.

Here is an example script that specifies only the port, with all other setting to be read from the ini file **if it exists**:

```
java -jar iri.jar -p 14265
```

### Command Line Options 

Option | Shortened version | Description | Example Input
--- | --- | --- | --- 
`--port` | `-p` | This is a *mandatory* option that defines the port to be used to send API commands to your node | `-p 14265`
`--neighbors` | `-n` | Neighbors that you are connected with will be added via this option. | `-n "udp://148.148.148.148:14265 udp://[2001:db8:a0b:12f0::1]:14265"`
`--config` | `-c` | Config INI file that can be used instead of CLI options. See more below | `-c iri.ini`
`--udp-receiver-port` | `-u` | UDP receiver port | `-u 14600`
`--tcp-receiver-port` | `-t` | TCP receiver port | `-t 15600`
`--testnet` | | Makes it possible to run IRI with the IOTA testnet | `--testnet`
`--remote` | | Remotely access your node and send API commands | `--remote`
`--remote-auth` | | Require authentication password for accessing remotely. Requires a correct `username:hashedpassword` combination | `--remote-auth iotatoken:LL9EZFNCHZCMLJLVUBCKJSWKFEXNYRHHMYS9XQLUZRDEKUUDOCMBMRBWJEMEDDXSDPHIGQULENCRVEYMO`
`--remote-limit-api` | | Exclude certain API calls from being able to be accessed remotely | `--remote-limit-api "attachToTangle, addNeighbors"`
`--send-limit`| | Limit the outbound bandwidth consumption. Limit is set to mbit/s | `--send-limit 1.0`
`--max-peers` | | Limit the number of max accepted peers. Default is set to 0 (mutual tethering) | `--max-peers 8`
`--dns-resolution-false` | | Ignores DNS resolution refreshing  | `--dns-resolution-false`	
### INI File

You can also provide an ini file to store all of your command line options and easily update (especially neighbors) if needed. You can enable it via the `--config` flag. Here is an example INI file:
```
[IRI]
PORT = 14265
UDP_RECEIVER_PORT = 14600
NEIGHBORS = udp://my.favorite.com:14600
IXI_DIR = ixi
DEBUG = false
DB_PATH = db
```
