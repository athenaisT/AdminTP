# Atelier 1

suivre diapo 

vsca :Depuis la version 5.0 de vSphere, vCenter est disponible sous forme d'appliance virtuelle pré-configurée, fonctionnant sur une distribution Linux SUSE. Cette appliance se nomme vCSA (vCenter Server Appliance), vCenter Server Appliance est une machine virtuelle Linux préconfigurée et optimisée pour l'exécution de VMware vCenter Server® et des services associés sur Linux.


On est sur vlan 30
cable love (prononcer lover) c'est l'enroulement

cable: </br>
Athé : 6 </br>
Louis : 7 </br>
Claire: 10  </br>
Axel : 9  </br>
Jérémy: 8  </br>

**vNIC**:Carte réseau virtuelle 

fair un virtual réseau seul axel à dhcp => on va se co à se réseau ensuite avec les vm pour tous etre sur le meme réseau

suivre video diapo pour faire DNS => (faire par axel , fonctionnel)

**VMware ESXi** est un hyperviseur de type 1 indépendant des systèmes d'exploitation. Il repose lui-même sur le système d'exploitation VMkernel qui assure l'interface avec les agents dont il soutient l'exécution. ESXi est l'hyperviseur exclusif des licences VMware vSphere 5.x.


**vmcenter** :VMware vCenter Server est un logiciel de gestion de serveurs avancée qui vous offre une plate-forme centralisée pour le contrôle de vos environnements VMware vSphere et vous permet d'automatiser et de fournir une infrastructure virtuelle dans l'ensemble du Cloud hybride en toute confiance.

**vSphere**:  est la plateforme de virtualisation de serveurs de VMware

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
=> nas serveur de stockage mais peut etre un pc etc.. alors que san il y a du materiel dedier  
=> san les systeme fichier voient les baies de stockage comme leur disk dur mais ne voient que ceux qui leurs sont attribuer alors que nas ils voient tout

=> san disk dur et nas un dossier partager

pour faire le datastorage on va sur l'addressse ip (la ou ya vmware log+mdp)


**Fibre Channel FCoE** : (Fibre Channel over Ethernet) est un protocole qui encapsule les trames Fibre Channel, provenant d'un réseau de stockage SAN, sur un réseau Ethernet1
Fibre Channel permet le raccordement avec son système de stockage par de la Fibre, tandis que l’iSCSI est encapsulé sur un réseau Ethernet standard
son intérêt : réfractaires au départ, tous les constructeurs de stockage ont finalement intégré l’iSCSI à leur catalogue. </br>

 **iSCSI**:(Internet Small Computer System Interface). C'est un protocole de stockage en réseau basé sur le protocole IP destiné à relier les installations de stockage de données.
 
**Type de fichier ZFS**: un système de fichiers open source sous licence CDDL. Les caractéristiques de ce système de fichiers sont sa très haute capacité de stockage, l'intégration de tous les concepts précédents concernant les systèmes de fichiers et la gestion de volume.
 
 **OpenZFS** :t un projet visant à rendre ZFS plus largement utilisé et développé de manière open source.
 
 **Un ZVOL**:  est un périphérique bloc ZFS qui réside dans votre pool de stockage
 https://pthree.org/2012/12/21/zfs-administration-part-xiv-zvols/
 
 **ova**(Open Virtual Appliance). Open Virtualization Format (OVF) est un format de fichier qui prend en charge l'échange de dispositifs virtuels entre les produits et les plate-formes. OVA est une distribution de fichier unique du même module de fichier
 
 -------------------
 théorique ( bezzt cours distance + video bezzet)
 
**vCenter**:permet de gérer exsi de maniere centralisé, on peut faire plus de chose pour gérer les vm avec, les vm sont représenter que par des fichier et donc peuvent etre migré
**exsi**: communique sur le port 443 avec vcenter, il est piloter via un agent telecharger quand on va relier vcenter et lui 
 **Un LUN** (Logical Unit Number) désigne, dans le domaine du stockage informatique, le numéro d'unité logique d'un équipement SCSI
 **drs** une fonctionnalité qui permet d'equilibré la charge cpuram (gpu et ?), ne marche que avec vcenter 
 **cluster**: y'a une banque de pulsastion qui dit si y' a des exsi libre ou non
**vpxa** c'est un agent qui va etre active quand joint a un vcenter et va piloter cet agent
**ha** permet de voir la haute disponiblité des exsi , il les redemarre et les bascule pas, disponiblité des serveur et pas des machines! 



a regarder :
Vcenter,
HA, 
DRS, 
Vmotion 
Storage 
VMotion
LUN 
DATAStore 
Agents 
Dossiers 
Autorisations 
Raid 
type de provisionnements
déduplication, 
iscsi
taget

spher6 -admin et exploit
    0.2VM=> 0.1-les composant machines virtuel ( on en est a la version 17), 02(celle qui suit 0.1), 0.4 diff etat vm
 1. 0.3HA=> 6 premiere
 2. 


-----

type 1 : dépent pas d'un os gere lui meme
type 2 : depend os

 
 
 ncréation isci: - faire pool (ensemble de disk),  raid 5 (5 disk au min et on peut en perdre 1), raid z
       - ZVol (donc on affect un volume apelle lun)
       - on va config le portail (on va sur TrueNAs le truc ou on va config) on va dans portail et on met 0.0.0.0 pour ip addresse c'est pour dire j'accepte toutes les requete de tout le monde (port 3260 de base) portail ouverture du truenas sur le réseau
       - iniator c'est qui qui va se co sur mon truenas
       - iqn=>id des esxi
       - targets : c'est qu'est ce que va voir l'initair qui va se co (la ou on va mettre le nom lun)
       - extents => c'est quel volume on va utliser, xen c'est un hyperviseur existant, jamais mettre read-only
       - associated targer => on prend target (portail+initiator) + extents
       - puis on va dans service et on le fait running
       - il faut ensuite y lié au exsi, on se co sur un esxi (192.168.30.85),adpataters=> softaware dynamic target on rentre ip du true nas+port
       - dans device on voit truenas pour verif (il est vue comme les autres disk)
       - refaire la partie liason exsi et la ils on un stockage commun

vSphere: - on ajoute un datacenter (organistaion comme une ou)
         - on crer un new datasrore et selectionner le Lun
         - crer cluster et on va sur les exsi ajouter
         - on va créer nos vm sur nos serveur
vmotion => depalcer vm à chaus (pas besoin de l'éteindre) d'un exsi vers un autre

=> grace au drs , quand on lance vm c'est lui qui choisis sur quel serveur la lancer et faire la répartition
=> utlis car si un serveur tombe les vm peut etre deplacer dans l'immédiat
              
 cluster : plein de serveur qui travaille ensemble comme un super serveur
 
 fqdn: (fauly qualifed domain name) => son nom (serveur)+ son nom domaine + extension de domaine
 
 cpu over-comminent: sucharge de la repartition des coueurs
 DPM => optimisation de la conso des esxi
 vCls => machine de base obligatoir
 content laibraies : emplacement de stockage  avec (iso + ovf /ova)
 
 c/windows/32/sysprep
sysprep => capture  et master image de base

ha !=**La tolérance aux pannes** est l'aptitude d'un système informatique à demeurer fonctionnel malgré certaines pannes de ses constituants.
