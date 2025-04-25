# TrueNas-Scale

🚀 Projet : Installation de TrueNAS SCALE et tests de services
🖥️ Machines Virtuelles
💾 VM 1 : TrueNAS SCALE
2 cœurs, 4 Go de RAM

2 disques de 16 Go (système)

5 disques de 2 To configurés en RAID 6 ➜ stockage nommé "Stockage"

🧪 VM 2 : Debian avec interface graphique
2 cœurs, 2 Go de RAM

1 disque de 8 Go

⚙️ 1. Configuration de TrueNAS SCALE
🔧 Installation
Créer une VM en mode "Custom"

Choisir : I will install the operating system later

Système invité : Linux ➜ Debian 12.x 64-bit

Configurer : 1 processeur, 2 cœurs, 4 Go RAM, 2 disques de 16 Go, 5 disques de 2 To

Lancer l'installation avec l'ISO TrueNAS SCALE :
👉 Téléchargement

Suivre les étapes :
➜ Sélectionner le disque sda VMware Virtual -- 16 GiB
➜ Définir l’utilisateur et mot de passe (ex: truenas_admin)
➜ Redémarrer à la fin de l’installation

✅ Une fois la VM relancée, noter l’adresse IP affichée pour accéder à l’interface web : https://<IP>

🌐 Mise en service
Se connecter à l'interface TrueNAS via le navigateur

Passer l'interface en français :
Système → Paramètres généraux → Localisation → Modifier

🛠️ Création du RAID 6
Stockage → Créer un volume

Nommer : Stockage

Choisir le layout RAIDZ2

Sélectionner les 5 disques de 2 To

Créer le volume

✅ RAID 6 créé avec succès !

🔐 2. Connexions SSH & SFTP
👤 Création d’utilisateurs
Identifiants → Utilisateurs → Ajouter

Configurer un utilisateur

Cocher : ✅ Connexion SSH par mot de passe activée

🚪 Activer les services
Système → Services → Activer SSH

🔗 Connexion via terminal

ssh nom_utilisateur@adresse_IP
sftp nom_utilisateur@adresse_IP
✅ Connexions SSH & SFTP réussies !

🔁 Modification du port SSH
Système → Services → SSH → Modifier

Changer le port (ex : 2222)

Enregistrer

🔗 Connexion avec port personnalisé

ssh -p 2222 nom_utilisateur@adresse_IP
sftp -P 2222 nom_utilisateur@adresse_IP
✅ Connexions SSH & SFTP validées sur port personnalisé !

📁 3. Création d’un dossier Public
Stockage → Ajouter un Dataset

Nommer : Public

Configurer les autorisations :
Autorisations → Modifier → Options avancées → Définir les ACL

✅ Dossier public créé avec permissions correctes !

🧪 4. Tests depuis la deuxième VM
Connexion en SFTP avec client graphique

Test des connexions : HTTPS, SSH, SFTP

✅ Tous les services fonctionnent depuis la VM Debian 🎉

🚀 Pour aller plus loin
🔐 Installer Vaultwarden (Docker)
Créer un nouveau dataset pour l’app :

Stockage → Créer un volume → Nom : Appli

Rechercher et installer Vaultwarden :

Applications → Recherche : Vaultwarden

Configurer :

Volume : Appli

Définir un mot de passe base de données

Définir un Admin Token

Lancer l’installation

✅ Vaultwarden installé et fonctionnel !

ℹ️ Qu’est-ce que TrueNAS SCALE ?
TrueNAS SCALE est un système d’exploitation open source basé sur Debian Linux, développé par iXsystems, conçu pour gérer le stockage en réseau (NAS).

⭐ Principales fonctionnalités :
📦 ZFS intégré : protection avancée des données

🧩 Support de la virtualisation et conteneurisation (VMs & Docker/Kubernetes)

📈 Évolutivité : gestion de clusters

🔁 Protocoles multiples : SMB, NFS, iSCSI, etc.

🌐 Interface Web simple et intuitive

🆚 Une alternative puissante aux NAS commerciaux, 100% open source 💚
