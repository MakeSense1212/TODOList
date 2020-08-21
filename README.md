# NativeScript-Vue Application

> A native application built with NativeScript-Vue

## Usage

``` bash
# Install dependencies
npm install

# Preview on device
tns preview

# Build, watch for changes and run the application
tns run

# Build, watch for changes and debug the application
tns debug <platform>

# Build for production
tns build <platform> --env.production

### Description du sujet selectionné
#Le projet à pour but d'afficher une liste de chose à faire. Il est possible d'obtenir plus de detail sur un tache en cliquant dessus.

### Indication concernant les outils utilisés
#NativeScript + VueJS

### Indication concernant les TD réalisés
#TD-1

### Les inscructions pour installer et démarrer le projet
#Brancher votre appareil sur votre ordinateur
#Lancer le CMD et rendez-vous à l'endroit ou est sauvegarder le projet
#Effectuer la commande 'tns run android' ou 'tns run ios' en fonction de votre appareil
#Ensuite, l'application est disponible sur votre appareil sous forme de logo

### Information utile : problèmes rencontrés, etc ...
#1er gros problème, l'ouverture d'une nouvelle page lorseque l'on clique sur un bouton pour en savoir plus sur une tache.
#Nous bloquons depuis deux heures. Nous avons regardé la DOC, suivis des tutos vidéos, mais les boutons ne fonctionnent pas.
#Solution : nous testions notre projet en version web au lieu de le tester sur un appareil android, la fonction $navigateTo(Page) ne fonctionne pas sur web.

#Aucun débug ou logcat disponible lors du lancement de l'application contrairement à Android Studio
#Solution : le logcat est dans la boite de commande