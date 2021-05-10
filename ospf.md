# OSPF

## Définir le router-id

``Router(config-router)#router-id 1.1.1.1``

## Activation du protocole de routage OSPF

``Router(config)#router ospf $pid``

## Annoncer un réseau

``Router(config-router)#network $network $mask area $area-number``

## Afficher les voisins

``Router#show ip ospf neighbor``

# Définir la priorité d'une interface

```
Router(config)#interface $interface-name
Router(config-if)#ip ospf priority $priority-number
```



## Définir la route par défaut sur OSPF

Indiquer au router qu'une de ses interfaces va devenir la route par défaut pour l'ensemble de la zone OSPF

Remarque:

default-information originate reste en O au niveau de la table de routage Alors que
redistribute static est en D*EX

```
Router(config)#router ospf 1
Router(config-router)#default-information originate
```

default-information-originate= network 0.0.0.0 0.0.0   reste en 0
redistribute static= injecte toutes les routes statiques  E2* au niveau de la table de routage



redistribute connected subnets

## ajouter une interface à OSPF (ipv6)

```
R1(config)#interface gigabitEthernet 0/0
R1(config-if)#ipv6 ospf 10 area 0
 ```
