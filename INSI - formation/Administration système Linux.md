installation de kali linux (Kali.org)
choix kali pour virtual box


## gestion des utilisateurs
sudo => miantso super-utilisateur (root)
```Bash
%% pour ajouter une utilisateur %%
sudo useradd [option] nom_utilisateur
```

exemple:
```Bash
sudo useradd hasina
```

création d'une repertoire dans /home

l'UID de l'utilisateur root est 0

base du commande linux : commande options argument

dans linux, toute est un repertoire


pour lancer une script ./script.sh


r=4; w=2 ; x=1 chmod 764 fichier.txt

proprietaire (u)
groupe (g)
autre (o)

chmod : change mode
chown : change owner
man: manuel


nom et mot de passe : kali



## 22/03//2025
chemin absolu toujour commencer par /
chemin relatif toujour commencer par le repertoire courant actuel

log c'est une historique des evenements

- linux sensible à la cache
- . est le répértoire actuel
- .. est le répértoire parent
- /dev (pour devices) contient le matériel (disques dur, processeur,...)

crée un utilisateur



afficher les utilisateur
```Bash
cat /etc/passwd %% affichier les utilisateur avec detail %%
cut -d: -f1 /etc/passwd %% afficher les utilisateur avec son nom seulement %%

```


donner un mot de passe pour l\'utilisateur
```Bash
sudo passwd <nom_utilisateur>
```

connecter avec l'utilisateur
```Bash
su - <nom_utilisateur>
```

voir le groupe ou l'utilisateur appartient
```Bash
groups <nom_utilisateur>
```

crée une group
```Bash
sudo groupadd nom_du_groupe
```

verification si le groupe est crée
```Bash
getent group nom_du_groupe

ou 

grep nom_du_groupe /etc/group

```

Ajouter un utilisateur à ce groupe :
```Bash
sudo usermod -aG <nom_groupe> <nom_utilisateur>
```

🧠 Remarques :

- `-aG` = ajoute (`-a`) l’utilisateur aux groupes listés (`-G`) sans supprimer les groupes existants.

vérification si l'utilisateur est bien ajouter dans le groupe
```Bash
groups nom_utilisateur
```

vérification si un utilisateur autre que root a été crée
```Bash
cat /etc/passwd | grep "/home"
```

se connecter à un utilisateur
```Bash
su - <nom_utilisateur>
```
il va te demander le mot de passe de l'utilisateur

création d'un dossier
```Bash
mkdir nom_dossier
```

lister les droits du dossier
```Bash
ls -l
```

change le droit du dossier
```Bash
chmod 644 nom_dossier
```
Remarque: 
- r=4 / w=2 / x=1 / 0 pour le pas de permission
- 6 = pour le droit du propriétaire (u)
- 4 = pour le droit du groupe (g)
- 4 = pour le droit des autre (o)

pour supprimer l'utilisateur
```Bash
sudo userdel -r etudiant1
```

pour supprimer un groupe
```Bash
sudo groupdel groupe_etudiants
```

email andefasana ilay devoir TP2
poonrhm@gmail.com 