
Go to both your terminal windows and in the console
~~~
>web3.fromWei(eth.getBalance(eth.coinbase), "ether")
~~~

It should show '0'

Now in one of the node
~~~
>miner.start()
~~~

When some blocks have been mined
~~~
>miner.stop()
~~~

In that node, again check balance
~~~
>web3.fromWei(eth.getBalance(eth.coinbase), "ether")
~~~

It will now show some non-zero value.

To send ether from this node to the other node
~~~
> eth.sendTransaction({from:sender, to:receiver, value: amount})
~~~

Again start mining in the sender node and let the transaction be mined. Once you stop the mining again, go to the other node and check balance. It will reflect the ether sent to it.
