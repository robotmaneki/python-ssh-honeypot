# Python SSH Honeypot

Forked from 
https://securehoney.net/blog/how-to-build-an-ssh-honeypot-in-python-and-docker-part-1.html
https://github.com/sjbell/basic_ssh_honeypot


Uses the [Paramiko](https://github.com/paramiko/paramiko) Python SSH protocol library.

# Installation

## Port forwarding
Setup port forwarding (e.g. from 22 to 2222)

```
iptables -A PREROUTING -t nat -p tcp --dport 22 -j REDIRECT --to-port 2222
```

## Generate server key
```
ssh-keygen -t rsa -f server.key
```
## Build
```
docker build -t basic_honeypot .
```
## Run
```
docker run -v ${PWD}:/usr/src/app -p 2222:2222 basic_honeypot
```
Logs are recorded in the auto-generated ```ssh_honeypot.log``` file
