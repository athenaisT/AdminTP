# Atelier 5

Sur le serveur Membre SML1 modifier les autorisations de partage et les paramètres de sécurité NTFS du répertoire Partagé Données :
  - Autorisations de Partage : 
     Contrôle total au groupe : Tout le monde
  Paramètres de sécurité NTFS : 
    - Contrôle total au groupe : DL_Total_Ressources
    - Lecture au groupe :  DL_Lecture_Ressources
    - Refuser au groupe : DL_Refuser_Ressources
Sur le serveur Membre SML2 modifier les autorisations de partage et les paramètres NTFS du répertoire Partagé Données :
  - Autorisations de Partage : 
    -  Contrôle total au groupe : DL_Total_Ressources
    -  Lecture au groupe : DL_Lecture_Ressources
    - Refuser au groupe : DL_Refuser_Ressources


------

**sm1**
on va créer dans explorateur-> shares -> un foldre ou on va faire advanced share-> permission fulll conttrol .

ntfs  

dans explorateur-> shares -> un folder ou on va faire advanced sécurity-> permission fulll conttrol ou read et tout ça en fonctionde dl et droit demander et permission dans share advanced everyone full controlle.

**sml2**
on va metrre dans permission advanced les dl et security a tous fulll controll


quand les regle de sécu sont okay et permission share non  => c'est pas bon car normalement on devrait pourvoir faire action, 

les regle de sécu sont plus forte ue les permsission de share. (faut donc favoriser mettre les regles de sécu si on veut partager) 

------


Paramètres de sécurité NTFS : 
 - Contrôle total au groupe : Tout le monde </br>
**fait sur sml2**

- Connectez-vous en Local sur SML1 puis essayer de créer un fichier dans le répertoire Données situé sur SML1, effectuer cette procédure trois fois avec un utilisateur appartenant aux groupes suivants : G_Direction, G_Comptabilité et G_Production

=> se co avec un user de ses service normallent on doit pouvoir tout faire selon les droits.

- Connectez-vous en Local sur SML2 puis essayer de créer un fichier dans le répertoire Données situé sur SML2, effectuer cette procédure trois fois avec un utilisateur appartenant aux groupes suivants : G_Direction, G_Comptabilité et G_Production 


=> se co avec un user de ses service normallent on doit pouvoir tout faire sans respect des droit mis.

- Connectez-vous en Local sur SML1 puis essayer de créer un fichier dans le répertoire Données situé sur SML2 « \\SML2\Donnees », effectuer cette procédure trois fois avec un utilisateur appartenant aux groupes suivants : G_Direction, G_Comptabilité et G_Production 

------------
L’abréviation « NTFS » renvoie à « New Technology File System » (littéralement : nouveau système de fichiers technologique). Du fait de la prédominance de Microsoft, NTFS est un système de fichiers très répandu permettant l’organisation des données sur des disques durs et des supports de données. Depuis l’introduction de Windows XP en 2001, ce système de fichiers est le standard incontesté pour les systèmes d’exploitation Windows. Dans les sections suivantes, nous vous expliquons dans le détail comment il fonctionne, quels sont ses avantages et en quoi il se démarque des autres systèmes, par exemple des systèmes FAT.

http://www.prosygma.com/iishelp/iis/htm/core/iidfpsc.htm 
