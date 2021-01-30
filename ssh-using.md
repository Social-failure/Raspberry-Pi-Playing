# how to use ssh to connect with your own raspberry pi

connect with your raspberry pi with ssh so you don't need another screen for display, another keyboard and another mouse

>   you should set wifi and ssh of your raspberry pi on by default. 

1.  connect with your raspberry with wifi which your computer is also connecting with

2.  use ``ifconfig | grep broadcast | arp -a`` to know the ip address of your raspberry pi

3.  use ``ssh pi@<ip address>`` to connect with your raspberry pi


