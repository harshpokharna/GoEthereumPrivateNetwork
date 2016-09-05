# GoEthereumPrivateNetwork
Setting up and running a private network using geth

Install geth (Go client for Ethereum)
~~~
brew tap ethereum/ethereum
brew install ethereum
~~~

Install gethdev (gethdev is a small wrapper around the geth command, which automatically sets some parameters to create a private test blockchain)
~~~
npm install -g gethdev
~~~

Close all other apps (Mist, etc) that might be using geth. Open a terminal window 
~~~
gethdev
~~~

The output of the above command will contain the path to an ipc file. Note it down.

Open another terminal window (keep the previous window running)
~~~
get attach ipc:path/to/ipc/file
~~~


