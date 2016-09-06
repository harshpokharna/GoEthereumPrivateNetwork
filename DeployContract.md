You should have a solidity compiler built in on your geth console. To test it, use this command
~~~
eth.getCompilers()
~~~

If you have it installed, it should output something like this
~~~
['Solidity' ]
~~~

If instead the command returns an error, then you need to install it.

In the Javascript console of your node (Check out the example contract)
~~~
>greeterSource = 'contract mortal { address owner; function mortal() { owner = msg.sender; } function kill() { if (msg.sender == owner) suicide(owner); } } contract greeter is mortal { string greeting; function greeter(string _greeting) public { greeting = _greeting; } function greet() constant returns (string) { return greeting; } }'
>greeterCompiled = web3.eth.compile.solidity(greeterSource)
>_greeting = "Hello World!"
>greeterContract = web3.eth.contract(greeterCompiled.greeter.info.abiDefinition);
>greeter = greeterContract.new(_greeting,{from:web3.eth.accounts[0], data: greeterCompiled.greeter.code, gas: 1000000})
~~~

At the end of this process, you will get an address where the contract is placed.

Note: You will have to start mining for this contract to be put on the chain

To check if everything works fine
~~~
>greeter.greet();
~~~

You should see 'Hello World'!

