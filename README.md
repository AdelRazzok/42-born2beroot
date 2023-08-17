# Born2beroot

## A faire

- [x] Creer une VM Debian
- [x] Creer 2 partitions chiffrees LVM (voir sujet)
- [x] Service SSH actif sur port 4242
- [ ] Configurer pare-feu UFW (laisser port 4242 ouvert)
- [x] Hostname = arazzok42
- [ ] Politique de mdp fort
- [x] Installer et config sudo pratique stricte
- [ ] Mettre en place script monitoring.sh

### Politique de mdp fort

- [ ] Expire tous les 30j
- [ ] Modifiable tous les 2j
- [ ] Avertissement 7j avant expiration
- [ ] 10 char min, une maj et un chiffre, pas + de 3 char identiques consecutifs
- [ ] Ne comporte pas le nom du user
- [ ] 7 char pas dans l'ancien mdp (ne s'applique pas a root)
 
### Sudo pratique stricte

- [x] Auth limitee a trois essais en cas de mdp errone
- [x] Afficher un message en cas d'erreur suite a un mauvais mdp
- [x] Garder logs toutes les actions sudo (inputs et outputs) dans /var/log/sudo
- [x] Mode TTY active pour + de securite
- [x] Limiter path utilisables par sudo (Exemple : /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin)

### Apres la mise en place des fichiers config

- [ ] Changer les mdp de tous les comptes (root inclus)

### monitoring.sh

Dès le lancement de votre serveur, le script écrira des informations toutes les 10 minutes sur tous les terminaux (jetez un oeil du côté de wall). La bannière est facultative. À aucun moment la moindre erreur ne doit être visible.

Le script doit afficher les infos suivantes :

- [ ] OS archi et version kernel
- [ ] Nombre processeurs physiques
- [ ] Nombre processeurs virtuels
- [ ] Memoire vive dispo et taux utilisation (en %)
- [ ] Memoire dispo et taux utilisation (en %)
- [ ] Taux utilisation actuel processeurs (en %)
- [ ] Date et heure dernier redemarrage
- [ ] Etat LVM
- [ ] Nombre connexion actives
- [ ] Nombre utilisateurs
- [ ] Adresse IPv4 et adresse MAC
- [ ] Nombre commandes executees avec sudo

Durant la soutenance, vous serez amené(e) à expliquer le fonctionnement de ce script et à interrompre son exécution sans le modifier. Regardez du côté de cron.

## Q&A

### Aptitude vs apt :

Dans une distribution basee sur Debian, le package manager de base est dpkg. Cet outil nous permet d'installer, de supprimer et de gerer des programmes sur notre OS.

Ces programmes sont souvent accompagnes de dependances vitales pour leur fonctionnement qu'il est possible de les installer manuellement.

Pour des raisons evidentes, nous prefererons utiliser un outil comme APT (Advanced Package Transfer) qui utilise dpkg et permet d'installer toutes les dependances dont le programme a besoin au moment de l'installation de ce dernier.

On peut maintnant installer des programmes avec une seule commande, en utilisant les services d'apt (apt-get, apt-cache...).

Dans le cas on nous voudrions utiliser une interface graphique, il faudrait alors utiliser aptitude.
Aptitude permet egalement un meilleur controle des dependances : il donne la possibilite de choisir les dependances a l'installation du programme.

### SELinux :

SELinux (Security-Enhanced Linux) est une architecture de securite pour systemes Linux qui permet aux administrateurs de mieux controller l'acces au systeme.

Il definit les controles d'acces pour les applications, processus, et fichiers d'un systeme en utilisants des politiques de securite (ensembles de regles) qui lui indiquent ce a quoi un utilisateur peut acceder on non.

Il existe differentes facons de configurer SELinux pour proteger un systeme : la politique ciblee et la politique de securite a plusieurs niveaux (MLS) sont les methodes les plus couramment utilisees.

La politique ciblee est l'option par defaut car elle couvre un certain nombre de processus, taches et services. La politique MLS peut etre tres complexe, elle est donc generalement utilisee uniquement par les organismes gouvernementaux.

Pour consulter la liste des processus qui doivent s'executer sur un système, il suffit d'ouvrir le fichier /etc/sysconfig/selinux.

Ce fichier comprend une section qui indique le mode de SELinux :
- Permissive (permissif)
- Enforcing (applique)
- Disabled (désactivé)
Le type de politique qui devrait être chargée est également indiqué.

### AppArmor :

AppArmor est logiciel de securite pour Linux. Il permet a l'administrateur d'attribuer des profils de securite a chaque programme, ce qui limite leurs acces au systeme d'exploitation.

### UFW :

UFW (Uncomplicated Firewall) est un logiciel qui permet a l'administrateur de gerer iptables simplement.

Etant donne qu'il est difficile de travailler directement avec iptables, UFW nous fournit une interface pour modifier le firewall (netfilter) sans compromettre la securite. 

Une fois UFW installe, nous pouvons choisir sur quels ports autoriser la connexion et les quels fermer, ce qui nous sera tres utile avec SSH.

### cron :

cron (chrono table -> crontable -> cron) est un programme qui premet aux utilisateurs Unix d'executer automatiquement des scripts, des commandes ou des logiciels a une date et a une heure (ou a un cycle) specifiee a l'avance.

### wall :

wall (write all) est une commande qui permet d'envoyer un message sur les terminaux de tous les utilisateurs connectes.
