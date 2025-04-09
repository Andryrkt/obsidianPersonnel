sudo apt install kali-desktop-xfce -y
sudo apt install xrdp -y
sudo service xrdp start
ip address : pour l'affichage de l'adresse ip

modifier sudo:
sudo visudo
coller ceci
hasina ALL=(ALL:ALL) NOPASSWD: /usr/sbin/service

Editer le fichier:
nano /home/hasina/.bashrc
ajouter ceci
sudo service xrdp start

Editer le fichier: pour modifier le port (on vaprende le port 3390)
sudo nano /etc/xrdp/xrdp.ini

redemarer le service xrdp:
sudo service xrdp restart