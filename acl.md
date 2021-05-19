ACL

ACL étendu= au plus proche de la source du trafic à bloquer
ACL standard = au plus proche de la destination du trafic à bloquer

## créer une acl
R2(config)#access-list 10 remark ACL_TO_PINK_LAN

## ajouter uen règle pour un hôte

R2(config)#access-list 10 permit host 192.168.2.50

## ajouter une règle pour un réseau

R2(config)#access-list 10 permit 172.16.1.0 0.0.0.25

## appliquer une ACL sur une interface 

R2(config)#interface gigabitEthernet 0/1
R2(config-if)#ip access-group 10 out

## créer une ACL nommée
R2(config)#ip access-list standard ADMIN_VTY

# ajouter une règle ACL nommée
R1(config-std-nacl)#access-list ADMIN_VTY host 192.168.2.50

# ajouter une règle ACL nommée VTY
R1(config-line)#access-class ADMIN_VTY in

# ajouter une ACL étendue numérotée 
R1(config)#access-list 100 permit tcp 172.22.34.64 0.0.0.31 host 172.22.34.62 eq ftp

# ajouter une ACL étendu nommée
R1(config)# ip access-list extended HTTP_ONLY

# ajouter une ACL étendu numérotée
R1(config)# ip access-list extended HTTP_ONLY

# ajouter une ACL ipv6 (forcément une ACL étendue nommée)
R1(config)#ipv6 access-list BLOCK_HTTP

# appliquer une ACL ipv6
R1(config-if)# ipv6 traffic-filter BLOCK_HTTP in