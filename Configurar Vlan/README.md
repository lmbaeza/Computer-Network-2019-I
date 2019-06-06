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