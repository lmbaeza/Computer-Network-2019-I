# Configurar Vlan - Switch

## Mostrar las Vlan

```python
'Mostrar todas las vlan'
Switch#show vlan 
```

## Crear una Vlan - Switch

```python
'Entrar en modo de configuración'
Switch#configure terminal 

'Crear la vlan 2'
Switch(config)#vlan 2

'Asignarle un nombre a la Vlan'
Switch(config-vlan)#name NOMINA
```
---

## Asignarle un puerto a una Vlan

```python
'Entra al modo de configuración de interface'
Switch(config)#interface FastEthernet 0/1

'Configura la interface en el modo access'
Switch(config-if)#switchport mode access

'Asigna la interface a la VLAN 2'
Switch(config-if)#switchport access vlan 2

'Inicializa la interface de switch'
Switch(config-if)#no shutdown
```

## Asignarle una IP a una Vlan

```python
'Ingresar a la Interface Vlan 3'
Switch(config)#interface vlan 3

'Asignarle IP a la Vlan - Switch'
Switch(config-if)#ip address 192.168.11.2 255.255.255.0

'Activar la IP'
Switch(config-if)#no shutdown
```

## Borrar una Vlan

```python
'Borra la VLAN 2'
Switch(config)#no vlan 2

'Si quieres borrar todas las VLANs creados en un Cisco Switch solo debes de borrar el archivo vlan.dat almacenado en la memoria flash del Swtich.'
Switch#delete flash:vlan.dat
```