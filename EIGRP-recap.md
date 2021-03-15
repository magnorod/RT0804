# EIGRP
 
## Activer le routage eigrp

$autonomous-system doit être identique sur chaque routeur (équivalent zone)

``R2(config)#router eigrp $autonomous-system ``

## Annoncer un réseau

``R2(config-router)#network $reseau ``

## Annoncer un sous réseau

``R2(config-router)#network $reseau $wildcard-mask``

ou avec un calcul automatique du wilcard-mask via le netmask

``R2(config-router)#network $reseau $netmask``

## Afficher les routes

``R2#show ip route``

## Afficher le protocole de routage utilisé, numéro de système autonome et les réseau, adresses IP des voisins

``R2#show ip protocols``

## Afficher les voisins

``R2#show ip eigrp neighbors``

## Afficher la topologie

``R2#show ip eigrp topology``

## Modifier le clock rate d'une interface série

à effectuer uniquement sur le coté DCE d'une liaison série (coté DCT ignoré)

### clock rate standard:
1200, 2400, 4800, 9600, 19200, 38400, 56000, 64000


```
R2(config)# interface $interface-name
R2(config-if)# clock rate $clock-rate
```

## Modifier la bande passante

$bandwith-value in kilobits

n'affecte pas la bande passante physique (uniquement pour le routage)

``R2(config-if)#bandwidth $bandwith-value``

## Désactivation de l'agrégation de routes automatique 

``R2(config-router)#no auto-summary``

## Agrégation de routes manuel

exemple avec les réseaux de base:
192.168.1.0/24, 192.168.2.0/24 et 192.168.3.0/24

```
R2(config)#interface $serial-interface
R2(config-if)#ip summary-address eigrp $autonomous-system 192.168.0.0 255.255.252.0
```

## Ajouter des adresses de bouclage (émulation de réseau)

```
R2(config)#interface $loopback-interface
R2(config-if)#ip address $ip $netmask 
```

## Injecter les routes statiques dans EIGRP
metric = bandwith delay reliability load MTU

````
Router(config)#router eigrp $autonomous-system
Router(config-router)#redistribute static metric 10000 100 255 1 1500
````
