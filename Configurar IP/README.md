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

### Configurar IP de FastEthernet HWIC-4ESW en Router

```python
'Ingresar a Modo Vlan'
Router#vlan database

'Crear la vlan 2 con nombre CONTABILIDAD'
Router(vlan)#vlan 2 name CONTABILIDAD

'Entrar a modo de configuración del puerto FastEthernet0/1/0'
Router(config)#interface FastEthernet 0/1/0

'Entrar en modo de Acceso'
Router(config-if)#switchport mode access

'Asignar al puerto FastEthernet0/1/0 en la vlan 2'
Router(config-if)#switchport access vlan 2

'Dejar activado el puerto'
Router(config-if)#no shutdown 

'Ingresar a modo de configuración de la vlan 2'
Router(config)#interface vlan 2

'Asignarle la Ip'
Router(config-if)#ip address 192.168.12.1 255.255.255.0

'Dejar Activada la Interface'
Router(config-if)#no shutdown 

```