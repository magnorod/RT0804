# ACL

ACL étendu= au plus proche de la source

ACL standard = au plus proche de la destination

<!> il faut toujours utiliser le masque inverse et pas le masque réseau classique <!>

OK

```
access-list 101 deny tcp any host 192.168.1.70 eq ftp
access-list 101 deny icmp any 192.168.1.0 0.0.0.63
access-list 101 permit ip any any
```

Ce qui donne : 

```
Extended IP access list 101
    10 deny tcp any host 192.168.1.70 eq ftp
    20 deny icmp any 192.168.1.0 0.0.0.63
    30 permit ip any any
```
KO car le résultat est différent (cisco ne traduit pas automatiquement)

```
access-list 101 deny tcp any host 192.168.1.70 eq ftp
access-list 101 deny icmp any 192.168.1.0 255.255.255.192
access-list 101 permit ip any any
```
Ce qui donne:

```
Extended IP access list 101
    10 deny tcp any host 192.168.1.70 eq ftp
    20 deny icmp any 0.0.0.0 255.255.255.192
    30 permit ip any any
```

## créer une acl numérotée avec une remarque
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
