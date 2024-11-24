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

Disponible avec le fichier pcs. Cette version propose un seul timer modifiable au moment de la programmation et un usage de l'écran virtuel

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
  
## Schéma de cablâge

![cablage](./res/MACC3-Cablage.drawio.png)

## Chargement du programme

__Pour charger le programme il est nécessaire d'avoir__  
- Un millenium SLim 230V alimenté
- Le logiciel [Crouzet Soft](https://www.crouzet.com/softwares/download) gratuit - v1.12 ou supérieure
- Le programme (fichier *.pcs) de ce dépôt

__Personnalisation des timers__  
- T1: Bloc B61 : temporisation de premier démarrage, exprimé en secondes
- T3: Bloc B24 : temporisation de redémarrage, exprimé en heures, minutes, secondes
- T2: Bloc B60 : temporisation avant chaque démarrage, exprimé en dixième de secondes

Voir le [PDF](./res/Slim_Timer_ACC3_Universel.pdf), page 2, pour le détail des blocs si besoin

__Chargement__  
- Ouvrir le programme depuis Crouzet Soft
- Sans le menu contrôleur> connexion sélectionnez Bluetooth
- Sélectionner votre Millenuim Slim dans la fenêtre de configuration
- Injecter le programme via le bouton d'écriture

Vous pouvez simuler le programme avant de vous lancer.

## Modification du programme

Modification des temporisations à votre convenance (c'est nécessaire).    
Créer un écran de configuration des timers.  
Une évolution possible est de remplacer le thermostat puisque les entrées restantes peuvent accueillir une sonde de température.  
Toute autre modification...  

Le programme fonctionne aussi sur les autres automates Crouzet, c'est le même logiciel de programmation.


