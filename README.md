# Born2beroot

## A faire

- [ ] Creer une VM Debian
- [ ] Creer 2 partitions chiffrees LVM (voir sujet)
- [ ] Service SSH actif sur port 4242
- [ ] Configurer pare-feu UFW (laisser port 4242 ouvert)
- [ ] Hostname = arazzok42
- [ ] Politique de mdp fort
- [ ] Installer et config sudo pratique stricte
- [ ] Mettre en place script monitoring.sh

### Politique de mdp fort

- [ ] Expire tous les 30j
- [ ] Modifiable tous les 2j
- [ ] Avertissement 7j avant expiration
- [ ] 10 char min, une maj et un chiffre, pas + de 3 char identiques consecutifs
- [ ] Ne comporte pas le nom du user
- [ ] 7 char pas dans l'ancien mdp (ne s'applique pas a root)
 
### Sudo pratique stricte

- [ ] Auth limitee a trois essais en cas de mdp errone
- [ ] Afficher un message en cas d'erreur suite a un mauvais mdp
- [ ] Garder logs toutes les actions sudo (inputs et outputs) dans /var/log/sudo
- [ ] Mode TTY active pour + de securite
- [ ] Limiter path utilisables par sudo (Exemple : /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin)

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

aptitude vs apt?
SELinux vs AppArmor?
SSH?
