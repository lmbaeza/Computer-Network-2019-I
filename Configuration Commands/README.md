# Comandos de configuración desde la Terminal

### Configuración de la IP de un Switch

```sql
Switch>enable
Switch#configure terminal
Switch(config)#interface vlan1
Switch(config-if)#ip address 192.168.1.2 255.255.255.0
Switch(config-if)#no shutdown
Switch(config-if)#exit
Switch(config)#exit
Switch#copy running-config startup-config 
Destination filename [startup-config]? 
Building configuration...
[OK]
```

### Configuración de la IP de la inteface de un Router

```c
Router>enable
Router#configure terminal
Router(config)#interface FastEthernet 0/0
Router(config-if)#ip address 192.168.1.1 255.255.255.0
Router(config-if)#no shutdown
Router(config-if)#exit
Router(config)#exit
Router#copy running-config startup-config 
Destination filename [startup-config]? 
Building configuration...
[OK]
```

### Configurar contraseña al modo privilegiado

1. Enable Secret

```swift
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

```markdown
Switch#disable
Switch>enable
Password: 
```

### Configurar contraseña de la Consola

```
Switch>enable
Switch#configure terminal
Switch(config)#line con 0
Switch(config-line)#password ciscoconsole
Nota: 'ciscoconsole' es la contraseña cifrada

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

```
Switch>enable
Switch#configure terminal
Switch(config)#line vty 0 15
Switch(config-line)#password ciscoremote
Nota: 'ciscoremote' es la contraseña cifrada

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

```
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