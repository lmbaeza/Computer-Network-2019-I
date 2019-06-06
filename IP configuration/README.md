# Comandos de configuración desde la Terminal

### Configuración de la IP de un Switch

```python
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

```python
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