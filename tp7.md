# Atelier n°7

avoir toujours un ip fixe
faire un reverse DNS (donne une ip ex: 8.8.8.8 il nous donne google)

**Créez un serveur DHCP sur le site de LYON et configurez-le pour qu’il attribue des adresses et des paramètres IP pour les postes clients et les serveurs de tous les sites.**
on va dans dasboard add features -> on selectionne cd puis on coche DHCP

dans les notif on peut config dhcp, click dhcp manager sur cd on va faire 3 scop avec 29-30-31 puis on va en rerver une addressse dans scpop reserve de chaque scop, 
on va créer nouveau dhcp sur sml1 puis dans le cd on va dans dhcp manager puis clik sur dhcp et add server
on va mettre failover (comme çav cela va se dupliquer et mettre sur l'auter server car si le premier tombe le 2e prend le relais)
pour tester sur un serveur memebre on fait ipconfig puis ipconfig /release puis ipconfig / renew
pour tester si l'autre serveur dhcp prend le relais on désactive les adaptateur de cd et on refait renew

=> get mac en cmd pour avoir l'adresse mac quand fait réservation
mes scoope sont mes pool d'addresse, mes reservation sont les adresse static pour les sever cd, sml1 par exemple.

**Ouvrez la console DNS, sélectionnez la zone de votre domaine et rechercher les définitions des enregistrements présents (S.O.A, NS, A, A.A.A.A …)**

**L’enregistrement SOA**
SOA signifie Start of Authority (début d’autorité). Les enregistrements de ce type renferment des informations sur la zone, qui sont organisées au moyen du fichier de zone ou du serveur DNS. Ils sont importants entre autres pour le transfert de zone : ce transfert consiste à répliquer une zone d’un serveur vers un autre pour parer d’éventuelles pannes. Le transfert de zone permet d’assurer une réplication fidèle du fichier d’origine. Dans un tel enregistrement DNS, vous trouverez derrière l’adresse électronique de l’administrateur un numéro de série. Celui-ci est incrémenté à chaque nouvelle mise à jour.

**L’enregistrement A**
La plupart des résolutions de noms sur Internet se font au moyen des enregistrements de type A. Son champ de donnée renferme une adresse IPv4. Ces enregistrements permettent notamment à un internaute de saisir un nom de domaine dans le navigateur : l’ordinateur envoie alors une requête HTTP à l’adresse IP correspondante. Une adresse IPv4 ayant toujours une taille de 4 octets, la valeur rdlength sera toujours 4.


**L’enregistrement AAAA**
Un enregistrement AAAA, aussi connu sous le nom de « quad-a », fonctionne comme un enregistrement A, sauf qu’il a recours à une adresse IPv6 au lieu d’une adresse IPv4 pour résoudre le nom du domaine. Une adresse IPv6 ayant une longueur de 128 bits ou 16 octets, on précise ici la longueur du champ de données. La désignation AAAA est une manière d’indiquer que cet enregistrement DNS est quatre fois plus long qu’un enregistrement A.

**L’enregistrement NS**
Dans un enregistrement NS, l’entrée du serveur de nom d’un fichier de zone, on vous indique la compétence d’une zone particulière. Cette entrée est donc obligatoire pour chaque fichier de zone. Cet enregistrement de ressources permet d’indiquer au serveur DNS s’il est compétent pour la requête, c’est-à-dire en charge de la zone, ou bien s’il doit transférer la requête.


**reverse DNS : on envoi requete dns puis on a le nom**
on va dans dns puis dns management puis revers -> primary puis on suuit etape. penser a mettre dans interface ipv6 mettre detecte automatiquement le DNS.
puis pour tester on fait nslooksup 172.31.1.1
http://www.antrimohamed.fr/nslookup-serveur-par-defaut-unknown/ 
