# Opérations basiques

## Modification du nom de l'hôte

``Router(config)#hostname R2``

## Désactiver la recherche DNS

``Routeur(config)#no ip domain-lookup``

## Définir le mdp pour le mode privileged

``Routeur(config)# enable password $motdepasse ``

## Définir le mdp chiffré pour le mode privileged

``Routeur(config)# enable secret $motdepasse``

## Chiffrer les mdp du mode privileged et console

``Routeur(config)# service password-encryption`` 

## Définir le mdp pour les connexions via le mode console

```
Router(config)#line con 0
Router(config-line)#password $motdepasse
Router(config-line)#login
```

## Définir le mdp pour les connexions via le mode vty

```
Router(config)#line vty 0 15
Router(config-line)#password $motdepasse
Router(config-line)#login local
```
## Ajouter une route par défaut

``Router(config)# ip route 0.0.0.0 0.0.0.0 serial 0/0/0``

## Configurer la bannière

```
R1(config)#banner motd $char-final
Authorized users only, violaters will be shot on sight! $char-final
```

## Configurer un timeout de 15 min pour l'exec mode

````
Router(config)#line vty 0 15
Router(config-line)#exec-timeout 15 0
````
## Ajouter une interface passive

Les interfaces dites “passives” sont celles qui n’envoient aucun message d’un protocole de routage

``Router(config-router)# passive-interface $interface-name``


## Synchroniser le flux d'erreur et autres sorties par défaut (pour ne pas bousiller le terminal avec des commandes debug alors que l'on tape une commande)


````
Router(config)#line con 0
Router(config-line)#logging synchronous
````



# Activer IPV6

Il est nécessaire d'activer le routage ipv6 unicast-routing pour activer le routage ipv6 via un protocole de routage

ROUTER(config)#ipv6 unicast-routing
