# Truck Multiples Vlans hacia un Router

![Truck Multiples Vlans hacia un Router](https://i.ibb.co/QNK5mKD/Truck.png)

**Nota:** _Asignar IPs a los Computadores_

### Crear Vlans

**Ingenieria:** _Vlan 2_
```python
Switch#configure terminal 
Switch(config)#vlan 2
Switch(config-vlan)#name INGENIERIA
Switch(config-vlan)#exit
```

**Economia:** _Vlan 3_
```python
Switch(config)#vlan 3
Switch(config-vlan)#name ECONOMIA
Switch(config-vlan)#exit
```

### Asignar los Puertos a las Vlans

**Fa0/1:** _Vlan 2 Ingenieria_
```python
Switch(config)#interface FastEthernet 0/1
Switch(config-if)#switchport mode access
Switch(config-if)#switchport access vlan 2
Switch(config-if)#no shutdown 
```


**Fa0/1:** _Vlan 3 Economia_
```python
Switch(config)#interface FastEthernet 0/2
Switch(config-if)#switchport mode access
Switch(config-if)#switchport access vlan 3
Switch(config-if)#no shutdown 
```

### Truncar el Puerto de Switch al Router

**Switch Fa0/24:** _Puerto Truncado_

```python
Switch(config)#interface FastEthernet 0/24
Switch(config-if)#switchport mode trunk 
Switch(config-if)#exit
```

### No ponerle IP a la Interfaz del Router

**Router Fa0/0:**

```python
Router(config)#interface FastEthernet 0/0
Router(config-if)#no ip address 
Router(config-if)#no shutdown 
Router(config-if)#exit
```

### Ponerle IP a la Vlan 2 Ingenieria desde el Router

```python
Router(config)#interface FastEthernet 0/0.2
Router(config-subif)#encapsulation dot1Q 2
Router(config-subif)#ip address 192.168.10.1 255.255.255.0
Router(config-subif)#no shutdown 
Router(config-subif)#exit
```

### Ponerle IP a la Vlan 3 Economia desde el Router

```python
Router(config)#interface FastEthernet 0/0.3
Router(config-subif)#encapsulation dot1Q 3
Router(config-subif)#ip address 192.168.20.1 255.255.255.0
Router(config-subif)#no shutdown 
Router(config-subif)#exit 
```
