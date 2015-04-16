# Autossh commands

## Make a stable tunnel

Suppose you want to make a tunnel to project HOST_B:PORT_B to HOST_A:PORT_A.

![](https://www.lucidchart.com/publicSegments/view/552efd80-bfac-4866-86c4-4fa20a004a17/image.png)

Here is the command:

```
autossh -M 0 -N -R PORT_B:HOST_A:PORT_A root@HOST_B -p SSH_PORT_B -o "ServerAliveInterval 60"
```

You can also connect to users other than root.

## Redirect port on remote server

After you have done this, autossh opened a port on HOST_B, but the access to that was limited to localhost on HOST_B.

So you have to redirect it to another port with public access.

```
apt-get install redir
```

```
redir --laddr=0.0.0.0 --lport=OPEN_PORT_B --cport=PORT_B
```

## Bonus: commands for setting up autossh for sandstorm

On local sandstorm server:

```
autossh -M 0 -N -R 6090:localhost:6080 root@HOST_B -p SSH_PORT_B -o "ServerAliveInterval 60"

autossh -M 0 -N -R 6091:localhost:6081 root@HOST_B -p SSH_PORT_B -o "ServerAliveInterval 60"
```

On remote server:

```
redir --laddr=0.0.0.0 --lport=6080 --cport=6090 &
redir --laddr=0.0.0.0 --lport=6081 --cport=6091 &
```