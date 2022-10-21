# ps

## To list every process on the system:

```shell
ps aux
```

## To list a process tree

```shell
ps axjf
```

## To list every process owned by foouser:

```shell
ps -aufoouser
```

## To list every process with a user-defined format:

```shell
ps -eo pid,user,command
```

## List the processes being run by a particular set of usernames

```shell
ps -f -u username1, username2, .... ,usernameN 
```

## Display a list of processes with a particular parent ID (5589)

Note that when a process is launched it may spawn several other sub processes which all share a common parent process ID


```shell
ps -f -ppid 5589
```

## List processes with given PIDs

```shell
ps -f -p 25001, 4567, 789
```

## Display all processes owned by the current user

```shell
ps -U $USER
```

## Sort processes based on CPU and memory usage (useful for finding memory leaks)

```shell
ps aux --sort pmem
```

## Show environment variable settings for each PID

```shell
COLUMNS=10240 ps axel
```
