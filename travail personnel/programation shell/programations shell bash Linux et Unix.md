source [[https://www.youtube.com/watch?v=wRswrO1SnB4&list=PLo53cbpzes8YqW9RsYQPMmadY__V1n9a3&index=6]]

entête
```Bash
#!/bin/bash
```
 (optionnel)
 ```Bash
 clear
```

pour affichage
```Bash
echo texte à afficher
```

commentaire
```Bash
# ceci est un commentaire
```

## Les Variables
Les variables d'environnements
```Bash
PATH, HOME, PWD, USER, USERNAME
```

pour lire une variable , on utiliser la commande
```Bash
read
```

Les quotes permettent de délimiter des paramètres qui contiennent un espace:
- simples quotes: le messafe n'est pas évalué
- Doubles quotes: le message est évalué
- Back quotes: le message est exécuté
exemple:
```bash
echo '$PWD'
=> $PWD

echo "$PWD"
=> /home/hasina

echo `$PWD`
=> /home/hasina
```
La commande "let" permet d'évaluer une chaîne de caractère 

### TP1
Nous voulons écrire un script shell qui utilise les variables 
- Nous dire bonjour en utilisant la variable USERNAME
- Nous donner la date du jour et l'heure avec la commande "date"
- Nous voulons ensuite déclarer une chaîne de caractères et l'afficher
- Enfin, nous voulons déclarer deux  variables entières, calculer leur somme dans une troisième variables afficher cette somme
```Bash
#!/bin/bash

clear

echo "Bonjour  $USER"
maDate=`date`
echo "Nous somme le $maDate "
uneChaine="voici un texte"
echo $uneChaine
nombre1=5
nombre2=6
let "somme=$nombre1+$nombre2"
echo "Somme : $somme"
```

## communiquer avec l'utilisateur
pour attendre une donnée utilisateur, nous pouvons utiliser la commande "read"
```Bash
Read <variable>
```
le paramètre "-p" da la commande "read" permet de spécifier un prompt. 
```Bash
Read -p <texte ou question> <variable>
```

### TP2
Ecrivez un script qui demande l'âge de l'utilisateur ainsi que son nom. ce script doit ensuite afficher le nom et l'âge à l'écran. Le script calcule ensuite l'année de naissance de l'utilisateur 

```Bash
#!/bin/bash

clear

read -p "Indiquer le nom de l'utilisateur :" nom
read -p "Indiquer l'age de l'utilisateur : " age

echo "Vous vous appelez $nom"
echo "Vous avez $age ans "

let "naissance=2025-$age"
echo "Vous êtes né en $naissance"
```

## Paramétrage du script au lancement
il est possible de lancer le script en lui associant directement des paramètre:
```Bash
> script <argument1> <argument2> ...
```

il est ensuite possible dans le programme de récupérer la valeur de ces arguments:
```Bash
$# Contient le nombre de paramètres
$0 est le nom du programme
$1 est la valeur du premier argument
$2 est la valeur du second argument
```

### TP3
Ecrivons un script qui lit l'âge et le nom de la personne directement dans la paramètre
```Bash
#!/bin/bash

clear

nom=$1
age=$2

echo "Vous vous appelez $nom"
echo "Vous avez $age ans "

let "naissance=2025-$age"
echo "Vous êtes né en $naissance"

```

## Redirection d'entrée standard
La redirection d'entrée standard permet de ne plus attendre que l'utilisateur saisisse les données.
Les données peuvent être lues directement dans un fichier
Ceci permet de rendre autonome un programme sans le modifier
Pour cela on utilise le symbole de redirection ```<``` au moment du lancement du script



### TP4
Modifions l'exemple prompt avec une redirection
```Bash
./tp3.sh < donner.txt
```
Remarque: les données doivent être dans l'ordre des paramètres et ligne par ligne

il est possible également de faire une redirection de sortie en utilisant le symbole ``` >``` au moment du lancement du script

```Bash
./tp3.sh < donnerEntrer.txt > donnerSortie.txt
```


## Structure CONDITIONNEL
```Bash
if[condition1]
then
	<commande à executé si condition1 vrai>
elif[condition2]
then
	<commande si condition 1 faux et condition2 vrai>
else
	<commande si condition1 faux et condition2 faux>
fi
```

### Evaluation des conditions - Opération sur les chaines de caractères
Les opération sont nécessaires pour bâtir nos conditions :
```Bash
$c1 = $c2 : Egalité
$c1 != $c2 : Différent
-z $c1: est-ce une chaine vide Chaîne vide
-n $c1: Chaîne non vide
```

### Evaluation des conditions - Opération sur les nombres
Les opérateurs de comparaison sont nécessaires por bâtir nos conditions :
```Bash
$n1 -eq $n2 : Egalité (Equal)
$n1 -ne $n2 : Différent (Not Equal)
$n1 -lt $n2 : inférieur (Lower Than)
$n1 -le $n2 : inférieur ou égale (Lower or Equal)
$n1 -gt $n2 : supérieur (Greater Than)
$n1 -ge $n2 : supérieur ou égale (Greater or Equal)
```

#### TP5
Reprenons le programme qui lit un âge et qui donne la catégorie d'âge qui lui correspond. Le programme demande à l'utilisateur son âge et affiche :
- 'bébé' si l'âge est inférieur à 3
- 'enfant' si l'âge est supérieur à 3 mais inférieur à 12
- 'adolescent' si l'âge est supérieur à 12 mais inférieur à 18
- 'adulte' si l'âge est supérieur à 18

```Bash
#!/bin/bash

clear

read -p "entrer votre age " age

if [ $age -lt 3 ]
then
        echo "Vous  êtes un bébé"
elif [ $age -lt 12 ]
then
        echo "Vous êtes un enfant "
elif [ $age -lt 18 ]
then
        echo "Vous êtes un ado "
else
        echo "Vous êtes un adulte"
fi
```

### Evaluation des conditions - Opérateur logiques
les opérateurs logiques permettent d'associer plusieurs tests (conditions):
```Bash
[ test1 ] && [ test2 ] : Opérateur ET
[ test1 ] || [ test2 ] : Opérateur OU
[ ! test1 ] : Opérateur NON
```

### Evaluation des conditions - structure Selon que . . .
La structure selon que est une variante de la structure Si:
```Bash
Case <Variable> in
	<Valeur1>)
		<commande si variable=Valeur1>
		;;
	<valeur2>)
		<commande si variable=valeur2>
		;;
	*)
		<commande dans les autres cas>
		;;
esac
```

c'est très intéressant de vérifier toujours le paramètre donner par l'utilisateur, donc il faut mettre cette script
```Bash
Case $# in
	2)
		nom=$1
		age=$2
		;;
	*)
		echo "usage : tp.sh <nom> <age>"
		;;
esac
```

### Evaluation des conditions - Existence d'un fichier/répertoire
Les scripts shell étant fortement liés au système d'exploitation, l'accès au système de fichier est facilité.

Il existe donc des possibilités pour tester facilement:
```Bash
# Le type d'un fichier : -d(répertoire) -f(fichier) -L(lien)
# Si un fichier ou répertoire existe: -e
# Les droits d'un fichier : -r, -w, -x
# comparer les dates de fichier: -nt(newer than), -ot(older than)
```

#### Tp6
Ecrire un script qui va créer un nouveau sous-répertoire dans le répertoire courant. Vérifier si le répertoire courant existe . Dans un second temps, tester si le répertoire à créer existe . Si le répertoire existe nous affichons qu'il existe déjà. Si le répertoire n'existe pas, nous le créons à l'aide de la commande "mkdir"
Attention si une variable chemin contient des espace, il faut l'encadrer avec des quottes

```Bash
#!/bin/bash

clear

rep=$PWD/$1

if [ -e "$PWD" ]
then
	echo " le chemin $PWD existe !"
	if [ -e "$rep" ]
	then
		echo " Le repertoire $rep existe déjà"
	else
		mkdir $rep
		echo "La repertoire a ete crée"
	fi
else
	echo "Le chemin $PWD n'existe pas"
fi
```