
# Atelier n°1

schéma logique que niveau 3 (pas de switch, pas de vlan)

**Pour TP1 manip vm1=> Cd**
on a del machines de base puis avec vmware on ouvre la vm enk2019 (celle sans c) et on suit infos puis on y met dans un rep
puis clik droit vm on fait snapshoot, puis click droit vm setting -> option->enable template, puis click droit vm manage-> clone -> depuis snapshot -> linked clone.
On lance le clone et suit étapes (do it later pour licence).
suivre : https://technet365.fr/installation-active-directory-sur-windows-serveur-2019/
  - mettre ip (172.31.1.1 pas passerelle)
  - changer nom controleur domaine en CD
  - On suit technet (nous on met pas ad ds mais accitve directory domaines service)
  - On suit technet (le domaines name : ens.dom)
  
  #penser a créer les 3 sites et les o.u des pc et utilisateur

**FSMO**: Le Maître d'opérations (master operation en anglais) désigne certains types de contrôleurs de domaine dans Active Directory, de Microsoft. La dénomination FSMO signifie Flexible Single Master Operation.
  
 **Pour TP1 manip vm2**
on va ouvrice 2k celle avec C, on va l'importer puis 




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


