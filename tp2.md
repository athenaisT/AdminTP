# TP 2

Création de l’arborescence Active Directory sur du papier, nous essaierons d’automatiser les créations des OU.  
Pour chacun des services créez 30 utilisateurs : 2 responsable RD pour le Responsable Direction   
Nous utiliserons un script PowerShell fournit pour les noms des utilisateurs.  

Modifier les propriétés de comptes afin que les employés ne puissent pas changer leur mot de passe.   
Seuls les responsables ont l’autorisation de se connecter le week-end.  
Renseigner pour tous les utilisateurs les champs Villes, Fonction, Service et Société.  
Créez un Serveur Membre à partir de la Base Windows Server 2019 dans chaque Site Paris, Marseille et Lyon et placez-les dans leurs UO Serveur respective. Nommez-les en respectant</br> la convention suivante : SMM1 pour le premier Serveur Membre du site de  Marseille. Le site Lyon compte deux serveurs Membres.
Créez un Serveur Membre Core à partir de la Base Windows Server 2019 Core dans le site de Paris, placez-le dans son UO Serveur respective. Nommez-le en respectant la convention</br> suivante : SMCP1 pour le premier Serveur Membre Core de Paris. 
Créer un client par site géographiques.


pour OU, Si y a que utilisateur ou ordi conditions pas respecter; toujours remplir description pour simplifier lecteru erreurs; créer utlisateur virtuelle qui supervise :supervision 
regarder bien quand coche pour new object + dans propriete y a plein de chose à remplir
automatiser remplissage car si plein de truc a remp peut se tromper; on gere plein de truc avec le script
gérer en entrée , se mettre d'accord sur le filtrage comme ça on sais ou aller pour corriger
On peut changer la destination du profil, il peut avoir son profil sur sa clé gentre U:profile et dés que la clé se monte il a son profil.
si a systeme gpo si ajoute un membre y a des ruc mis en auto/remp selon regle


pour retirer droit sur un dossier si a pas décocher pour OU: views -> advances feature -> dossier-> properties

**1: faire arboresccences des utilisateur et ordi (OU)**
Utilisateur:
  -Lyon(OU)
        Direction
        Informatique
        Compta
        Marketing
        Production
  -Paris(OU)
        Direction
        Informatique
        Compta
        Marketing
        Production
  -Marseille(OU)
        Direction
        Informatique
        Compta
        Marketing
        Production
**2:Script pour faire cette arbo**  # script doit etre fini pour atelier 3( février)
on tape power dans vm-CD (power Shell ISE à choisir)
New-ADOrganizationalUnit -Name "Lyon" -Path "OU=UTILISATEURS,DC=ENS,DC=dom"   (pour créer OU lyon) MAIS avant il faut faire les vyos

**2,5 : VyOS (routeur virtuelle):**
importe vm vyos(snapshot+clone)  (login: vyos   mdp: vyos )
pour mettre en fr : set console keymap -> generique 105 -> other -> french-> french -> ok->ok

ajouter en physic (settings-> add ->W network adaptater)  les interfaces


DNAT (nat en entrée)
