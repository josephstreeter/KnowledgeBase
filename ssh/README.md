# Secure Shell - SSH
Secure Shell (SSH) is a protocol that allows a user to securly access a remote system for tasks such as adminstration and file copy. 
## Generate Key
The following command will generate a new SSH key
```
ssh-keygen -t rsa 
```
## Authenticate with a Specific Key
A specific key can be specified in the SSH command. 
```
ssh -i ~/.ssh/id_rsa_host username@host.domain.com
```
## Compare Public Key Fingerprint
If you are having trouble logging into a host or a service you can confirm that the fingerprint of your public key matches what was uploaded.
```
ssh-keygen -l -E md5 -f ~/.ssh/id_rsa_ado.pub
```
## Test Authentication
The following command will test authentiction to a specific host. 
```
ssh -T git@ssh.dev.azure.com
```
In the case of source control services, you may get the following error. This is simply because the service is not intended for shell access and is completely normal. 
```
remote: Shell access is not supported.
```

# Secure File Copy - SCP
SCP uses the SSH protocol to securly copy files between systems. SCP is often included as part of the SSH client application.
## Copy a file
The SCP command for copying a file from a local path to a remote host
```
scp file host:path
```
For example:
```
scp script.sh admin@host.domain.com:/home/admin/
```
The SCP command for copying a file from the remote host to a local path.
```
scp host:file path
```
For example:
```
scp admin@host.domain.com:/home/admin/script.sh script.sh
```
## Copy a Directory
The SCP command for recursivly copying a directory from a local path to a remote host.
```
scp -r host:path/directory path
```
For example:
```
scp -r admin@host.domain.com:/home/admin/scripts .
```
# Configure SSH
## Execute Graphical Applications Remotely
Enabling X11 Forwarding and Agent Forwarding will allow a user to execute a graphical application on the remote host.
```
ForwardAgent yes
ForwardX11 yes
```

# Port Forwarding
SSH can be used to create secure tunnels for access to applications and services.
## Local Forwarding
Local forwarding is used to forward a port from the client host to a remote host. The user creates a local port on the client host which listens for connections. SSH then tunnels that traffic to the remote host. 
Local forwarding is used for:
- Bypassing a firewall that prevents a protocol or to bypass web content filtering
- Tunnelling sessions or copying files to a remote host through a jump server or bastion host
- Remote access to an internal host or service from an external host
- Connecting to a private resource over a public network

Local port forwarding is configured using the -L option:
```
ssh -L 80:host.local-domain.com:80 host.remote-domain.com
```
This example opens a connection to the 'host.remote-domain.com' bastion host, and forwards all connections to port 80 on the local machine, 'host.local-domain.com' to port 80 on 'host.remote-domain.com'.

By default, anyone (even on different machines) can connect to the specified port on the SSH client machine. 
However, this can be restricted to programs on the same host by supplying a bind address:
```
ssh -L 127.0.0.1:80:host.local-domain.com:80 host.remote-domain.com
```
The 'LocalForward' option can be used to configure forwarding without having to specify it on command line.

## Remote Forwarding
Remote forwading is similar to local forwarding except that is initiated from the remote host. 

Remote SSH port forwarding is specified by using the -R option. 
For example:
```
ssh -R 8080:localhost:80 host.domain.com
```
This example would allow someone remote access to an private service, such as a web server. Remote forwading could be performed by an employee working from home or by an attacker (AKA 'Shoveling Shell') who has established persistant access to the private environment.

=====> This needs to be rewritten
By default, OpenSSH only allows connecting to remote forwarded ports from the server host. However, the GatewayPorts option in the server configuration file sshd_config can be used to control this. The following alternatives are possible:
```
GatewayPorts no
```
This prevents connecting to forwarded ports from outside the server computer.
```
GatewayPorts yes
```
This allows anyone to connect to the forwarded ports. If the server is on the public Internet, anyone on the Internet can connect to the port.
```
GatewayPorts clientspecified
```
This means that the client can specify an IP address from which connections to the port are allowed. The syntax for this is:
```
ssh -R 52.194.1.73:8080:localhost:80 host147.aws.example.com
```
In this example, only connections from the IP address 52.194.1.73 to port 8080 are allowed.

OpenSSH also allows the forwarded remote port to specified as 0. In this case, the server will dynamically allocate a port and report it to the client. When used with the -O forward option, the client will print the allocated port number to standard output.
=====>

## Public Key Authentication
<future>
