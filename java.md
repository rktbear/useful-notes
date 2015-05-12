# Java

## Debugging with JDWP and `jdb`

### Preparation

The Java Virtual Machine (JVM) contains a remote debugging protocol called Java Debug Wire Protocol (JDWP).

Many IDE (Eclipse or IntelliJ) support this protocol for debugging but my weapon of choice is the command line debugger `jdb`.

Start the host application with JDWP enabled on port 8000:

```
java -Xdebug -Xrunjdwp:server=y,transport=dt_socket,address=8000,suspend=n -jar my.jar
```

Run `jdb` and connect to the host application:

```
jdb -attach <ipaddress>:8000
```

### Using `jdb`

When attaching to a running process execution is not suspended, once a breakpoint is added and hit execution
is suspended.

| Command                  | Description                                              |
|--------------------------|----------------------------------------------------------|
| 'stop <class>:<num>'     | Put a breakpoint in a class at a particular line number. |
| 'cont'                   | Continue running when execution is suspended.            |
| 'step'                   | Step into code when suspended.                           |  
| 'next'                   | Step over code when suspended.                           |  
| 'list'                   | Show the source code when suspended.                     |
| 'print <varName>'        | Print out a variable when suspended.                     |
| 'where'                  | Show the callstack when suspended.                       |
