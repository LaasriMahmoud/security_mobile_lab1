# 1. Importation de la VM
La première étape consiste à télécharger l'image au format .ova. Comme il s'agit d'une image disque complète, aucun aperçu n'est disponible directement dans le navigateur.

Fichier : Mobexler.ova prêt au téléchargement.
![Aperçu du téléchargement](./1.png)
# 2. Configuration Matérielle et Réseau
Une fois importée dans VirtualBox, la machine est configurée sur une base Debian (64-bit) avec les spécifications suivantes :

RAM : 4096 Mo

Processeurs : 2

Réseau : Double interface pour permettre à la fois l'accès internet et la communication avec l'hôte (essentiel pour ADB).

Détails de la configuration dans VirtualBox.
![Configuration VirtualBox](./2.png)
# 3. Premier Démarrage et Connexion
Au lancement, le système charge l'interface de connexion personnalisée de Mobexler.

Interface de login Mobexler "For Hackers by Hackers".
![Ecran de login Mobexler](./3.jpg)
# 4. Tests de Connectivité
Il est crucial de vérifier que la machine peut communiquer avec l'extérieur et avec la machine hôte.

Vérification de l'interface Hôte-Privé
Le ping vers 192.168.56.1 confirme que la VM voit bien la passerelle VirtualBox de l'hôte.
![Réseau host-only](./4.png)
Table de routage et DNS
La commande ip route montre que le trafic par défaut passe par l'interface NAT (10.0.2.2).
![ip route](./5.png)
Test Internet (ICMP & DNS)
Les tests de ping vers l'IP de Google (8.8.8.8) et le nom de domaine (google.com) valident la configuration DNS et l'accès au Web.
![test du NAT](./6.png)
# 5. Sauvegarde (Snapshot)
Après avoir validé que tout est fonctionnel (Réseau OK, Boot OK), un snapshot est créé. Cela permet de revenir à un état "propre" après des tests d'applications mobiles ou des manipulations système risquées.

Snapshot : CLEAN_BASELINE_TP1

![Création de snapshot](./8.png)
# 6. Détection de l'appareil de test intrusion (ADB)
La validation finale de l'environnement de laboratoire repose sur la capacité de la VM à communiquer avec le terminal mobile cible via le protocole ADB (Android Debug Bridge). En exécutant la commande adb devices, on confirme que l'appareil de test (ID 571290180411) est correctement attaché et reconnu par Mobexler. Cette étape est cruciale pour permettre l'installation d'outils d'instrumentation comme Frida, l'analyse des journaux système ou l'exécution de charges utiles directement sur le matériel de test lors d'un audit de sécurité.
![Validation ADB devices](./9.png)
