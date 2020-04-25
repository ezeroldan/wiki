# SSH

## Introduccion
SSH es el cliente - ssh_config
SSHD es el servidor donde uno se conecta - sshd_config

## Public/Private Key Pair
`ssh-keygen` Generar claves  
`~/.ssh/id_rsa` Private Key  
`~/.ssh/id_rsa.pub` Public Key  
`authorized_keys` Donde se almacenan las public keys en el server  

## Comandos
`ssh user@host` Conectar al host  
`ssh -p port user@host` Se conecta mediante el puerto  
`ssh -D port user@host` Conecta y usa bind port  


## cPanel
> SECURITY > SSH Access

## SSH Port Forwarding

```BASH
ssh -g -L2001:HostD:143 user1@HostB
```

