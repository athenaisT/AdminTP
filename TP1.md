
# Atelier n°1

Schématiser les différents ordinateurs pour cet exercice et renseigner le nom d’ordinateur avec ses paramètres IP, vous ferez évoluez ce schéma au fil des Ateliers.

Installer une version de Windows Server 2019  Standard dans VMware Workstation dans le VMnet 2

Configurer votre machine avec comme nom CD, avec comme paramètres IP 172.31.X.1/16 qui seras sur le site de Lyon.

Récupérer les Machines de Bases de Windows Server 2019 et Server 2019 Core. Décompressez les bases puis effectuer un clone lié de la Base Server 2019 et un clone lié de la base Server 2019 Core.

Paramétrer vos deux clones pour qu’ils deviennent Serveur Membre du domaine ESN.dom, ils auront comme noms SRV1_M et SRV2C_P

Donner les définitions de : Domaine Active directory, Serveur Autonome, Contrôleur de Domaine, Serveur Membre, Rôles, Fonctionnalités, Groupe de travail, Forêt


notes: schéma logique que niveau 3 (pas de switch, pas de vlan)

**Pour TP1 manip vm1=> Cd (Lyon)**
on a del machines de base puis avec vmware on ouvre la vm enk2019 (celle sans c) et on suit infos puis on y met dans un rep
puis clik droit vm on fait snapshoot, puis click droit vm setting -> option->enable template, puis click droit vm manage-> clone -> depuis snapshot -> linked clone.
On lance le clone et suit étapes (do it later pour licence).
suivre : https://technet365.fr/installation-active-directory-sur-windows-serveur-2019/
  - mettre ip (172.31.1.1 pas passerelle)
  - changer nom controleur domaine en CD
  - On suit technet (nous on met pas ad ds mais accitve directory domaines service)
  - On suit technet (le domaines name : ens.dom)
  - on ajoute site en allant dans en haut droite tools puis active directory sites and services
  - on ajoute ou en allant dans en haut droite tools puis active directory user and computer et on click sur dossier le + a droite en haut (c'est UTILISATEURS, ORDI)
  


**FSMO**: Le Maître d'opérations (master operation en anglais) désigne certains types de contrôleurs de domaine dans Active Directory, de Microsoft. La dénomination FSMO signifie Flexible Single Master Operation.   
Eviter de supprimer les roles il faut d'abors les migré sinon pete tout l'AD. Celui qui a le FSMO n'ai pas forcément le patron mais peut juste etre le garant des modif
  
 **Pour TP1 manip vm2 core (Paris)**
on va ouvrice 2k sans c, on va l'importer puis on met template et snapshot puis on la clone
 - mettre ip (172.31.1.2 pas passerelle)
 


**Pour TP1 manip vm3 (Core enfaite c'est marseille)**
on va ouvrice 2k sans c, on va l'importer puis on met template et snapshot puis on la clone
 - mettre ip (172.31.1.3 passerelle c'est l'adresse de CD)

https://social.technet.microsoft.com/Forums/fr-FR/9a763ad2-246b-4eb2-a840-484a64c591cd/configuration-initiale-de-windows-server-core-2012-r2-contribution-technet-priode-28042014?forum=windowsserver8fr 

faire sconfig pour avoir interface bleu pour + de clik clik ( 8 -> 2 ----->





**pour l'instant no serveurs ne sont que memebre ils vont évoluer au fur et a mesure des tp**


**Domaine Active Directory** : Active Directory répertorie les éléments d'un réseau administré tels que les comptes des utilisateurs, les serveurs, les postes de travail,
les dossiers partagés (en), les imprimantes, etc.

**Serveur Autonome**: les serveurs autonomes comme des serveurs autogérés dont la durabilité dépend du travail volontaire et/ou rémunéré de ceux qui en ont la responsabilité 
lorsqu’ils reçoivent un financement de la communauté des usagers à laquelle ils servent. Leur fonctionnement ne dépend donc pas d’une institution publique ou privée.
Ceci étant, l’autonomie de ces services peut varier, certains acceptent des subventions ou sont logés dans des institutions éducatives alors que d’autres peuvent être cachés 
dans un bureau ou logés dans un centre éducatif ou d’art et n’ont pas besoin d’autant de financement.

**Controleur de domaines**: Un contrôleur de domaine est un serveur qui répond aux demandes d'authentification et contrôle les utilisateurs des réseaux informatiques. 
Le contrôleur de domaine permet donc d'organiser et de sécuriser toutes les données

**Serveur Membre:** Un serveur membre est un serveur  non domain Controller . il peut etre donc config selon les besoins en tant que serveur fichier, impression, web, applicatif, etc.

**Rôles:** Les roles sont utilisé pour gérer l'acces des user finaux aux resources externes.
les roles sont organiser en 4 types:
 - roles professionnel
 - roles informatique
 - applications
 - materiel

**Fonctionnalités:** fonction implanté dens un system informatique permettant a l'utlisateur d'effectuer un traitement

**Groupe de travail:** Dans les réseaux informatiques, un groupe de travail (workgroup en anglais) est un ensemble d'ordinateurs connectés sur un réseau local qui partagent des 
ressources et des responsabilités communes.

**Forêt :** Une forêt représente le niveau d'organisation le plus élevé dans Active Directory.
Chaque forêt comporte une base de données unique, une liste d'adresses mondiales unique et une limite de sécurité. Par défaut, un utilisateur ou administrateur d'une forêt 
donnée n'a pas accès aux autres forêts.
La foret est la racines de l'architecture 

**snapshot :** etat des lieu vm, permet de récup un état de la vm. C'est un fichier de copie.

**OU**: organisation unit

**Site**: est un objet de l'annuaire qui represente le réseau physique de l'entreprise


