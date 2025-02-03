## Documentation : Installation, ajout d'un client, préparation du déploiement de mise à jour.

### 1️⃣ Installation du rôle WSUS.

Dans un premier temps, ouvrir le « Gestionnaire de serveur », cliquer sur « Gérer » puis « Ajouter des rôles et fonctionnalités ».

![Image1](/WSUS/src/img/installation-wsus-windows-server-2022-01.png)
![Image2](/WSUS/src/img/installation-wsus-windows-server-2022-02.png)
![Image3](/WSUS/src/img/installation-wsus-windows-server-2022-03.png)
![Image4](/WSUS/src/img/installation-wsus-windows-server-2022-04.png)
![Image5](/WSUS/src/img/installation-wsus-windows-server-2022-05.png)
![Image6](/WSUS/src/img/installation-wsus-windows-server-2022-06.png)
![Image7](/WSUS/src/img/installation-wsus-windows-server-2022-07.png)
![Image8](/WSUS/src/img/installation-wsus-windows-server-2022-08.png)
![Image9](/WSUS/src/img/installation-wsus-windows-server-2022-09.png)
![Image10](/WSUS/src/img/installation-wsus-windows-server-2022-10.png)
![Image11](/WSUS/src/img/installation-wsus-windows-server-2022-16.png)

On peut vérifier que l'installation est terminée en regardant le dashboard.

![Image12](/WSUS/src/img/Capture%20d'écran%202025-02-03%20104632.png)

### 2️⃣ Configuration de base de WSUS.

WSUS est installé sur notre serveur, lancer la console « Services WSUS » pour effectuer la configuration de base.

![Image13](/WSUS/src/img/installation-wsus-windows-server-2022-19.png)

Ici on sélectionne la première option car la deuxième option n'est possible que dans le cas d'une architecture avec pusieurs serveurs WSUS :

![Image14](/WSUS/src/img/installation-wsus-windows-server-2022-21.png)

Ici on n'utilise pas de proxy, alors il suffit de cliquer uniquement sur suivant :

![Image15](/WSUS/src/img/installation-wsus-windows-server-2022-22.png)

Ensuite, cliquer sur « Start Connecting » pour que le serveur WSUS se connecte sur les serveurs Microsoft Update et récupère la liste des OS et logiciels pris en charge, les types de mises à jour, et les langages disponibles. Une fois la barre de progression pleine cliquer sur « Next ».

![Image16](/WSUS/src/img/installation-wsus-windows-server-2022-23.png)

La prochaine étape est le choix des langues de mise à jour. Comme on utilise les serveurs en anglais et les clients en français, choisir les deux langues.

![Image17](/WSUS/src/img/installation-wsus-windows-server-2022-24.png)

La prochine étape consiste à sélectionner les produits pour lesquels nous voulons synchroniser les maj (Exchange, Office, Edge etc…). Ici on selectionne uniquement Windows Server 2019 et Windows 10/11. La séléction est modifiable à tout moment.

![Image18](/WSUS/src/img/installation-wsus-windows-server-2022-25.png)
![Image19](/WSUS/src/img/installation-wsus-windows-server-2022-26.png)

L’étape suivante concerne la classification des mises à jour, les types de mises à jour qu’il faut synchroniser sur le serveur.

- « Mises à jour critique », « Mise à jour de la sécurité » et « Mise à jour » : maj mensuelles publiées par Microsoft
- « Mises à jour de définitions » : maj Windows Defender.
- « Upgrades » : mises à niveau de windows

![Image20](/WSUS/src/img/installation-wsus-windows-server-2022-27.png)

Ensuite, il faut synchroniser les maj avec les serveurs Microsoft Update et les planifier pour recevoir les dernières maj. Ici on planifie la nuit pour ne pas surcharger la bande passante pendant les heures de travail

![Image21](/WSUS/src/img/installation-wsus-windows-server-2022-28.png)

Enfin il faut cocher « Begin initial synchronization » pour réaliser une première synchronisation.

![Image22](/WSUS/src/img/installation-wsus-windows-server-2022-29.png)

### 3️⃣ Configuration des clients (via GPO).

Création d'une GPO WSUS_Config

Editer la GPO via :

- Configuration ordinateur > Modèles d'administration > Composants Windows > Windows Update

#### Configuration des paramètres WSUS

1. Spécifier l'emplacement du service Microsoft Update sur intranet

![Image23](/WSUS/src/img/Capture%20d'écran%202025-02-03%20120520.png)

2. Configurer les mises à jour automatiques

![Image23](/WSUS/src/img/Capture%20d'écran%202025-02-03%20115148.png)

3. Définir la fréquence de détection des mises à jour

![Image23](/WSUS/src/img/Capture%20d'écran%202025-02-03%20115515.png)
