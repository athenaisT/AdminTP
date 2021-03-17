# Atelier n °1

recuperation vm jeremy

dans mdt01, on va dans server manager-> dans wds -> click droit -> deploiement (seul truc pas next standalone) -> selectionner l'image dans dvd drive (mis à la douille avec le usb)

il faut dans vmnet enlever le dhcp de vmware mis de base

sur pc physique prendre 1 iso (windoms 10) le copier sur bureau (pas ouf mais bon) 

**MDT** est une collection unifiée d’outils, de processus et d’instructions pour l’automatisation du déploiement de bureau et serveur. Vous pouvez l’utiliser pour créer des images de référence ou comme solution de déploiement complète. MDT est l’un des outils les plus importants disponibles aujourd’hui pour les professionnels de l’informatique.

**wds**Les Services de déploiement Windows ("Windows Deployment Services" ou WDS) sont une technologie de Microsoft permettant d'installer un système d'exploitation Windows via le réseau. Ils succèdent aux services d'installation à distance ("Remote Installation services" ou RIS) et sont apparus dans le Service Pack 2 de Windows Server 2003 et Windows Vista. 
=> on met des images sur ce serveur, permet de deplloyer des images via le réseau donc on permet d'installer des images sur ordi (attention il faut les allumer en meme temps)

**PXE** (sigle de Pre-boot eXecution Environment) permet à une station de travail de démarrer depuis le réseau en récupérant une image de système d'exploitation qui se trouve sur un serveur.
L'image ainsi récupérée peut être le système d'exploitation brut ou bien le système d'exploitation personnalisé avec des composantes logicielles (suite bureautique, utilitaires, packs de sécurité, scripts, etc.).
Une fois cette image « pré-chargée », elle peut éventuellement, en fonction des paramétrages passés à cette image sur le serveur, être installée sur la machine qui a été amorcée en PXE.

# Atelier 2

dans power sheel pc physique : Install-module –name OSDBuilder –scope CurrentUser -force


osbbuilder -> osbimport-> sources ou os pour trouvers boot ou install.


winPe ne fait pas instalation il propser des image à installer


DORA : discover, Offer , request, acknolegde (communication dhcp)

regarder la video de bezet pour installer winpe.



# Atelier 3

https://rdr-it.com/deployer-windows-avec-mdt-et-wds/4/

quand fait le truc a vec iso mettre dans setting de SATA , l'iso windows bussiness

pour installer cisko packet pas en exe on fait une installation silencieuse : https://silentinstallhq.com/cisco-packet-tracer-silent-install-how-to-guide/


**séquence de tâche:** Une séquence de tâche dans MDT contient l’ensemble des actions qui vont être effectuées sur le poste durant le déploiement.

mdt -> image systeme explotation 
Le MDT est en fait une console graphique (de type MMC) dont l’objectif est de fédérer des sources, réaliser l’assemblage et proposer des séquences de taches pour piloter le tout…

wds -> image de bootage
 En utilisant WDS vous aurez l’avantage de ne pas être limité par le support (disques du serveur), mais l'inconvénient du transport de fichiers volumineux (bande passante du réseau).
Le premier intérêt de WDS est d’offrir une "dématérialisation" des DVD de distribution afin de les centraliser sur un serveur et fournir par la même occasion un système d’amorçage via le réseau PXE.

=> quand browser : c-> deployementhare->boot-> prendre la 64


=> mdt et wds sont complémentaire c'est wds qui va cherecher les images et mdt va config les images

les scénario sont les task sequences

# Atelier 4

=> https://www.it-connect.fr/overview-mdt-wds-winpe/

BOOSTRAP.INI => sécu merdique + son role : donne des info à loa machine pour se co au partage de déploiement (donc des que modif on doit mettre à jour tout le lignt et wwds)
customsettings.ini => Régles : permet de parametre le deploiement en fonction de l'emplacement (ex langue , fuseau horaire..) 
https://les2t.fr/mdt-customsettings-ini-et-bootstrap-ini/ 

**CustomSettings.ini** : Fichier de configuration principal pour les règles de traitement utilisées dans tous les scénarios. Le fichier reste dans le dossier de déploiement.
**BootStrap.ini** : Fichier de configuration utilisé lorsque l’ordinateur cible n’est pas en mesure de se connecter au point de déploiement approprié. Cette situation survient dans un scénario de nouvel ordinateur et pour l’ordinateur de remplacement d’un scénario de remplacement d’ordinateur. Le fichier BootStrap.ini est intégré dans l’image de boot
=> boostrap agit en 1er, mieux de modif custom car sinon doit tout mettre à jour
=> si bootstrap pas bon peut baiser image

modification du boostarp et config sur teams


on update deployement share : quand on modif boostrap, quand on veut faire des modif sur le boot

https://numerique.univ-reims.fr/index.php?eID=dumpFile&t=f&f=2157&token=d717d00675f9aee16e5c3fb1bce09ed7fc78d98a
http://winux.overblog.com/2014/08/creation-d-un-master-avec-mdt.html



manque des truc sir le dc à config, on doit créer une vm pour faire capture, donc on va lancer cette vm on va choisirr iso + les appli(task séquances) puis on fait uune capture
et on va l'utiliser comme image de boot ==> Master 
le master est en faite une image fait avec une capture d'image ou on avit déjà 2 aplli et on fait une task sur la capture pour avoir lse 3 autres appli.
penser à lancer en silicieux les applis => c'est pour installer sans display user (il voit pas l'installation)

suivit de VM louis car ça marche pas chez nous

on peut faire des deployment type compta que pour deployer ordi config pour compta etc ( en fonction de l'adresse mac etguid de l'ordi on le reconait comme ordi compta donc deployment compta)

**sql express** MDT peut utiliser SQL Server Express ou un SQL Server existant. Cependant, étant donné que le déploiement de base de données n’est pas volumineux, même dans les environnements d’entreprise, nous recommandons l’utilisation de la base de données gratuite SQL Server2012 SP1 Express dans votre environnement.


**lite-touch** Le déploiement LTI peut être réalisé avec ou quasiment sans assistance humaine mais dans la pratique, le Lite Touch est semi-automatisé chez la plupart des clients. Il est cependant réalisable d'automatiser entièrement (hormis le démarrage de la machine) un déploiement LTI avec MDT

penser à bien mettre les droit de connexion

# Atelier 5

https://docs.microsoft.com/fr-fr/windows/deployment/deploy-windows-mdt/use-the-mdt-database-to-stage-windows-10-deployment-information



pour tester on prend l'adresse mac de 2vm puis on fait task pour 2 sur une puis 3 sur l'autres


