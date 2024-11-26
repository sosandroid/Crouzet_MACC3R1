# Relai temporisé MACC3R1 Crouzet

Ce relai MACC3R1 n'étant plus fabriqué, il est possible de proposer une alternative à base de petit automate. Il est utilisé pour les PAC (Pompes à Chaleur). Le Crouzet [Millenium Slim](https://soda.crouzet.com/pn/?i=88983903) est parfait pour cela. Le relai MACC3R1 existe en plusieurs versions : 
- MACC3R1 SP 05039 - 88826867 - Délai de redémarrage de 25 minutes
- MACC3R1 SP 08001 - 88826890 - Délai de redémarrage de 3 minutes avec délai de 5 secondes à chaque démarrage

Toutes ces versions peuvent être gérées par le Millenium Slim et une personnalisation du programme

## Diagramme de fonctionnement

![Diagramme de fonctionnement](./res/MACC3R1_Diagramme_u.drawio.png)
- T1: délai au premier démarrage
- T2: délai à chaque démarrage
- T3: temporisation de redémarrage

## Fonctionnalités du programme

### Version avec écran

Disponible avec le fichier `Slim_Timer_ACC3_SPxxxxx_ecran.pcs`. Cette version propose un seul timer modifiable au moment de la programmation et l'usage de l'écran virtuel

Les 3 temporisations :
- Premier démarrage du contrôleur : eviter que la PAC démarre juste après la remise sous tension générale (coupure EDF)
- Temporisation de redémarrage (fonction initiale du relai)
- Temporisation avant chaque démarrage (existe pour certaines variantes)

Via un [écran virtuel Crouzet](https://www.crouzet.com/produits/controleurs-automatisme/software/crouzet-virtual-display/) (application iPhone et Android), il est possibile de visualiser 
- Etat du relai
- Etat de l'entrée du thermostat
- Compte à rebours
- Mise à zéro du compte à rebours - bouton A
- Relancer le délai à la mise sous tension - bouton B

![ecran](./res/ecran.png)

### Version 4 timers sans écran

Cette version propose 4 variations du timer (1 par entrée / sortie) pour ce que soit adaptable sans modification du programme. Les 4 timers fonctionnenent en parallèle. Disponible avec le fichier `Slim_Timer_ACC3_SPxxxxx_4timers.pcs`. Les différents modes sont accessibles selon le tableau ci-dessous:

| Mode                  | Entrée | Sortie |  T1 | T2 |   T3  |
|-----------------------|:------:|:------:|:---:|:--:|:-----:|
| SP08001               |   I1   |   O1   |  0s | 5s |  3min |
| SP08001 1er démarrage |   I2   |   O2   | 60s | 5s |  3min |
| SP05039 1er démarrage |   I3   |   O3   | 60s | 0s | 25min |
| SP05039               |   I4   |   O4   |  0s | 0s | 25min |

## Schéma de cablâge

![cablage](./res/MACC3-Cablage.drawio.png)

## Chargement du programme

### Pour charger le programme il est nécessaire d'avoir
- Un millenium SLim 230V alimenté
- Le logiciel [Crouzet Soft](https://www.crouzet.com/softwares/download) gratuit - v1.12 ou supérieure
- Le programme, fichier *.pcs choisi

### Personnalisation des timers

__Version avec écran__ 

- T1: Bloc B61 : temporisation de premier démarrage, exprimé en secondes
- T3: Bloc B24 : temporisation de redémarrage, exprimé en heures, minutes, secondes
- T2: Bloc B60 : temporisation avant chaque démarrage, exprimé en dixième de secondes

Voir le [PDF](./res/Slim_Timer_ACC3_Universel.pdf), page 2, pour le détail des blocs si besoin

__Version sans écran__

Normalement pas besoin de personnalisation, qui se fait par le choix de l'entrée / sortie utilisée.

### Chargement

- Ouvrir le programme depuis Crouzet Soft
- Dans le menu contrôleur > connexion sélectionnez Bluetooth
- Sélectionner votre Millenuim Slim dans la fenêtre de configuration
- Lancez la simulation si nécessaire
- Injecter le programme via le bouton d'écriture


## Modification du programme

Tout est modifiable selon votre besoin 
Créer un écran de configuration des timers.  
Une évolution possible est de remplacer le thermostat puisque les entrées restantes peuvent accueillir une sonde de température.  
Toute autre modification...  

Le programme fonctionne aussi sur les autres automates Crouzet, c'est le même logiciel de programmation.


