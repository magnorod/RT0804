# OSPF

## Définir le router-id

``Router(config-router)#router-id 1.1.1.1``

## Activation du protocole de routage OSPF

``Router(config)#router ospf $pid``

## Annoncer un réseau

``Router(config-router)#network $network $mask area $area-number``

## Afficher les voisins

``Router#show ip ospf neighbor``

## Définir la priorité d'une interface

```
Router(config)#interface $interface-name
Router(config-if)#ip ospf priority $priority-number
```

## Ajouter une interface passive

Les interfaces dites “passives” sont celles qui n’envoient aucun message d’un protocole de routage comme OSPF

``Router(config-router)# passive-interface $interface-name``

## Définir la route par défaut sur OSPF

Indiquer au router qu'une de ses interfaces va devenir la route par défaut pour l'ensemble de la zone OSPF

```
Router(config)#router ospf 1
Router(config-router)#default-information originate
```
