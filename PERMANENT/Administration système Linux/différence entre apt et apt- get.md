Sur les systèmes Linux basés sur **Debian** (comme Ubuntu), **`apt`** et **`apt-get`** sont deux outils de gestion de paquets, mais ils ont des différences importantes :

### 🔹 **1. `apt-get` (ancien outil)**

- Fait partie du système **APT** (_Advanced Package Tool_).
    
- Principalement conçu pour les scripts et les opérations bas niveau.
    
- Nécessite souvent l'utilisation d'autres outils comme `apt-cache` pour certaines tâches.
    
- **Commandes courantes :**
    ```Bash
    sudo apt-get update          # Met à jour la liste des paquets
    sudo apt-get upgrade         # Met à jour les paquets installés
    sudo apt-get install <pkg>   # Installe un paquet
    sudo apt-get remove <pkg>    # Désinstalle un paquet (mais garde les fichiers de config)
    sudo apt-get purge <pkg>     # Désinstalle complètement (fichiers de config inclus)
```
    
    

### 🔹 **2. `apt` (version moderne et conviviale)**

- Introduit pour simplifier l'expérience utilisateur.
    
- Combine les fonctionnalités de `apt-get`, `apt-cache`, etc., dans un seul outil.
    
- Affiche une **barre de progression** et des **informations colorées**.
    
- **Commandes courantes :**
    ```Bash
    sudo apt update              # Met à jour la liste des paquets
    sudo apt upgrade             # Met à jour les paquets installés
    sudo apt install <pkg>       # Installe un paquet
    sudo apt remove <pkg>        # Désinstalle un paquet
    sudo apt purge <pkg>         # Désinstalle complètement
    sudo apt autoremove          # Supprime les paquets inutiles
    sudo apt search <mot-clé>    # Recherche un paquet
    sudo apt show <pkg>          # Affiche les détails d'un paquet
```
    
### 🔹 **Principales différences**

|Fonctionnalité|`apt`|`apt-get`|
|---|---|---|
|**Convivialité**|✅ Oui (couleurs, barre de progression)|❌ Non (sortie brute)|
|**Commandes combinées**|✅ (`search`, `show`, etc.)|❌ Nécessite `apt-cache`|
|**Recommandé pour...**|Usage interactif|Scripts et automation|

### 🔹 **Quand utiliser `apt` vs `apt-get` ?**

- **Pour un usage quotidien** (installer/mettre à jour des paquets) : **`apt`** (plus simple et lisible).
    
- **Pour des scripts ou l'automatisation** : **`apt-get`** (plus stable en sortie brute).
    

### 🔹 **Exemple de différence visuelle**

- Avec **`apt upgrade`**, vous voyez une barre de progression :
    ```Bash
    0% [En attente des en-têtes] [En attente de la connexion]
```
    
    
- Avec **`apt-get upgrade`**, la sortie est plus technique et sans couleurs.
    

### **Conclusion**

- **`apt`** est plus moderne et convivial pour les utilisateurs normaux.
    
- **`apt-get`** reste utile pour les scripts et la compatibilité.
    

En résumé, préférez **`apt`** sauf si vous avez besoin de **`apt-get`** pour des raisons spécifiques. 😊