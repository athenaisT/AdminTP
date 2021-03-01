# Atelier n°7

avoir toujours un ip fixe
faire un reverse DNS (donne une ip ex: 8.8.8.8 il nous donne google)

**Créez un serveur DHCP sur le site de LYON et configurez-le pour qu’il attribue des adresses et des paramètres IP pour les postes clients et les serveurs de tous les sites.**
on va dans dasboard add features -> on selectionne cd puis on coche DHCP

dans les notif on peut config dhcp, click dhcp manager sur cd on va faire 3 scop avec 29-30-31 puis on va en rerver une addressse dans scpop reserve de chaque scop, 
on va créer nouveau dhcp sur sml1 puis dans le cd on va dans dhcp manager puis clik sur dhcp et add server
on va mettre failover (comme çav cela va se dupliquer et mettre sur l'auter server car si le premier tombe le 2e prend le relais)
pour tester sur un serveur memebre on fait ipconfig puis ipconfig /release puis ipconfig / renew
