# Atelier 4

- Sur chaque Serveur 2016-19 créer un groupe Local ayant comme nom : GL_ESN, créer deux utilisateurs de domaine Jean Vien et Jean Peuplus, ils doivent appartenir 
au groupe GL_ESN. L’utilisateur Jean Vien doit appartenir aux groupes administrateur local des machines du domaine.
- Créez des groupes Globaux pour les responsables de chaque service, un pour les employés, et un par service, exemple : G_Responsable
Répartissez l’ensemble des utilisateurs crées dans leur groupe respectifs.
- Créer trois groupes de Domaine Locaux : DL_Total_Ressources, DL_Lecture_Ressources, DL_Refuser_Ressources.
Placer les groupes Globaux dans les groupes de domaine Locaux de la manière suivante :
  - G_Responsables et G_Direction dans le groupe DL_Total_Ressources
  - G_Informatique, G_Comptabilite, G_Marketing sont dans le groupe DL_Lecture_Ressources
  - G_Production est dans le groupe DL_Refuser_Ressources


- Le responsable informatique doit faire partie du groupe Administrateur du domaine, l’employé n°1 doit être membre des groupes Opérateur d’impression, 
de sauvegarde, de compte et de serveur, le second membre du groupe Lecteur des journaux d’évènements, utilisateur de l’analyseur de performances et utilisateur du journal de 
performance


-------
l'annuaire de regle jamais sur les noms toujours sur les groupe car si une personne à un accident et qu'on doit recup qql chose il faut se souvenir de ou son nom apparait.

---

group domain local on fait dans tools user computer on va créer new group check domain local.

pour faire gl_responsable dans DL_Lecture_Ressources donc on va add a un group gl_responsable.
pour groupe local on va dans un serveur memebre, puis computer managment on va dans system tools -> local user -> group. on va rajouter dans la ou on est dans le groupe existant administrator et on add jean vien.

pour dernier question: on va dans user and computer dans users (trucs de basse) et on va clicker sur domain admini et add un memebre.
pour le 1 on va idem user&com-> buldin-> print/account/backup/server operator et add un random gars.
pour le 2 on va idem user&com-> buldin-> event/preformance log user et add un random gars

----------

 Les groupes locaux sont vraiment locaux. Ils sont définis et disponibles uniquement pour l’ordinateur spécifique sur lequel ils ont été créés. Ne créez pas de nouveaux groupes locaux sur les postes de travail ; dans la plupart des cas, les seuls groupes locaux qu’il faut gérer sont les groupes d’utilisateurs et d’administrateurs.
    
 Les groupes locaux de domaine permettent de gérer les autorisations des ressources, car ils peuvent être appliqués partout dans le domaine. Un groupe local de domaine peut inclure des membres du domaine de tout type et des membres issus de domaines de confiance. Supposons par exemple que vous deviez gérer l’accès à une collection de dossiers sur un ou plusieurs serveurs contenant des informations destinées aux responsables. Le groupe que vous créez dans ce but doit être un groupe local de domaine (par exemple, « DL_Managers_Modify »).
    
 Les groupes universels d’Active Directory sont utiles dans les forêts multi-domaines. Ils vous permettent de définir des rôles ou de gérer des ressources couvrant plusieurs domaines. Chaque groupe universel est stocké dans le domaine dans lequel il a été créé, mais son appartenance aux groupes est stockée dans le catalogue global et répercutée à l’ensemble de la forêt. N’utilisez pas les groupes universels si vous n’avez qu’un seul domaine.
    
Les groupes globaux servent principalement à définir des collections d’objets de domaine (utilisateurs, autres groupes globaux et ordinateurs) en fonction des rôles métier, ce qui signifie qu’ils servent principalement de groupes de rôles. Les groupes d’utilisateurs basés sur des rôles (par exemple, « RH » ou « Marketing ») et les groupes d’ordinateurs basés sur des rôles (par exemple, « Postes de travail marketing ») sont généralement des groupes globaux.
