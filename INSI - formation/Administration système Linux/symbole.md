## symbole |
Le symbole `|` (pipe) est utilisé en **shell** pour **rediriger la sortie d'une commande** vers l'entrée d'une autre commande.

### **Exemple simple :**
```Bash
echo "Hello, world!" | wc -c
```

**Explication :**
1. `echo "Hello, world!"` → Affiche `"Hello, world!"` dans la sortie standard (`stdout`).
2. `|` → Envoie cette sortie vers la commande suivante.
3. `wc -c` → Compte le nombre de caractères dans l'entrée reçue.
**Résultat :**
```
14
```
(incluant le saut de ligne `\n`)