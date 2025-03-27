## préparation de dossier de travail

Création et activation de l'environnement virtuel 
pourquoi crée un environnement de travail?
création de l'environnemnt de travail:

```BASH
python -m venv env
```
activation de l'environnment de travail
sous windows :
```BASH
.\env\Scripts\activate
```
sou linux:
```BASH
souce env/bin/activate
```

### ouvrir le dossier dans ***"Pycharm"***
- ouvrir pycharm et chercher le dossier 

## Affichage et entrer
```PYTHON
<variable> = input('message ou question')
print("variable ou texte à afficher")
print("texte à afficher", <variable>)
print(f'texte à afficher {<variable} suite texte') # n'oubli pas de mettre la lettre "f" au debut
print('texte à afficher {} suite du texte', format(<variable>))
print('text à afficher %s' %(<variable>))
```

## Arithmétique
```PYTHON
	+ ; -, *, /,
	** : pour la puissnace
	% : modulo
```
## Commentaire
```PYTHON
# commentataire sur une ligne
'''
commentaire
à plusieurs
ligne
'''
```

## Condition
syntaxe :
 ```PYTHON
 if <condition 1> :
	 <code executer si condition 1 est true>
elif <condition 2> :
	<code executer si condition 2 est true>
else :
	<code executer si condition 1 et 2 sont false>
```

les signes de comparaison :
- == pour la comparaison egale
- > pour supérieur
- != pour différent
- < pour inférieur

## Les Boucles
syntaxe pour la boucle for :
```PYTHON
for <element> in <tableau>
	<code à executer>
```

syntaxe pour la boucle while :
```PYTHON
while <condition>
	<code à executer>
```

incrementation et decrementation
```PYTHON
i=i+1 ou i+=1
j=j-1 ou j-=1
```

## break et continu
## indentation
## type de variable
int, float, bool , string
en python, toute est objet

## formatage de variable


## Les Fonctions


