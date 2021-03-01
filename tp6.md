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

on va dans cd on va dans all server et on add le serveur memebre, puis clique droit dessus add roles et features on next les 3 premier puis on coche ad et services et on next jusqu'à install

wpf => interface graphique de windows pour du power shell

