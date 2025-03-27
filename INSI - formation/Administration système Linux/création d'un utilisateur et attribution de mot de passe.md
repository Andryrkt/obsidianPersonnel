lien pour lister les utilisateur existant [[liste les utilisateurs]]
## crée un utilisateur avec répertoire et shell 
```Bash
sudo adduser <nom_utilisateur>
```
la commande crée automatiquement:
- le répertoire /home/<nom_utilisateur>
- les fichier de configuration par défaut (.bashrc, .profile,etc.)

## crée un utilisateur sans répertoire et shell
```Bash
%% pour ajouter une utilisateur %%
sudo useradd [option] nom_utilisateur
```

exemple:
```Bash
sudo useradd hasina
```

Remarque : 
- ce commande ne crée pas un répertoire (/home/<nom_utilisateur>) et n'attribue pas une shell pour l'utilisateur
- un shell permet à l'utilisateur d'utiliser des ligne de commande

pour crée un répertoire pour l'utilisateur, il faut utiliser la commende suivant:
```Bash
sudo mkdir /home/<nom_utilisateur>
sudo chown lui:nous /home/etudiant1 
%% hange le propriétaire en lui et le groupe propriétaire en nous du répertoire /home/etudiant1%%
```

## crée un utilisateur avec répertoire et shell avec une seul ligne de code

```Bash
sudo useradd -m -s /bin/bash etudiant1
```

- -m = crée le dossier /home/etudiant1
- -s /bin/bash = attribue un shell

## attribution de mot de passe
donner un mot de passe pour l\'utilisateur
```Bash
sudo passwd <nom_utilisateur>
```

## modification (mise à jour )nom et mot de passe d'un ou plusieurs utilisateur

**mettre à jour les mots de passe des utilisateurs en masse**.
### **Syntaxe de base**
```Bash
echo "nom_utilisateur:mot_de_passe" | sudo chpasswd
```
- `nom_utilisateur` → Le nom de l'utilisateur à modifier.
- `mot_de_passe` → Le nouveau mot de passe attribué.
- `|` (pipe) → Envoie la sortie de `echo` comme entrée de `chpasswd`. voire  [[symbole]]
- `sudo` → Requis car **changer un mot de passe nécessite les droits root**.