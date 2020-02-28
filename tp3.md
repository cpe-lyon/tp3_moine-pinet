# Compte-Rendu Administration Système / TP 3 - Gestion des paquets

## Exercice 1 - Commande de base

1- La commande correspondant à l'affichage des 5 derniers paquets installés sur votre machine est :
*cat /var/log/dpkg.log | grep installed | tail -n 5* . En effet :

      cat /var/log/dpkg.log     -     affiche l'historique des installations sur la machine
      
      grep installed            -     recherche le mot-clé "installed" dans la recherche 
      
      tail -n 5                 -     affiche les 5 dernières lignes de la recherche
      
Ainsi on obtient, via l'historique présent dans */var/log/dpkg.log*, la liste des 5 derniers paquets installés.

2- Le comptage du nombre de paquet via :

* *dpkg* : *dpkg -l | wc -l*  => *dpkg -l* affiche l'ensemble des paquets installés ; *wc -l* compte le nombre de ligne engendré par la commande *dpkg -l*

* *apt*  : *apt list | grep installé | wc -l* => *apt list | grep installé* affiche l'ensemble des paquets installés (en recherchant le mot clé **installé** dans la recherche) ; *wc -l* compte le nombre de ligne engendré par la commande *apt list | grep installé*


