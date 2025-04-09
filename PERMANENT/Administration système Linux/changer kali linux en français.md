## clavier -> AZERTY
cliquer sur le logo de kali linux
setting/keyboard
layout; 
decochena option "Use system default"
selectionner "English (US)" et 'Edit'
choix french

## système en français
utiliser le commande suivant
```Bash
sudo dpkg-reconfigure locales 
```
 choisir "Fr_FRUTF-8 UTF-8"
redémarrer le système apès

Remarque:
si le paquet "locales" n'est pas encore installer , il faut exécuter cette commande
```Bash
sudo apt update && sudo apt install locales
```

### changer le manuel en fr
```Bash
sudo apt install manpages-fr
#generer la local français 
sudo locale-gen fr_FR.UTF-8
sudo update-locale LANG=fr_FR.UTF-8

#recharger la configuration
source /etc/default/locale

#essaier 
man ls
```