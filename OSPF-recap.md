# OSPF

## Activation du protocole de routage OSPF

``Router(config)#router ospf $pid``

## Annoncer un réseau

``Router(config-router)#network $network $mask area $area-number``

## Afficher les voisins

``Router#show ip ospf neighbor``
