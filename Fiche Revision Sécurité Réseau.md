
--- 

## Sommaire : 


--- 

## Definition 

- **Sécurité des SI** : ensemble de moyens **techniques**, **organisationnels**, **juridiques** et **humains** visant a empecher l'utilisation ou l'acces non autorisé, le mauvais usage, la modification ou le détournement du système d'information



--- 

![[Pasted image 20241028170123.png]]

## Critères D.I.C 

- **Disponibilité** : Propriété d'==accessibilité au moment voulu== des biens par les personnes autorisées
- **Intégrité** : Propriété d'==exactitude et complétude== des biens et informations (détecter une motif illégitime par exemple)
- **Confidentialité** : Propriété des bien de n'==être accessible qu'aux personnes autorisées==

#### Besoin de sécurité : La ==Preuve==

- **Preuve** : Propriété d'un bien permettant de retrouver avec une ==confiance suffisante== sont évolutions : 
	- **Traçabilité** des actions menées
	- **Authentification** des utilisateurs
	- **Imputabilité** des responsable de l'action effectué



- Mécanisme de sécurité pour atteindre les besoins **DICP**

| Service                                     | Information                                                                                                             | D   | I   | C   | P   |
| ------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | --- | --- | --- | --- |
| Anti-Virus                                  | Mécanisme pour détecter des attaques virales déjà identifiés par la communauté sécurité                                 | X   | X   | X   |     |
| Cryptographie                               | Chiffrement et signatures electroniques                                                                                 |     | X   | X   | X   |
| Pare-Feu                                    | Isoler des zones réseaux et autoriser uniquement certains flux                                                          | X   |     | X   |     |
| Contrôle d'accès logiques                   | Restreindres les accès lecture/ecriture/suppression aux personnes habilités                                             |     | X   | X   | X   |
| Sécurité physique des équipements locaux    | Proteger l'intégrité du matériel physique et des batiments/bureaux                                                      | X   | X   | X   |     |
| Capacité d'audit                            | Assurer l'efficacité et la pertinence des mesrures prises pour la sécurité du SI                                        | X   | X   | X   | X   |
| Clauses Contractuelles avec les partenaires | S'assurer que les contractuelles et partenaires ont pris des mesures nécessaires pour ne pas impacter la sécurité du SI | X   | X   | X   | X   |
| Formation / Sensibilisation                 | Expliquer les bonnes pratiques                                                                                          | X   | X   | X   | X   |

1. **Minimisation** : Réduire la surface d'attaque au minimum ( unicité de fonction, une fonction une machine)
2. **Moindre Privilèges** : Donner les droits strictement nécessaire (exemple : Segmentation réseau)
3. **Défense en profondeur** : Authentification, Journalisation centralisé, mécanisme de cloisonnement. En réseau : cloisonnement pour être hébergé sur des services distincts.

![[Pasted image 20241028173038.png]]

4. **Goulot d'étranglement** : Offrir qu'un seul accès depuis et vers l'extérieur car plus simple de contrôler si tout passe par la, modèle Zéro Trust.


![[Pasted image 20241028173301.png]]

5. **Maillon le plus faible** : La solidité d'une architecture correspond au maillon le plus faible. Sécuriser donc tous les aspects du réseau ( Mises a jour de tous les serveurs, ssh inutile si telnet etc)
6. **Interdiction par défaut** : Interdire tout ce qui n'est pas explicitement permis. Refus par defaut
7. **Participation des utilisateurs** : Sensibilisation, bien connaitre les besoins utilisateurs et bien communiquer les raisons des restrictions.

--- 

## Attaques sur les réseaux

![[Pasted image 20241028173914.png]]

Classification des attaques sur le réseau : 


| Passives           | Actives              |
| ------------------ | -------------------- |
| Ecoute             | Mascarade / Spoofing |
| Analyse du traffic | Rejeu                |
|                    | Déni de service      |
|                    | Modification méssage |

-> Ecoute sur les réseaux sans fil nécessite un matériel spécial, et il faut utiliser WPA2 ou WPA3

Les switch ne font pas de diffusion pour un trafic unicast 
-> Pour capturer le traffic : 
	- MAC spoofing
	- ARP spoofing ou ARP cache poisoning ( message ARP falsifié)
	- MAC flooding : transformer le switch en hub

Attaques sur les switch : 
	- CAM Tables Attacks
	- STP Attacks
	- Address Spoofing Attacks
	- VLAN Attacks
	- DHCP Attacks
	- ARP Attacks

Attaques sur le réseau techniques de scan

-> Envoie de paquets SYN : Avantage ne créé jamais de connexion TCP donc peu suspect mais nécessite un privilège root ( Raw Socket)

Spoofing : Interférer avec une session réseau ( vol de session TCP, token php etc)
-> Exemple : Kevin Mittnick


![[Pasted image 20241028174924.png]]

Attaque DOS : 
- Inondation de paquets ; Ping ou SYN
- Attaque sur DNS 
- DDOS ( machine zombie pour attaquer )


APT : 
-> rester dans le système ( Advanced Persistent Threat)

---
## Comment sécuriser un réseau


### Pare-Feu 

- Equipement en coupure entre 2 ou plusieurs réseaux
- Filtrage basé sur des règles 
- Analyse les paquets entrant et sortant d'un réseau a l'autre

###### Règles de filtrage : 
- Couches basses ( réseau et transport)
- Aujourd'hui peut Applicatif aussi 
- Proxy et reverse proxy = pare feu applicatifs dédiés

Sur un pare-feu ==Interdiction par défaut==

2 types de Pare-Feu

![[Pasted image 20241028175500.png]]

Exemple : Paloalto, Fortinet,Pfsense etc

### Load-balancer : 

==Répartit et distribue la charge réseau== donc sur des grosses infrastructures. Permets de mieux se protéger contre le DOS

![[Pasted image 20241028175654.png]]


### Anti-Virus : 
- Logiciel pour détecter des malwares connus
- Base de donnés qui contient les signatures des malwares
- Peut détecter uniquement que des malwares répertoriés

![[Pasted image 20241028175804.png]]

Peut être déployé en local : Post de travail etc
ou 
En coupure des flux réseaux sur un pare-feu par exemple. Semblable a un IDS. Solution EDR (Endpoint Detection & Response)

### IDS et IPS 

Intrusion Détection System
Intrusion Prevention System


-> Détecter les tentatives d'intrusion 

IDS alertent / IPS bloquent

![[Pasted image 20241028180124.png]]

### SIEM  : Security Information and Event Management

Centraliser les Logs, les services etc 

### VPN : Virtual Private Network

VPN est un **réseau virtuel** qui permets a ==deux réseaux distant de communiquer en toute sécurité==

Chiffrement des données = Intégrité -> Tunnel Virtuel


VPN site a site -> IPsec 
VPN entre systemes -> TLS


VPN sans crypto -> appel a des opérateurs MPLS, coeur inaccessible aux clients connecté sur le reseau

--- 

## Protocoles et OSI 

![[Pasted image 20241028180512.png]]

### IPSec 

VPN : PPTP -> session crée avec chaque saut (client fournisseur internet, client passerelle etc)
VPN : L2F -> tunnel crée entre passerelle et fournisseur
VPN : L2TP -> combine les 2

Mode Transport : Protection du trafic IP point a point, peut être implémenté sur tous les équipements

Mode Tunnel : Paquet IP initial encapsulé dans un nouveau paquet protégé. Protège les communications entre deux réseaux ou entre une machine et un réseau.


--- 

### Segmentation 

-> Principe majeur moindre privilège donc appliqué au réseau = ==segmentation==

Droits d'accès a ces zones doivent être filtrés et autoriser que les flux nécessaires

1. 2 réseaux distinct non connecté : Très efficace mais pas pratique en entreprise
2. VLAN : réseaux virtuels implémentés par les switch et gère la communication entre les réseaux selon des règles configurés (peut se faire grâces aux port Ethernet des switch mais aussi des adresses mac des systems)

