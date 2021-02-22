# Atelier 4

- Sur chaque Serveur 2016-19 créer un groupe Local ayant comme nom : GL_ESN, créer deux utilisateurs de domaine Jean Vien et Jean Peuplus, ils doivent appartenir 
au groupe GL_ESN. L’utilisateur Jean Vien doit appartenir aux groupes administrateur local des machines du domaine.
- Créez des groupes Globaux pour les responsables de chaque service, un pour les employés, et un par service, exemple : G_Responsable
Répartissez l’ensemble des utilisateurs crées dans leur groupe respectifs.
- Créer trois groupes de Domaine Locaux : DL_Total_Ressources, DL_Lecture_Ressources, DL_Refuser_Ressources.
Placer les groupes Globaux dans les groupes de domaine Locaux de la manière suivante :
G_Responsables et G_Direction dans le groupe DL_Total_Ressources
G_Informatique, G_Comptabilite, G_Marketing sont dans le groupe DL_Lecture_Ressources
G_Production est dans le groupe DL_Refuser_Ressources
-Le responsable informatique doit faire partie du groupe Administrateur du domaine, l’employé n°1 doit être membre des groupes Opérateur d’impression, 
de sauvegarde, de compte et de serveur, le second membre du groupe Lecteur des journaux d’évènements, utilisateur de l’analyseur de performances et utilisateur du journal de 
performance
