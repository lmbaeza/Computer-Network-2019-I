# Configuración de Contraseñas

### Configurar contraseña al modo privilegiado

1. Enable Secret

```python
Switch>enable
Switch#configure terminal
Switch(config)#enable secret ciscosecret
Nota: 'ciscosecret' es la contraseña cifrada

Switch(config)#exit
Switch#show running-config 
(...)
enable secret 5 $1$mERr$wZMkJsj2RVk4hay2C4T32.

Switch#copy running-config startup-config 
Destination filename [startup-config]? 
Building configuration...
[OK]
```
ó
2. Enable Password
```python
Switch>enable
Switch#configure terminal
Switch(config)#enable password cisco
Switch(config)#service password-encryption
Switch(config)#exit
Router#copy running-config startup-config 
Destination filename [startup-config]? 
Building configuration...
[OK]
```

---

*Cuando salgo del modo privilegiado y vuelvo a entrar, me pide contraseña*

```python
Switch#disable
Switch>enable
Password: 
```

### Configurar contraseña de la Consola

```python
Switch>enable
Switch#configure terminal
Switch(config)#line con 0
Switch(config-line)#password ciscoconsole
Nota: 'ciscoconsole' es la contraseña cifrada
Switch(config-line)#exit
Switch(config)#service password-encryption

Switch(config-line)#login
Switch(config-line)#exit

Switch#show running-config 
line con 0
 password 7 0822455D0A1606181C1803082F
 login

Router#copy running-config startup-config 
Destination filename [startup-config]? 
Building configuration...
[OK]
```

### Configurar contraseña en las conexiones remotas (ssh, telnet)

```python
Switch>enable
Switch#configure terminal
Switch(config)#line vty 0 15
Switch(config-line)#password ciscoremote
Nota: 'ciscoremote' es la contraseña cifrada
Switch(config-line)#exit
Switch(config)#service password-encryption

Nota: Si no pones contraseña, no puedes acceder de forma remota

Switch(config-line)#login
Switch(config-line)#exit
Switch(config)#exit

Switch#show running-config 
(...)
line vty 0 4
 password 7 0822455D0A1617121F041801
 login
line vty 5 15
 password 7 0822455D0A1617121F041801
 login

Router#copy running-config startup-config 
Destination filename [startup-config]? 
Building configuration...
[OK]
```

### Configurar contraseña para el usuario

```python
Switch>enable
Switch#configure terminal
Switch(config)#username lmbaeza
Switch(config)#username lmbaeza password cisco
Nota: 'cisco' es la contraseña cifrada
Switch(config)#exit

Switch#sh running-config | include lmbaeza
(...)
username lmbaeza privilege 1 password 7 0822455D0A16
```