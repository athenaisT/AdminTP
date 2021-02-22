# Atelier 3

GPO penser a ce que stratégie soit sur user ET ordi
Y' a des empillages de gpo, il faut voir les priorité
chercher executable de type msi.
default domain policie, on ne touche jamais ce qui est fait par défaut donc si peut soit créer un doublons soit on let un mdp fort dessus.


**Default domain policie**
si besoin internet met en nat une 2e adaptateur car vyos se deconf si change d'ordi
On fait tools puis user and computer on va dans Sites (lyon, Marseille, Paris) et on créer un groupe Responsable (new -> group)
Puis on va dans group polici management -> deploie la foret -> quand arrive à dans coupet et user on va dans computer et on fait policies, -> windows config-> security->local policies 
->user right ->allow log only

**quand change les truc pour mot de passe**

Puis on va dans group polici management -> deploie la foret -> quand arrive à dans coupet et user on va dans computer et on fait policies, -> windows config-> security->
account policies ->password->puis on modif en fonction du sujet

**Pour regle service informatique**

**On fait pso (strategie de mdp)**
On fait un nouveau groupes dans les site, informatique
puis on va dans tools -> active center (le 1e)-> puis dans ens(local)-> system-> password setting-> new puis config (on y add dans le group informatique créer)

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
