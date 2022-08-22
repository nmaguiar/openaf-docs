---
layout: default
title: ssh
parent: Reference
grand_parent: OpenAF docs
---


## ssh

### SSH.cd

__SSH.cd(aPath)__

````
Changes the remote directory to the corresponding path.
````
### SSH.close

__SSH.close()__

````
Closes the SSH connection.
````
### SSH.df

__SSH.df(aPath) : Map__

````
Tries to return an object, for the remote provided path, with size, used space, available space,  availableForRoot space and capacityPercentage.
````
### SSH.exec

__SSH.exec(aCommand, aStdIn, shouldOutputAlso, pty, outputMap, callbackFunc) : Object__

````
Executes a command over the SSH connection. You can optionally provide the input and indicate that it shouldOutputAlso  (boolean) to stdout and if you want to allocate a pty (boolean). The stderr will be stored in __stderr and also output  if shouldOutputAlso = true. If outputMap instead of the stdout string a map with stdout, stderr and exitcode will be returned. A callbackFunc can be provided, if shouldOutputAlso is undefined or false, that will receive, as parameters, an output stream, a error stream and an input stream. If defined the stdout and stderr won't be available for the outputMap if true. Example:

ssh.exec("someCommand", void 0, void 0, false, void 0, false, function(o, e, i) { ioStreamReadLines(o, (f) => { print("TEST | " + String(f)) }, void 0, false) });


````
### SSH.execSudo

__SSH.execSudo(aCommandWithSudo, aUser, aStdIn, shouldOutputAlso, pty, outputMap, callbackFunc) : Object__

````
Executes a command over the SSH connection using sudo to aUser. You can optionally provide the input and indicate that it shouldOutputAlso (boolean) to stdout and if you want to allocate a pty (boolean). The stderr will be stored in  __stderr and also output if shouldOutputAlso = true. If outputMap instead of the stdout string a map with stdout, stderr and exitcode will be returned. A callbackFunc can be provided, if shouldOutputAlso is undefined or false, that will receive, as parameters, an output stream, a error stream and an input stream. If defined the stdout and stderr won't be available for the outputMap if true. Example:

ssh.execSudo("someCommand", void 0, void 0, false, void 0, false, function(o, e) { ioStreamReadLines(o, (f) => { print("TEST | " + String(f)) }) });


````
### SSH.get

__SSH.get(aRemoteFilePath, aLocalFilePath, monitor) : String__

````
Retrieves a file, using the SFTP connection, from aRemoteFilePath to aLocalFilePath. Use SSH.getBytes in case you are reading a binary file. Optionally you can provided a callback function called monitor (see more in ow.format.sshProgress)
````
### SSH.getBytes

__SSH.getBytes(aRemoteFile) : anArrayOfBytes__

````
Returns an array of bytes with the contents of aRemoteFilePath, using the SFTP connection.
````
### SSH.getExecChannel

__SSH.getExecChannel() : Object__

````
Obatins the internal SSH session exec channel.
````
### SSH.getFile

__SSH.getFile(aRemoteFile, aLocalFile) : anArrayOfBytes__

````
Retrieves a remote file over the SSH connection to be stored on the local path provided. If aLocalFile is not provided the remote file contents will be returned as an array of bytes.
````
### SSH.getSftpChannel

__SSH.getSftpChannel() : Object__

````
Obtains the internal SSH session sftp channel.
````
### SSH.listFiles

__SSH.listFiles(aPath) : Map__

````
Returns a files array where each entry has filename, longname, filepath, size, permissions, lastModified,  createTime, isDirectory and isFile.
````
### SSH.mkdir

__SSH.mkdir(aPath)__

````
Tries to create a remote directory for the provided aPath.
````
### SSH.put

__SSH.put(aSourceFilePath, aRemoteFilePath, monitor)__

````
Copies a aSourceFilePath to aRemoteFilePath, using the SFTP connection. Optionally you can provided a callback function called monitor (see more in ow.format.sshProgress)
````
### SSH.putBytes

__SSH.putBytes(aRemoteFilePath, bytes, monitor)__

````
Writes an array of bytes on aRemoteFilePath, using the SFTP connection. Optionally you can provided a callback function called monitor (see more in ow.format.sshProgress)
````
### SSH.pwd

__SSH.pwd() : String__

````
Returns the current remote path.
````
### SSH.rename

__SSH.rename(aOriginalName, aNewName)__

````
Renames a remote original filename to a newname.
````
### SSH.rm

__SSH.rm(aFilePath)__

````
Removes a remote filename at the provided aFilePath.
````
### SSH.rmdir

__SSH.rmdir(aPath)__

````
Removes a remote directory at the provided aPath.
````
### SSH.sendFile

__SSH.sendFile(aSourceFile, aRemoteFile)__

````
Sends a source file over the SSH connection to be stored on the remote path provided.
````
### SSH.setTimeout

__SSH.setTimeout(aTimeout)__

````
Sets aTimeout in ms for the SSH connection.
````
### SSH.sftpGet

__SSH.sftpGet(aRemoteFile, aLocalFile, monitor) : JavaStream__

````
Retrieves a remote file over the SFTP connection to be stored on the local path provided. If aLocalFile is not provided the remote file contents will be returned as a Java Stream Optionally you can provided a callback function called monitor (see more in ow.format.sshProgress)
````
### SSH.sftpPut

__SSH.sftpPut(aSource, aRemoteFile, monitor)__

````
Sends aSource file (if string) or a Java stream to a remote file path over a SFTP connection. Optionally you can provided a callback function called monitor (see more in ow.format.sshProgress)
````
### SSH.SSH

__SSH.SSH(aHost, aPort, aLogin, aPass, anIdentificationKey, withCompression, aTimeout, noStrictHostKeyChecking) : SSH__

````
Creates an instance of a SSH client (and connects) given a host, port, login username, password and,  optionally a identity file path and the indication of use of compression. Alternatively you can provide  just a simple url where aHost = ssh://user:pass@host:port/identificationKey?timeout=1234&compression=true.
````
### SSH.tunnelLocal

__SSH.tunnelLocal(aLocalPort, aRemoteHost, aRemotePort)__

````
Creates a TCP tunnel between a local port and a remote host and port over the SSH connection.
````
### SSH.tunnelLocalBind

__SSH.tunnelLocalBind(aLocalInterface, aLocalPort, aRemoteHost, aRemotePort)__

````
Creates a TCP tunnel, on the aLocalInterface only, between a local port and a remote host and port over the SSH connection.
````
### SSH.tunnelRemote

__SSH.tunnelRemote(aRemotePort, aLocalAddress, aLocalPort)__

````
Creates a TCP tunnel between a local host and port to be accessed from a remote port over the SSH connection.
````
### SSH.tunnelRemoteBind

__SSH.tunnelRemoteBind(aRemoteInterface, aRemotePort, aLocalAddress, aLocalPort)__

````
Creates a TCP tunnel, on the aRemoteInterface only, between a local host and port to be accessed from a remote  port over the SSH connection.
````
