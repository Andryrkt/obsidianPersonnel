## **🔹 Commande `chmod` : Modifier les permissions d'un fichier**

Syntaxe :
```Bash
chmod [options] mode fichier
```

Où **`mode`** représente les nouvelles permissions.

---

### **🔍 Exemple : Modifier les droits pour un utilisateur spécifique**

#### ✅ **Donner au propriétaire (`user`) tous les droits (`rwx`)**
```Bash
chmod u+rwx fichier.txt
```


➡ **Signification** :

- `u` = **user** (propriétaire).
    
- `+rwx` = **ajoute lecture (`r`), écriture (`w`), exécution (`x`)**.
    

---

#### ✅ **Retirer les droits d'écriture au propriétaire**

bash

CopierModifier

`chmod u-w fichier.txt`

➡ **Le propriétaire pourra seulement lire et exécuter le fichier, mais pas le modifier.**

---

#### ✅ **Donner les droits d'exécution (`x`) à tout le monde**

bash

CopierModifier

`chmod a+x fichier.txt`

➡ **`a` signifie "all" (tous les utilisateurs)**.

---

### **📍 Modifier les permissions avec une notation numérique**

Tu peux aussi utiliser la notation **octale** :

bash

CopierModifier

`chmod 755 fichier.txt`

➡ **Signification** :

- `7` (propriétaire) = **lecture (`r`) + écriture (`w`) + exécution (`x`)**.
    
- `5` (groupe) = **lecture (`r`) + exécution (`x`)**.
    
- `5` (autres) = **lecture (`r`) + exécution (`x`)**.
    

---

## **🔹 Commande `chown` : Modifier le propriétaire d'un fichier**

Si tu veux **changer le propriétaire du fichier**, utilise **`chown`** :

bash

CopierModifier

`sudo chown nouvel_utilisateur fichier.txt`

Exemple :

bash

CopierModifier

`sudo chown roger fichier.txt`

➡ Le fichier **appartient maintenant à `roger`**.

Si tu veux changer **le propriétaire et le groupe** :

bash

CopierModifier

`sudo chown roger:gestion fichier.txt`

➡ **Le fichier appartient maintenant à `roger` et au groupe `gestion`**.

---

### **✅ Résumé**

|Commande|Action|
|---|---|
|`chmod u+rwx fichier.txt`|Donne tous les droits au propriétaire|
|`chmod 755 fichier.txt`|Donne `rwx` au propriétaire, `rx` au groupe et aux autres|
|`chmod a+x fichier.txt`|Permet à tout le monde d'exécuter le fichier|
|`sudo chown roger fichier.txt`|Change le propriétaire du fichier en `roger`|
|`sudo chown roger:gestion fichier.txt`|Change le propriétaire et le groupe|


### **📌 Commandes pour modifier le propriétaire et le groupe propriétaire d'un fichier sous Linux**

Les commandes utilisées sont **`chown`** et **`chgrp`**.

---

## **🔹 1️⃣ Modifier le propriétaire d’un fichier**

La commande **`chown`** permet de modifier le **propriétaire** d’un fichier.

### **✅ Modifier uniquement le propriétaire**

bash

CopierModifier

`sudo chown nouvel_utilisateur fichier.txt`

🔹 **Exemple :**

bash

CopierModifier

`sudo chown roger fichier.txt`

➡ Le fichier **`fichier.txt`** appartient maintenant à l'utilisateur **`roger`**.

---

## **🔹 2️⃣ Modifier le groupe propriétaire d’un fichier**

La commande **`chgrp`** permet de modifier **seulement** le groupe propriétaire.

### **✅ Modifier uniquement le groupe propriétaire**

bash

CopierModifier

`sudo chgrp nouveau_groupe fichier.txt`

🔹 **Exemple :**

bash

CopierModifier

`sudo chgrp gestion fichier.txt`

➡ Le fichier **`fichier.txt`** appartient maintenant au groupe **`gestion`**.

---

## **🔹 3️⃣ Modifier à la fois le propriétaire et le groupe propriétaire**

Tu peux modifier les **deux en même temps** avec `chown` en utilisant la syntaxe :

bash

CopierModifier

`sudo chown nouvel_utilisateur:nouveau_groupe fichier.txt`

🔹 **Exemple :**

bash

CopierModifier

`sudo chown roger:gestion fichier.txt`

➡ Maintenant, **le propriétaire est `roger` et le groupe est `gestion`**.

---

### **📌 Vérifier les changements**

Après avoir exécuté `chown` ou `chgrp`, vérifie les nouvelles permissions avec :

bash

CopierModifier

`ls -l fichier.txt`

🔹 **Exemple de sortie avant modification :**

css

CopierModifier

`-rw-r--r-- 1 hasina hasinaltn 0 Mar 25 20:30 fichier.txt`

🔹 **Après `sudo chown roger:gestion fichier.txt` :**

css

CopierModifier

`-rw-r--r-- 1 roger gestion 0 Mar 25 20:30 fichier.txt`

➡ **Le propriétaire est `roger` et le groupe `gestion`**.

---

### **✅ Résumé des commandes**

|Commande|Action|
|---|---|
|`sudo chown roger fichier.txt`|Change le propriétaire en `roger`|
|`sudo chgrp gestion fichier.txt`|Change le groupe propriétaire en `gestion`|
|`sudo chown roger:gestion fichier.txt`|Change le propriétaire en `roger` et le groupe en `gestion`|