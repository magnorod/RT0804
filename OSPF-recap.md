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
