# PuTTY-Proxy-Jumphost
Having had problems setting up a proxy or jumphost connection to my target with PuTTY, I came up with this solution:

PuTTY via jumphost
==================

A) Set up the session
---------------------
```
Session:
	Host Name (or IP address):
		MYTARGET
	Port:
		22
	Connection type:
		SSH
		
Connection > Data:
	Auto-login username:
		targetuser
		
Connection > Proxy:
	Proxy hostname:
		MYPROXYHOST
	Port:
		22
	Username:
		proxyuser
	Telnet command, or local proxy command:
		E:\your\path\to\PLINK.EXE -i e:\your\path\to\\new\certificates\key-for-MYPROXYHOST.ppk -P %proxyport %user@%proxyhost -nc %host:%port
		NOTE THE DOUBLE BACKSLASH IN FRONT OF "new". The telnet command seems to interpret \n as a newline character.
Connection > SSH > Auth:
	Authentication parameters:
		[v] Allow agent forwarding
	Private key file for authentication:
		e:\your\path\to\new\certificates\key-for-MYTARGET_rsa.ppk
		NOTE THE LACK OF DOUBLE BACKSLASH HERE.
```		
B) Start Pageant and load keys
------------------------------

C) Start the connection in PuTTY
--------------------------------
