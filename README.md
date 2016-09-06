# GoEthereumPrivateNetwork
Setting up and running a private network using geth

Install geth (Go client for Ethereum)
~~~
brew tap ethereum/ethereum
brew install ethereum
~~~

Now, we want to start a node with a custom genesis block in it's own data directory and assign the ports to it

Init a Custom Genesis Block in a data directory (customgenesis.json is available in this repository)
~~~
eth --datadir "/Users/user/workspace/Ethereum/Data/node1" init "/Users/user/workspace/Ethereum/Data/customgenesis.json"
~~~

Create a new account
~~~
geth --datadir "/Users/user/workspace/Ethereum/Data/node1" account new
~~~

Start the node
~~~
geth --identity "Node1" --datadir "/Users/user/workspace/Ethereum/Data/node1" --rpc --rpcport "8080" --rpccorsdomain "*" --port "30303" --nodiscover --rpcapi "db,eth,net,web3" --networkid 42 console
~~~

The node has now started and you will see a Javascript console in your terminal window.

Now open another terminal window and repeat the above steps for another node (which means a different data directory, different identity, different rpcport, different port but same networkid)

Once the other node has also started, type the following command in the Javascript console
~~~
>admin.nodeInfo
~~~

You will get something like
~~~
"enode://760b26b805cb2b3ad14761406fd469b1c317423d5f40c39ceedb1d083a5fe7b2022ab78ed73b34a41018e5fa99d53b5ad7ad0e3452a43f6846116b24a426dff5@[::]:30304?discport=0"
~~~

Go to the other terminal window. In the Javascript console add
~~~
admin.addPeer("enode://760b26b805cb2b3ad14761406fd469b1c317423d5f40c39ceedb1d083a5fe7b2022ab78ed73b34a41018e5fa99d53b5ad7ad0e3452a43f6846116b24a426dff5@[::]:30304?discport=0")
~~~

Now both the nodes are connected

You can check this by
~~~
>admin.peers
~~~

To add more nodes to the network, simply follow the same steps!

This repository also contains guide for generating ether through mining and then transfering it between nodes (Check out SendingEther.md)


