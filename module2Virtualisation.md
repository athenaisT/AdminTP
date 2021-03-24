# Atelier 1

suivre diapo 

vsca :Depuis la version 5.0 de vSphere, vCenter est disponible sous forme d'appliance virtuelle pré-configurée, fonctionnant sur une distribution Linux SUSE. Cette appliance se nomme vCSA (vCenter Server Appliance), vCenter Server Appliance est une machine virtuelle Linux préconfigurée et optimisée pour l'exécution de VMware vCenter Server® et des services associés sur Linux.


On est sur vlan 30
cable love (prononcer lover) c'est l'enroulement

cable:
Athé : 6 
Louis : 7
Claire: 10
Axel : 9
Jérémy: 8

**vNIC**:Carte réseau virtuelle 

fair un virtual réseau seul axel à dhcp => on va se co à se réseau ensuite avec les vm pour tous etre sur le meme réseau

suivre video diapo pour faire DNS => (faire par axel , fonctionnel)

**VMware ESXi** est un hyperviseur de type 1 indépendant des systèmes d'exploitation. Il repose lui-même sur le système d'exploitation VMkernel qui assure l'interface avec les agents dont il soutient l'exécution. ESXi est l'hyperviseur exclusif des licences VMware vSphere 5.x.


**vmcenter** :VMware vCenter Server est un logiciel de gestion de serveurs avancée qui vous offre une plate-forme centralisée pour le contrôle de vos environnements VMware vSphere et vous permet d'automatiser et de fournir une infrastructure virtuelle dans l'ensemble du Cloud hybride en toute confiance.

V?zqre11(dernier 1 en maj)

la net1 => .85
la net =>.86

il faut faut mettre sur les vm sur le network du dns puis on met sur la bonne carte et on met vmnet2
puis on met une adresse fixe à ethernet3 (.13)
et on se met sur la page 192.168.30.85 ou 86

notre dns va etre notre routeur
finalement on a fait un vyos

pour le vmcenter mettre le port derrier l'addresse ip sinon marche pas

truNAs => mdp : 123+qwe

le dhcp donne une addresse pour l' eternet du pc physique


**Un hyperviseur** : également appelé moniteur de machine virtuelle, est un processus qui crée et exécute des machines virtuelles (VM). Il permet à un ordinateur hôte de prendre en charge plusieurs VM clientes en partageant virtuellement ses ressources, telles que la mémoire et la capacité de traitement.
=> outils de virtualisation

**Définition d'un Hyperviseur :**
Si on souhaite définir un hyperviseur, on peut dire qu'il s'agit d'un outil de virtualisation qui permet à plusieurs systèmes d'exploitation (OS) de fonctionner simultanément sur une même machine physique.

Théoriquement, c'est une couche logicielle très légère (en comparaison à un OS classique) qui permet d'allouer un maximum de ressources physiques aux machines virtuelles.


Le **SAN**( Un réseau de zone de stockage) permet de présenter du stockage à des serveurs via un réseau dédié. </br>
Le **NAS** permet quand à lui de disposer d'un système de fichiers accessible depuis n'importe quel appareil équipé d'un protocole compatible.
=> san coute chere et le nas lui c'est un peu fait une place dans les familles 
=> nas serveur de stockage mais peut etre un pc etc..   
=> san les systeme fichier voient les baies de stockage comme leur disk dur mais ne voient que ceux qui leurs sont attribuer alors que nas ils voient tout

pour faire le datastorage on va sur l'addressse ip (la ou ya vmware log+mdp)




