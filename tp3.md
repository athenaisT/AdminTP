# Atelier n° 3

GPO penser a ce que stratégie soit sur user ET ordi </br>
Y' a des empillages de gpo, il faut voir les priorité </br>
chercher executable de type msi. </br>
default domain policie, on ne touche jamais ce qui est fait par défaut donc si peut soit créer un doublons soit on let un mdp fort dessus. </br>

**A l’aide d’une stratégie de groupe existante donnez l’autorisation à chaque responsable de chaque Service l’autorisation d’ouvrir une session sur l’ensemble des contrôleurs de domaine de la société.**

**Default domain policie**
si besoin internet met en nat une 2e adaptateur car vyos se deconf si change d'ordi </br>
On fait tools puis user and computer on va dans Sites (lyon, Marseille, Paris) et on créer un groupe Responsable (new -> group) </br>
Puis on va dans group polici management -> deploie la foret -> quand arrive à dans coupet et user on va dans computer et on fait policies, -> windows config-> security->local policies ->user right ->allow log only


**Le mot de passe ne peut être repris pendant une année
Il doit être changé au moins une fois tous les trente jours et doit être complexe et doit être composé de cinq caractères minimum.**
**quand change les truc pour mot de passe**</br>
Normalement il aurrait fallut faire une pso pour tout le monde! </br>
Puis on va dans group polici management -> deploie la foret -> quand arrive à dans coupet et user on va dans computer et on fait policies, -> windows config-> security-> 
account policies ->password->puis on modif en fonction du sujet

**Pour regle service informatique**

**Les membres du service Informatiques doit avoir un mot de passe qui dont la longueur doit être de 9 caractères minimum et complexe.**
**On fait pso (strategie de mdp)**</br>
On fait un nouveau groupes dans les site, informatique </br>
puis on va dans tools -> active center (le 1e)-> puis dans ens(local)-> system-> password setting-> new puis config (on y add dans le group informatique créer) </br>

**Les postes du site de Lyon doivent avoir le programme 7zip et les membres du service Informatique utilisent le programme Notepad++, par contre le logiciel doit être masqué si une autre personne se sert du PC.**

**Pour on veut que les lyonnais et zip** </br>
On va télécharger le msi de 7zip , du coup on met la gpo dans le site lyon</br>
On va créer un dossier partager: dans la gauche du menu de base, on à file and storage; puis share -> new->selct puis next tout le temps (a part pour le nom) </br>
Puis on va dans explorateur de fichier pour trouver notre dossier et on va y glisser les appli voulues. </br>
On va dans tools -> group polici management -> on va dans sites dans lyon puis clik droit new gpo (nommé lyon7zip)-> puis on fait edit -> on va dans computer-> 
policies->softaware->new package et on selection 7zip dans le dossier shares créer

**pb** il faut refaire le dosssier à la main le doossier avec click droit propereties-> sharing ->advenced sharing **JAMMAIS FAIRE CLICK SHARES..**, full droit et rajouter everyone avec cocher modify et quqand ajoute packet zip on fait le lien réséeau (avec //) car sinon le serveurM va chercher en local un chemin qu'il n'a pas.

**pour notepad**</br>
del notepad++ msi</br>
On créer une gpo dans group mangement policies dans group object et puis edit le gpo on va dans computer-> </br>
policies->softaware->new package et on selection nottpad puis on va aller dans les services informatiques (lyon, paris, marseille) et on va linked existing gpo </br>
et on sellectionne celle de nottepadd du shares. (pas pareille que zip ca r zip que pour lyon). </br>

**pour supprimer le menu Exécuter pour l’ensemble du Domaine mais les membres du service Informatique on cette commande**

on creer une gpo puis on va edit puis -> user-> admin-> start menu->double click et on va mettre en enable. Penser à y linked au site puis on va crere une autre gpo idem sauf qu'il ya aura desable (pour y link au informatique) </br>

**pour tester**
on va creer un nouvel utlisateur dans user et computer (pour si co su rles serveur membre) car si en admin on a le droit à tout (donc y voit pas)

**Sauvegarder l’ensemble des GPO du Domaine un serveur membre de votre choix. Discussion sur la sauvegarde des GPO et leur restauration**</br>

https://www.it-connect.fr/chapitres/sauvegarde-et-restauration-des-strategies-de-groupe-gpo/ 

dans les tools -> group management policies on va dans les gpo et on clique droit sur le fichier et on fait backup (emplacement c'est la ouon va y copier ici une clé USB)</br>
ensuite sur un autre serveur memebre on créer un fichier sauvegarde et on y copirera dedans(ici serveur Memebre c'est celui de marseille) 


--------------------------------

L S D Ou   => ordre des executions des strategies de groupe des gpo

>Local : la GPO d’ordinateur qui est la première crée lorsque l’ordinateur est installé.</br>
>Site : une GPO de site.</br>
>Domaine : une GPO qui applique des paramètres communs à l’ensemble du domaine.</br>
>OU : Unité d’Organisation Active Directory dans lesquelles des utilisateurs, ordinateurs, groupes et autres OU peuvent être stockés</br>


