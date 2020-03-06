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

3- Pour dénombrer l'ensemble des packages disponibles au téléchargement, on procède de la manière suivante  :
* *apt list | wc -l* => renvoie le nombre de package disponibles et installés sur le serveur. Résultat : 61599
* *apt list | grep installé | wc -l* => renvoie le nombre de package installés. Résultat : 506

En conséquence, le nombre de paquets sont disponibles en téléchargement est 61093.

4- Créer un alias “maj” qui met à jour le système = *alias maj='sudo apt update'

5- Le paquet fortunes sont de petits messages, des citations, des proverbes, etc. affichés à chaque connexion en mode console (terminal). Son installation se réalise de la manière suivante : *sudo apt install fortune*. Pour vérifier son installation, on tape *fortune*, une citation s'affiche à l'écran en cas de bonne installation.

6- Pour chercher l'ensemble des packages permettant de jouer au sudoku, on utilise la commande *apt search sudoku*. Elle affiche à l'écran l'ensemble des packages contenant dans leurs descriptifs sudoku.

7- Afin de lister l'ensemble des packages installés avec *apt install*, on note la commande *dpkg -S apt install* . Il y en a 580.

## Exercice 2 

Pour savoir à partir de quel paquet est installé *ls*, on note la commande : 

which -a ls | xargs dpkg -S => coreutils: /bin/bash (*ls* est dans le paquet *coreutils* situé dans le répertoire bin/bash) ; xargs permet de recuperer les résultats de la première commande et de les passer en argument à la deuxième.

script origine-commande:

#!bin/bash 

echo $(which -a $1 | xargs dpkg -S )


## Exercice 3

Ecrire une commande qui aﬀiche “INSTALLÉ” ou “NONINSTALLÉ” selon le nom et le statut du package spécifié dans cette commande :

dpkg -l "nomdupackage" | grep "^ii") && echo "installé" || echo "non installé"

## Exercice 4

1- Pour afficher la liste des programmes installés avec coreutils on utilise la commande : 

*apt-file list coreutils*.

2- L'outil *\[* est le symbole conventionnel pour tester une commande dans le bash. Par exemple, si l'on souhaite test la commande *-e* qui permet de vérifier la présence d'un fichier au sein du répertoire courrant, et en conséquence afficher "1" si le fichier recherché y est présent et "0" dans le cas contraire, on réalisera la commande bash suivante : 

*if \[ -e fichier ]; then echo "1"; else echo "0"; fi*

## Exercice 5 - aptitude 

1- On procède dans un premier temps à l'installation de **aptitude** via la commande :

*sudo apt install aptitude*

2- On recherche par la suite le paquet *emacs* à intsaller (pour aller plus vite on peut tapper le mot clé "emacs" précédés d'un "/").

On procède ainsi :

![lancement aptitude](https://github.com/cpe-lyon/tp3_moine-pinet/blob/master/1.PNG)
![recherche des paquets non installés](https://github.com/cpe-lyon/tp3_moine-pinet/blob/master/3.PNG)
![recherche de "emacs" qui est un éditeur de texte](https://github.com/cpe-lyon/tp3_moine-pinet/blob/master/4.PNG)
![écran de préinstallation NB : pour installer un package, il faut pointer sur ce dernier et appuyer successivement sur "+" ; "g" ; "g" ](https://github.com/cpe-lyon/tp3_moine-pinet/blob/master/5.PNG)

NB : pour installer un package, il faut pointer sur ce dernier et appuyer successivement sur "+" ; "g" ; "g".

![écran en cours d'installation du package "emacs"](https://github.com/cpe-lyon/tp3_moine-pinet/blob/master/7.PNG)

NB : pour installer un paquet, il est préférable de lancer la commande *sudo bash* avant de lancer **aptitude** dans le but d'être "superutilisateur" (ou encore "root") afin de posséder l'ensemble des droits d'accés aux fichiers nécessaires à l'installation.

Pour vérifier que notre paquet est bien installé, on éxécute la commmande : 

apt list | grep emacs | grep installé

On observe en conséquence qu'un nombre conséquent de paquets relatifs à **emacs** ont été installés.

## Exercice 6 - Installation d’un paquet par PPA 

1- Installation de la version Oracle de Java (avec l’ajout des PPA) : 
* sudo add-apt-repository ppa:linuxuprising/java 
* sudo apt update 
* sudo apt install oracle-java11-installer

2- Le fichier /etc/apt/sources.list.d contient les fichiers :
* linuxuprising-ubuntu-java-eoan.list
* linuxuprising-ubuntu-java-eoan.list.save

Le premier, comme le second, contiennent un ensemble de lien vers **ppa.launchpad.net**, services proposés dans le cadre de la plate-forme LaunchPad, qui prend le code source déposé par les développeurs de logiciels et génère des paquets .deb que les utilisateurs d'Ubuntu pourront installer à travers leur gestionnaire de paquets logiciels.

## Annexes sujet Exerice 7 et 8

### Exercice 7

![sujet tp](https://github.com/cpe-lyon/tp3_moine-pinet/blob/master/10.PNG)
![sujet tp](https://github.com/cpe-lyon/tp3_moine-pinet/blob/master/11.PNG)
![sujet tp](https://github.com/cpe-lyon/tp3_moine-pinet/blob/master/12.PNG)

### Exercice 8

![sujet tp](https://github.com/cpe-lyon/tp3_moine-pinet/blob/master/13.PNG)




![tortank ascii](https://github.com/cpe-lyon/tp3_moine-pinet/blob/master/14.PNG)


