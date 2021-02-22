# Atelier 3

GPO penser a ce que stratégie soit sur user ET ordi
Y' a des empillages de gpo, il faut voir les priorité
chercher executable de type msi.
default domain policie, on ne touche jamais ce qui est fait par défaut donc si peut soit créer un doublons soit on let un mdp fort dessus.

**A l’aide d’une stratégie de groupe existante donnez l’autorisation à chaque responsable de chaque Service l’autorisation d’ouvrir une session sur l’ensemble des contrôleurs de domaine de la société.**

**Default domain policie**
si besoin internet met en nat une 2e adaptateur car vyos se deconf si change d'ordi
On fait tools puis user and computer on va dans Sites (lyon, Marseille, Paris) et on créer un groupe Responsable (new -> group)
Puis on va dans group polici management -> deploie la foret -> quand arrive à dans coupet et user on va dans computer et on fait policies, -> windows config-> security->local policies ->user right ->allow log only


**Le mot de passe ne peut être repris pendant une année
Il doit être changé au moins une fois tous les trente jours et doit être complexe et doit être composé de cinq caractères minimum.**
**quand change les truc pour mot de passe**
Normalement il aurrait fallut faire une pso pour tout le monde!
Puis on va dans group polici management -> deploie la foret -> quand arrive à dans coupet et user on va dans computer et on fait policies, -> windows config-> security->
account policies ->password->puis on modif en fonction du sujet

**Pour regle service informatique**

**Les membres du service Informatiques doit avoir un mot de passe qui dont la longueur doit être de 9 caractères minimum et complexe.**
**On fait pso (strategie de mdp)**
On fait un nouveau groupes dans les site, informatique
puis on va dans tools -> active center (le 1e)-> puis dans ens(local)-> system-> password setting-> new puis config (on y add dans le group informatique créer)

**Les postes du site de Lyon doivent avoir le programme 7zip et les membres du service Informatique utilisent le programme Notepad++, par contre le logiciel doit être masqué si une autre personne se sert du PC.**

**Pour on veut que les lyonnais et zip**
On va télécharger le msi de 7zip
On va dans tools -> group polici management -> on va dans sites dans lyon puis clik droit new gpo (nommé lyon7zip)-> puis on fait edit -> on va dans computer-> 
policies->softaware->new package et on selection 7zip

**pour notepad**
del notepad++ msi
On créer une gpo dans group mangement policies dans group object et puis edit le gpo on va dans computer-> 
policies->softaware->new package et on selection nottpad puis on va aller dans les services informatiques (lyon, paris, marseille) et on va linked existing gpo 
et on sellectionne celle de nottepadd. (pas pareille que zip ca r zip que pour lyon).

**pour supprimer le menu Exécuter pour l’ensemble du Domaine mais les membres du service Informatique on cette commande**

on creer une gpo pui quand click normal dessu il a un onglet delegation -> advenced-> on va add informatique puis cocher dans deny aply group policies et on va edit 
puis -> user-> admin-> start menu->double click et on va mettre en enable.

**Sauvegarder l’ensemble des GPO du Domaine un serveur membre de votre choix. Discussion sur la sauvegarde des GPO et leur restauration**








--------------------------------

L S D Ou   =>ordre des executions des strategies de groupe des gpo


