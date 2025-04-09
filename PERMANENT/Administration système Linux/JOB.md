## 🎯 Un **job**, c’est quoi exactement dans un terminal Linux (bash) ?

Un **job** est un **processus ou groupe de processus** lancé **depuis ton shell interactif** (ton terminal), et **géré par ce shell**.

Il peut être :

- **en avant-plan** (tu interagis avec),
    
- ou **en arrière-plan** (il tourne, mais tu continues à utiliser le terminal).
    

---

## 🧠 Exemple simple :

bash

CopierModifier

`sleep 100`

Là, le job est en **avant-plan** → ton terminal est bloqué jusqu’à ce que `sleep` finisse.

---

bash

CopierModifier

`sleep 100 &`

Là, le job est en **arrière-plan**, et tu vois :

csharp

CopierModifier

`[1] 12345`

- `[1]` → Numéro du job dans le shell.
    
- `12345` → PID du processus.
    

Ton terminal est **libre**, mais le job tourne toujours.

---

## 🔧 Commandes utiles pour les jobs :

|Commande|Utilité|
|---|---|
|`jobs`|Liste tous les jobs lancés depuis ce shell|
|`fg %1`|Ramène le job numéro 1 au **premier plan**|
|`bg %1`|Met le job numéro 1 en **arrière-plan**|
|`kill %1`|Termine le job numéro 1|
|`CTRL+Z`|Met un job en pause (suspendu)|
|`CTRL+C`|Interrompt un job en avant-plan|

---

## 📌 Important :

Les **jobs sont liés au shell**. Si tu fermes le terminal, les jobs **en arrière-plan sont tués** (sauf si tu utilises `nohup` ou `disown`).

---

Si tu veux qu’un processus tourne en arrière-plan **même si tu fermes la session**, il vaut mieux :

- Utiliser un **service systemd** ✅
    
- Ou lancer avec `nohup` :
    

bash

CopierModifier

`nohup /usr/local/bin/moniteur.sh &`

Souhaites-tu un exemple avec `nohup` ou `disown` ?

4o