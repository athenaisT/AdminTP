# Atelier n° 6

**Quel rôle pour des outils d’administration, pourquoi travailler avec le minimum de droits nécessaire et exécuter les tâches d’administration en utilisant la fonction Exécuter
en tant que**

Les outils RSAT permettent aux administrateurs informatiques de gérer les rôles et les fonctionnalités de Windows Server à partir d’un PC Windows 10.
Les Outils d’administration de serveur distant comprennent le Gestionnaire de serveur, des composants logiciels enfichables MMC (Microsoft Management Console), des consoles, 
des fournisseurs et des applets de commande Windows PowerShell, ainsi que des outils en ligne de commande pour la gestion des rôles et des fonctionnalités exécutés sur
Windows Server.
Les Outils d’administration de serveur distant incluent des modules d’applet de commande Windows PowerShell qui peuvent être utilisés pour gérer des rôles et des fonctionnalités 
s’exécutant sur des serveurs distants.

c'est pour controler les taches que peuvent faire les user pour éviter qu'ils cassent ailleurs mais qu'ils puissent réaliser certaines taches possible que en admin.


**Quelle est l’utilité des consoles MMC**

Microsoft Management Console (abr. MMC) est un gestionnaire de console virtuelle incorporé dans Microsoft Windows, qui sert de conteneur pour des interfaces graphiques 
de configuration. Ce logiciel utilitaire est à la base de nombreux outils de configuration incorporés dans Windows, et permet de créer des outils d'administration système 
en regroupant un lot d'extensions dans une même fenêtre1.

**Pour une sécurité accrue au sein de votre entreprise renommer le compte administrateur du domaine.**
on fait rename sur user administrator penser a changer account aussi.

**Créer un autre compte pour l’administrateur n’ayant pas les droits d’administration, il devra dorénavant utiliser ce compte pour se connecter au domaine et effectuer l’administration du domaine à l’aide de la commande  Exécuter en tant que avec le compte ayant les droits sur le domaine.**
on créer un nouveau group ou on add amin et admini le new user. puis properties attribute j'ai mis dans admincount :2 (jsp si juste)
penser a ajouter g-admin dans gpo du remove le run menue (delegation deny group machin).
admini c'est le compte du l'autre admin. creer gpo la ou ya vait run menue y ' a un truc show run as different user.

on va dans cd on va dans all server et on add le serveur memebre, puis clique droit dessus add roles et features on next les 3 premier puis on coche ad domain et services et on next jusqu'à install. puis sur mozilla on tappe SAD.ens.dom pui on ajoute cd. puis dans le dasboard on fait add other server et add tous

**Créer une console MMC ou application WPF  personnalisé afin que les responsables puissent créer des utilisateurs dans leur service ainsi que la possibilité de réinitialiser les mots de passes des membres de son service.**
dans un serveur memebre ici lyon1
windomws+r puis mmc.exe puis file -> new add/snappin puis on add le 3e avec ad user puis on va dans sites->LYON-> COMPTA ET ON FAIT NEW WIDOW FROM HERE -> new task passs vieew
on suit etapes (le new password et en dehors du node) puis on fait click sur comptabilité(ou)->delegate control-> on add a responsable et coche les 2 premier (create et reset password)
se co avec admin du cd

**Créer un groupe de serveurs dans le Gestionnaire de serveurs et nommer-le SRV_Form et Installer Le rôle IIS sur le serveur CORE et sur un serveur Membre**
on va dans le dasboard create a server groupe (dans ad on add les serveur voulu), puis on va add features et on met server web (iis) sur les serveur voulues.it


-------

iis :Internet Information Services, anciennement Internet Information Server, communément appelé IIS (prononcé généralement "2 i s"), est un serveur Web (HTTP) des différents systèmes d'exploitation Windows NT.
IIS est un le serveur web progiciel conçu pour Windows Server. Il est utilisé pour l'hébergement sites Internet et d'autres contenus sur le Web.

wpf => interface graphique de windows pour du power shell

