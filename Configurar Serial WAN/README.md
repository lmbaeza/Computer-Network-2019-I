# Configurar Serial - WAN


### Asignarle Ip al puerto Serial
```python
'Ingresar a la Interfaz Serial0/0/0'
Router(config)#interface Serial 0/0/0

'Asignarle IP'
Router(config-if)#ip address 194.20.10.1 255.255.255.0

'Activar Puerto'
Router(config)#no shutdown
```

### Crear Usuario

```python
Router(config)#username lmbaeza password cisco
```

### Comunicacion WAN entre redes LAN

```python
'Esto indica - Todo lo que no conosco envielo a 194.20.10.1'
'Desde el Router con la interfaz serial 194.20.10.2'
Router(config)#ip route 0.0.0.0 0.0.0.0 194.20.10.1

'Esto indica - Todo lo que no conosco envielo a 194.20.10.2'
'Desde el Router con la interfaz serial 194.20.10.1'
Router(config)#ip route 0.0.0.0 0.0.0.0 194.20.10.2
```