Panneau de configuration\Système et sécurité\Pare-feu Windows Defender 
cliquer sur le Paramètres avancés
cliquer sur règles de trafic entrant
clique droite sur ces lignes puis cliquer sur désactiver
- **Bureau à distance (TCP-In)**
- **Bureau à distance (UDP-In)**
- Toute autre règle liée à des services comme VNC, SSH, etc.

### 🪟 **Sous Windows (10 / 11)**

#### 1. **Désactiver le Bureau à distance (Remote Desktop)**

- Appuie sur `Windows + I` pour ouvrir **Paramètres**
    
- Va dans **Système > Bureau à distance**
    
- Désactive l’option **Activer le Bureau à distance**
    

#### 2. **Bloquer les connexions entrantes via le Pare-feu**

- Va dans le **Panneau de configuration**
    
- Clique sur **Système et sécurité > Pare-feu Windows Defender**
    
- Dans la colonne de gauche, clique sur **Paramètres avancés**
    
- Dans les **Règles de trafic entrant**, désactive ou supprime les règles comme :
    
    - **Bureau à distance (TCP-In)**
        
    - **Bureau à distance (UDP-In)**
        
    - Toute autre règle liée à des services comme VNC, SSH, etc.
        

#### 3. **Désactiver l’assistance à distance**

- Dans la recherche Windows, tape `sysdm.cpl` et ouvre-le
    
- Onglet **Utilisation à distance**
    
- Décoche **Autoriser l'assistance à distance...**