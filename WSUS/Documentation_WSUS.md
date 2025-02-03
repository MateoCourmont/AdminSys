## Documentation : Installation, ajout d'un client, préparation du déploiement de mise à jour

### 1️⃣ Installation du rôle WSUS

#### Étape 1 : Ouvrir le « Gestionnaire de serveur »

Dans un premier temps, ouvrez le **Gestionnaire de serveur**, puis cliquez sur **Gérer** et sélectionnez **Ajouter des rôles et fonctionnalités**.

![Étape 1](/WSUS/src/img/installation-wsus-windows-server-2022-01.png)

#### Étape 2 : Sélectionner les options d'installation

![Étape 2](/WSUS/src/img/installation-wsus-windows-server-2022-02.png)
![Étape 3](/WSUS/src/img/installation-wsus-windows-server-2022-03.png)
![Étape 4](/WSUS/src/img/installation-wsus-windows-server-2022-04.png)
![Étape 5](/WSUS/src/img/installation-wsus-windows-server-2022-05.png)
![Étape 6](/WSUS/src/img/installation-wsus-windows-server-2022-06.png)
![Étape 7](/WSUS/src/img/installation-wsus-windows-server-2022-07.png)
![Étape 8](/WSUS/src/img/installation-wsus-windows-server-2022-08.png)
![Étape 9](/WSUS/src/img/installation-wsus-windows-server-2022-09.png)
![Étape 10](/WSUS/src/img/installation-wsus-windows-server-2022-10.png)

#### Vérification de l'installation

Une fois l'installation terminée, vous pouvez vérifier l'état via le **dashboard**.

![Dashboard](/WSUS/src/img/Capture%20d'écran%202025-02-03%20104632.png)

---

### 2️⃣ Configuration de base de WSUS

#### Lancer la console « Services WSUS »

Une fois WSUS installé, ouvrez la console **Services WSUS** pour effectuer la configuration initiale.

![Console WSUS](/WSUS/src/img/installation-wsus-windows-server-2022-19.png)

#### Choisir l'option appropriée

Sélectionnez la première option, car la deuxième est uniquement disponible pour une architecture WSUS multi-serveurs.

![Option sélectionnée](/WSUS/src/img/installation-wsus-windows-server-2022-21.png)

#### Configuration du proxy

Si vous n'utilisez pas de proxy, cliquez sur **Suivant**.

![Pas de proxy](/WSUS/src/img/installation-wsus-windows-server-2022-22.png)

#### Connexion aux serveurs Microsoft Update

Cliquez sur **Start Connecting** pour que WSUS se connecte aux serveurs Microsoft Update et récupère les informations nécessaires.

![Connexion](/WSUS/src/img/installation-wsus-windows-server-2022-23.png)

#### Sélection des langues de mise à jour

Choisissez les langues des mises à jour en fonction de votre environnement. Ici, nous sélectionnons l'anglais pour le serveur et le français pour les clients.

![Langues](/WSUS/src/img/installation-wsus-windows-server-2022-24.png)

#### Sélection des produits

Sélectionnez les produits pour lesquels vous souhaitez synchroniser les mises à jour. Ici, nous choisissons **Windows Server 2019** et **Windows 10/11**.

![Produits](/WSUS/src/img/installation-wsus-windows-server-2022-25.png)
![Suite des produits](/WSUS/src/img/installation-wsus-windows-server-2022-26.png)

#### Choix des classifications de mises à jour

Sélectionnez les types de mises à jour à synchroniser, comme les mises à jour critiques, de sécurité, et les mises à jour de définitions pour Windows Defender.

![Classifications](/WSUS/src/img/installation-wsus-windows-server-2022-27.png)

#### Planification de la synchronisation

Programmez la synchronisation pour qu'elle se fasse pendant la nuit afin d'éviter de surcharger la bande passante durant les heures de travail.

![Planification](/WSUS/src/img/installation-wsus-windows-server-2022-28.png)

#### Lancer la première synchronisation

Enfin, cochez l'option **Begin initial synchronization** pour effectuer la première synchronisation avec Microsoft Update.

![Synchronisation](/WSUS/src/img/installation-wsus-windows-server-2022-29.png)

---

### 3️⃣ Configuration des clients (via GPO)

#### Création de la GPO WSUS_Config

Créez une **GPO** appelée `WSUS_Config` et éditez-la via :

- **Configuration ordinateur** > **Modèles d'administration** > **Composants Windows** > **Windows Update**

#### Configuration des paramètres WSUS

1. **Spécifier l'emplacement du service Microsoft Update sur intranet** <br>
   ![Emplacement WSUS](/WSUS/src/img/Capture%20d'écran%202025-02-03%20120520.png)

2. **Configurer les mises à jour automatiques** <br>
   ![Mises à jour automatiques](/WSUS/src/img/Capture%20d'écran%202025-02-03%20115148.png)

3. **Définir la fréquence de détection des mises à jour** <br>
   ![Fréquence de détection](/WSUS/src/img/Capture%20d'écran%202025-02-03%20115515.png)

---

### Vérification des paramètres WSUS via GPO

Enfin, vérifiez que les paramètres WSUS sont bien appliqués via les stratégies de groupe (GPO).

Commande sur le serveur :

![Vérification GPO](/WSUS/src/img/Capture%20d'écran%202025-02-03%20133122.png)

Commande sur le PC :

![Vérification GPO2](/WSUS/src/img/Capture%20d'écran%202025-02-03%20134830.png)
