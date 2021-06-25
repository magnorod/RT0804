# Nat statique
```
(config) ip nat inside source static 192.168.10.254 209.165.201.5
(config) interface serial 0/1/0
(config-if) ip address 192.168.1.2 255.255.255.252
(config-if) ip nat inside
(config-if) exit
(config) interface serial 0/1/1
(config-if) ip address 209.165.201.5 255.255.255.252
(config-if) ip nat outside
```
# Vérifier NAT statique
```
r2#clear ip nat statistics *
r2#show ip nat statistics
```

# Nat dynamique
```
r2(config)#ip nat pool NAT-POOL1 209.165.200.226 209.165.200.240 netmask 255.255.255.224
r2(config)#access-list 1 permit 192.168.0.0 0.0.255.255
r2(config)#ip nat inside source list 1 pool NAT-POOL1
r2(config)#interface serial 0/1/0
r2(config-if)#ip nat inside
r2(config)#interface serial 0/1/1
r2(config-if)#ip nat outside
```
# Vérifier NAT dynamique
```
r2#show ip nat translations *
r2#show ip nat translations
```
# Vérifier NAT dynamique (méthode 2)
```
r2#show running-config | include NAT
```
# Configurer PAT pour une adresse IPV4 unique
Toutes les adresses 192.168.0.0/16 qui envoient du trafic via le routeur R2 sur internet
sont traduites en adresse IPV4 209.165.200.225 (adresse ip de l'interface serial0/1/1)
```
R2(config)# ip nat inside source list 1 interface serial 0/1/0 overload
R2(config)# access-list 1 permit 192.168.0.0 0.0.255.255
R2 (config) # interface serial0/1/0
R2(config-if)# ip nat inside
R2(config-if)# exit
R2 (config) # interface Serial0/1/1
R2(config-if)# ip nat outside
```
# Configurer PAT pour une pool d'adresses
Ici 2 adresses 
```
R2(config)# ip nat pool NAT-POOL2 209.165.200.226 209.165.200.240 netmask 255.255.255.224
R2(config)# access-list 1 permit 192.168.0.0 0.0.255.255
R2(config)# ip nat inside source list 1 pool NAT-POOL2 overload
R2(config)# interface serial0/1/0
R2(config-if)# ip nat inside
R2(config-if)# interface serial0/1/0
R2(config-if)# ip nat outside
```
# Vérifier PAT
ici les machines sont différenciées avec leurs numéros de ports
```
R2# show ip nat translations
```
