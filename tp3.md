# Compte-Rendu Administration Système / TP 3 - Gestion des paquets

## Exercice 1 - Commande de base

1- La commande correspondant à l'affichage des 5 derniers paquets installés sur votre machine est :
*cat /var/log/dpkg.log | grep installed | tail -n 5* . En effet :

      cat /var/log/dpkg.log     -     affiche l'historique des installations sur la machine
      
      grep installed            -     recherche le mot-clé "installed" dans la recherche 
      
      tail -n 5                 -     affiche les 5 dernières lignes de la recherche
      
Ainsi on obtient, via l'historique présent dans */var/log/dpkg.log*, la liste des 5 derniers paquets installés.

2- Le comptage du nombre de paquet via :

* *dpkg* : *dpkg -l | wc -l*  => *dpkg -l* affiche l'ensemble des paquets installés ; *wc -l* compte le nombre de ligne engendré par la commande *dpkg -l* . Résultat affiché : 572.

* *apt*  : *apt list | grep installé | wc -l* => *apt list | grep installé* affiche l'ensemble des paquets installés (en recherchant le mot clé **installé** dans la recherche) ; *wc -l* compte le nombre de ligne engendré par la commande *apt list | grep installé* . Résultat affiché : 506.

Cette différence s'explique ?????????

3- Pour dénombrer l'ensemble des packages disponibles au téléchargement, on procède de la manière suivante  :
* *apt list | wc -l* => renvoie le nombre de package disponibles et installés sur le serveur. Résultat : 61599
* *apt list | grep installé | wc -l* => renvoie le nombre de package installés. Résultat : 506

En conséquence, le nombre de paquets sont disponibles en téléchargement est 61093.

4- Créer un alias “maj” qui met à jour le système = *alias maj='sudo apt update'

5- Le paquet fortunes sont de petits messages, des citations, des proverbes, etc. affichés à chaque connexion en mode console (terminal). Son installation se réalise de la manière suivante : *sudo apt install fortune*. Pour vérifier son installation, on tape *fortune*, une citation s'affiche à l'écran en cas de bonne installation.

6- Pour chercher l'ensemble des packages permettant de jouer au sudoku, on utilise la commande *apt search sudoku*. Elle affiche à l'écran l'ensemble des packages contenant dans leurs descriptifs sudoku.

7- Afin de lister l'ensemble des packages installés avec *apt install*, on note la commande *dpkg -S apt install* . Il y en a 580.




