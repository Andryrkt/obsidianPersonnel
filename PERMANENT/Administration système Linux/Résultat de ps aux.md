## 📋 Résultat de `ps aux | grep moniteur.sh`

|PID|USER|CMD|
|---|---|---|
|`29797`|root|`sudo /usr/local/bin/moniteur.sh` → _commande lancée_|
|`29799`|root|`sudo /usr/local/bin/moniteur.sh` → _sous-processus lié au terminal `pts/1`_|
|`29800`|root|`/bin/bash /usr/local/bin/moniteur.sh` → **le script réel en exécution** ✅|
|`34151`|kali|`grep moniteur.sh` → ta commande de recherche, à ignorer ❌|

---

### ✅ Le "vrai" processus qui **exécute réellement le contenu du script**, c'est :

bash

CopierModifier

`root       29800  0.0  0.1   7076  3360 pts/1    SN   12:48   0:00 /bin/bash /usr/local/bin/moniteur.sh`

👉 C’est ce processus-là que tu dois **tuer** si tu veux **arrêter le script** :

bash

CopierModifier

`sudo kill 29800`

> Les autres (`29797`, `29799`) sont des **processus intermédiaires** créés par `sudo` ou le terminal.

---

### 💡 Astuce rapide pour tout tuer en une commande :

Si tu veux tuer **tous les processus liés à `moniteur.sh`**, tu peux faire :

bash

CopierModifier

`sudo pkill -f moniteur.sh`