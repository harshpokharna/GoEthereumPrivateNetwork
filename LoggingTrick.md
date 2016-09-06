You can remove the clutter from your interactive console and divert it to another terminal window. All you have to do is: 

Open another terminal window
~~~
tty
~~~

You will get an output 
~~~
/dev/ttys001
~~~

In your main terminal window
~~~
geth console 2>> /dev/ttys001
~~~


Now monitor your node wthout cluttering the console.
