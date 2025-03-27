### 📌 **Comprendre le "Nombre de liens" (`1` dans `ls -l`)**

Dans la sortie de `ls -l`, **le deuxième champ numérique** correspond au **nombre de liens physiques** vers un fichier ou un dossier.

Exemple de sortie :

bash

CopierModifier

`-rw-r--r-- 1 roger gestion 0 Mar 25 20:26 test`

📌 **Le "1" ici signifie que le fichier `test` a un seul lien physique.**  
En d'autres termes, **aucun autre nom de fichier ne pointe vers ce fichier sur le disque**.

---

## 🔹 **Explication des liens en Linux**

### 📍 **1. Fichiers normaux : Un seul lien**

Quand tu crées un fichier, il a **un seul lien physique** par défaut, car il est référencé par un seul chemin.

Exemple :

bash

CopierModifier

`touch fichier.txt ls -l fichier.txt`

Résultat :

css

CopierModifier

`-rw-r--r-- 1 roger gestion 0 Mar 25 20:26 fichier.txt`

- **Le "1" signifie qu'il n'y a qu'un seul chemin vers ce fichier.**
    
- **Si on le supprime (`rm fichier.txt`), il disparaît.**
    

---

### 📍 **2. Liens physiques (hard links) : Plusieurs chemins vers le même fichier**

Si tu crées un **lien physique** (hard link), le compteur augmente car plusieurs fichiers pointent vers le même contenu.

Exemple :

bash

CopierModifier

`touch fichier.txt ln fichier.txt lien.txt ls -l fichier.txt lien.txt`

Résultat :

diff

CopierModifier

`-rw-r--r-- 2 roger gestion 0 Mar 25 20:26 fichier.txt -rw-r--r-- 2 roger gestion 0 Mar 25 20:26 lien.txt`

💡 **Le compteur est passé à `2` car `fichier.txt` et `lien.txt` sont deux noms pour le même fichier sur le disque.**  
Si tu supprimes `fichier.txt` (`rm fichier.txt`), **`lien.txt` existera toujours !**

---

### 📍 **3. Dossiers : Minimum 2 liens (ou plus)**

Un répertoire a **au minimum 2 liens** :

- Un vers **lui-même** (`.`).
    
- Un vers **son parent** (`..` dans le répertoire parent).
    

Exemple :

bash

CopierModifier

`mkdir mon_dossier ls -ld mon_dossier`