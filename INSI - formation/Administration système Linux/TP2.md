1- Créer deux groupes nommés respectivement gestion et informatique 
2- Créer les utilisateurs suivants : roger, mickael, paul, yvon, achille, nasser et arnaud. Le mot de passe de chaque utilisateur portera son nom
3- Ajouter chaque utilisateur dans un groupe 
a) gestion : roger, mickael, paul 
b) informatique : yvon, achille, nasser et arnaud

**Réponses :**

création de fichier user_list.txt

```Bash
vim user_list.txt
```

```
roger:gestion
mickael:gestion
paul:gestion
yvon:informatique
achille:informatique
nasser:informatique
arnaud:informatique
```

création de script create_user.sh pour la création du nom, mot de passe et attribution de groupe
```Bash
Vim create_user.sh
```

```Bash
#!/bin/bash

# Vérifier si un fichier contenant la liste des utilisateurs est fourni
if [ -z "$1" ]; then
    echo "Usage: $0 <fichier_utilisateurs>"
    exit 1
fi

FILE="$1"

# Vérifier si le fichier existe
if [ ! -f "$FILE" ]; then
    echo "Erreur : Fichier $FILE introuvable."
    exit 1
fi

echo "Lecture du fichier : $FILE"

# Lire chaque ligne du fichier et créer les utilisateurs
while IFS=":" read -r user group; do
    if [ -z "$user" ] || [ -z "$group" ]; then
        echo "Ligne ignorée (format incorrect) : $user:$group"
        continue
    fi

    # Vérifier si le groupe existe, sinon le créer
    if ! grep -q "^$group:" /etc/group; then
        echo "Création du groupe $group..."
        sudo groupadd "$group"
    fi

    # Vérifier si l'utilisateur existe déjà
    if id "$user" &>/dev/null; then
        echo "L'utilisateur $user existe déjà, aucune action nécessaire."
    else
        # Créer l'utilisateur avec son groupe
        sudo useradd -m -g "$group" "$user"
        echo "$user:$user" | sudo chpasswd  # Définir le mot de passe identique au nom d'utilisateur
        echo "Utilisateur $user ajouté au groupe $group."
    fi
done < "$FILE"

echo "Création des utilisateurs terminée !"

```

rendre le script exécutable
```Bash
chmod +x create_users.sh
```

exécution du script
```Bash
./create_users.sh users_list.txt
```

resultat après execution
```Bash
Lecture du fichier : user_list.txt
Création du groupe gestion...
Utilisateur roger ajouté au groupe gestion.
Utilisateur mickael ajouté au groupe gestion.
Utilisateur paul ajouté au groupe gestion.
Création du groupe informatique...
Utilisateur yvon ajouté au groupe informatique.
Utilisateur achille ajouté au groupe informatique.
Utilisateur nasser ajouté au groupe informatique.
Utilisateur arnaud ajouté au groupe informatique.
Ligne ignorée (format incorrect) : :
Création des utilisateurs terminée !
```

**Fin de la réponse 1 / 2 / 3**


4- Connectez-vous sur le compte de roger
```Bash
su - roger
```

5- Créer dans son répertoire personnel un dossier appelé document
```Bash
mkdir document
```

6- Créer dans document le dossier cours et le fichier test
```Bash
mkdir -p document/cours
touch document/test
```

7- Lister de façon détaillé le contenu du dossier document. Interpréter les résultats
```Bash
ls -l document
total 4
drwxr-xr-x 2 roger gestion 4096 Mar 25 20:24 cours
-rw-r--r-- 1 roger gestion    0 Mar 25 20:26 test
```
Interprétation
**1️⃣ `total 4`**
- Cela signifie que le dossier `document` utilise 4 Ko.

**2️⃣ `drwxr-xr-x 2 roger gestion 4096 Mar 25 20:24 cours`**
- **`d`** → C'est un **répertoire** (`cours`).
- **`rwxr-xr-x`** → Permissions du répertoire :
    - **`rwx` (7)** → **Propriétaire (`roger`)** a les permissions **lecture (`r`), écriture (`w`), exécution (`x`)**.
    - **`r-x` (5)** → **Groupe (`gestion`)** peut **lire (`r`) et exécuter (`x`)**, mais **pas écrire**.
    - **`r-x` (5)** → **Autres utilisateurs** peuvent **lire (`r`) et exécuter (`x`)**, mais **pas écrire**
- **`2`** → Nombre de liens (normalement `.` et `..`).
- **`roger`** → Propriétaire du dossier (`cours`).
- **`gestion`** → Groupe auquel appartient le dossier (`cours`).
- **`4096`** → Taille du dossier (`4 Ko`).
- **`Mar 25 20:24`** → Date et heure de la dernière modification.
- **`cours`** → Nom du répertoire.

**3️⃣ `-rw-r--r-- 1 roger gestion 0 Mar 25 20:26 test`**
- **`-`** → C'est un **fichier** (pas un dossier).
- **`rw-r--r--`** → Permissions du fichier :
    - **`rw-` (6)** → **Propriétaire (`roger`)** peut **lire (`r`) et écrire (`w`)**, mais **pas exécuter** (`-`).
    - **`r--` (4)** → **Groupe (`gestion`)** peut **seulement lire (`r`)**.
    - **`r--` (4)** → **Autres utilisateurs** peuvent **seulement lire (`r`)**.
- **`1`** → Nombre de liens (fichiers normaux ont `1`).
- **`roger`** → Propriétaire du fichier (`test`).
- **`gestion`** → Groupe du fichier (`test`).
- **`0`** → Taille du fichier (`0` octets, donc vide).
- **`Mar 25 20:26`** → Date et heure de la dernière modification.
- **`test`** → Nom du fichier.

8- Quel est la commande utilisée pour modifier les droits d’un utilisateur sur un fichier
```Bash
chmod
```

9- Quelles sont les commandes utilisées pour respectivement modifier le propriétaire d’un fichier et son groupe propriétaire
```Bash
chown #change le proprietaite
chgrp #change le groupe proprietaire
```

10- Modifier le groupe propriétaire du dossier cours et du fichier test. Le nouveau groupe sera gestion
d'après la sortie de `ls -l document, le dossier` cours ` et le fichier ` test` appartiennent déjà au groupe `gestion`

11- Modifier les droits des utilisateurs sur le dossier cours et le fichier test de telle façon que : 
a) Le propriétaire ait les droits de lecture, d’écriture et d’exécution sur ces fichiers
b) Le groupes propriétaires ait uniquement les droits de lecture et d’exécution
c) Les autres utilisateurs n’aient aucun droit sur ces fichiers
```Bash
chmod 750 document/cours
chmod 750 document/test
```

12- Utilisez les utilisateurs mickael et yvon pour tester le bon fonctionnement de la configuration.
```Bash
sudo chmod 750 /home/roger/ #entant que administrateur
└─$ su - mickael
Password:
┏━(Message from Kali developers)
┃
┃ This is a minimal installation of Kali Linux, you likely
┃ want to install supplementary tools. Learn how:
┃ ⇒ https://www.kali.org/docs/troubleshooting/common-minimum-setup/
┃
┗━(Run: “touch ~/.hushlogin” to hide this message)
$ cd /home/roger
$ ls
document
$ cd document/cours
$ ls
$ touch fichier.txt
touch: cannot touch 'fichier.txt': Permission denied
```
`yvon`  **ne peut rien faire**.

13- L’utilisateur achille peut-il supprimer le fichier test ? Justifier votre réponse
vérifier la permission du fichier test et le groupe d'achille
```Bash
ls -l /home/roger/document/test
-rwxr-x--- 1 roger gestion 0 Mar 25 20:26 test

groups achille
achille : informatique
```
Achille fait partie du groupe `informatique`, donc il ne peut PAS le modifier ni le supprimer.

14- Que peut faire l’utilisateur Paul sur ce fichier ?
vérifier le group de Paul
```Bash
groups paul
achille : gestion
```
Pau peut lire et executer

15- Que fait les commandes chmod 777 cours et chmod 654 test ?
```Bash
chmod 777 
```

|Catégorie|Valeur `7` (rwx)|Signification|
|---|---|---|
|**Propriétaire**|`rwx`|Peut lire (`r`), écrire (`w`), exécuter (`x`)|
|**Groupe**|`rwx`|Peut lire, écrire, exécuter|
|**Autres (tout le monde)**|`rwx`|Peut lire, écrire, exécuter|

```Bash
chmod 654
```

|Catégorie|Valeur|Signification|
|---|---|---|
|**Propriétaire**|`6` (`rw-`)|Peut lire (`r`), écrire (`w`), mais pas exécuter (`-`)|
|**Groupe**|`5` (`r-x`)|Peut lire (`r`), exécuter (`x`), mais pas écrire (`-`)|
|**Autres**|`4` (`r--`)|Peut seulement lire (`r--`)|


16 – Connectez-vous avec l’utilisateur nasser et utilisez la commande echo pour écrire la phrase suivante dans le fichier test : « Je vais réussir ». Commentez les résultats

```Bash
sudo chmod 777 /home/roger/document/
su - nasser
echo "Je vais réussir" > /home/roger/document/test
-sh: 1: cannot create /home/roger/document/test: Permission denied
```

17- Modifier les groupes principaux de chaque utilisateur conformément à la question 3 : les utilisateurs du groupe gestion doivent désormais appartenir au groupe informatique et ceux du groupe informatique au groupe gestion. 
```Bash
cat /etc/group | grep -E "gestion|informatique" #verification de groupe de chaque utilisateur

sudo usermod -g informatique roger
sudo usermod -g informatique mickael
sudo usermod -g informatique paul

sudo usermod -g gestion yvon
sudo usermod -g gestion achille
sudo usermod -g gestion nasser
sudo usermod -g gestion arnaud
```

18- Modifier le propriétaire du fichier test. Le nouveau propriétaire s’appelle yvon 
```Bash
sudo chown yvon /home/roger/document/test
```

19- Créer dans votre répertoire personnel un fichier nommé exemple dans Documents 
```Bash
su - yvon
touch documents/exemple
```


20- Faites en sorte que le propriétaire de ce fichier soit arnaud et son groupe propriétaire soit gestion
```Bash
sudo chown arnaud:gestion ~/Documents/exemple
```