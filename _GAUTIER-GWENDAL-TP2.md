# TP 2 Administration Système
## Gwendal GAUTIER 3A IRC

 ## Exercice 1 : Variables d'Environnement

 ## Question 1 
 bash trouve les commandes tapés par l'utilisateur dans les fichiers suivants : 
 * /usr/local/sbin
 * /usr/local/bin
 * /usr/sbin
 * /usr/bin
 * /sbin
 * /bin
 * /usr/games
 * /usr/local/games

 On trouve ces fichiers en utilisant la commande : 
 ```
 printenv PATH
 ```

 ## Question 2 
 La variable d'environnement qui permet à `cd` de retourner directement à son dossier personnel quand on ne lui donne pas d'arguments, est `HOME`

 ## Question 3 
 La variable `LANG` détermine la langue utilisé par les logiciels pour communiquer avec l'utilisateur.

 La variable `PWD` contient le chemin du dossier dans lequelle on se trouve actuellement.

 La variable `OLDPWD` contient le chemin du précédent dossier dans lequelle on se trouvais.

 La variable `SHELL` indique l'interpréteur de commande préféré de l'utilisateur.

 La variable `_` indique le chemin d'accès au script de printenv.

 ## Question 4 
 On crée une variable MY_VAR avec la commande suivante et On lui donne la valeur 4: 
```
MY_VAR=4
```
Puis on vérifie son existence et que sa valeur est bien attribuée : 
```
echo MY_VAR
```

## Question 5 
La commande `bash` ouvre un bash, qui est en fait un invite de commande. La varialbe MY_VAR existe, mais seulement dans ce bash (puisque c'est une variable locale). 

## Question 6 
Pour transformer MY_VAR en variable d'environnement  on utilisera la commande :
```
declare -x MY_VAR 
``` 
On lui affectera une valeur de la même manière que précédemment, et on utilisera ensuite `printenv` pour l'afficher. 

Cette fois-ci, même en utilisant `exit` on retrouve notre variable MY_VAR une fois sorti de ce bash, car c'est une variable d'environnement. 

## Question 7 
On créera la variable NOMS : 
```
NOMS="GAU TIER"
```
et on utilisera `echo` pour vérifier son existence.

## Question 8 
On utilisera `""` pour faire interpréter la chaîne par l'invit de commande : 
```
echo "Bonjour à vous deux $NOMS"
```
## Question 9
Donner une valeur vide à une variable fait qu'elle existe, mais n'a pas de valeur. `unset` supprime la valeur de la variable **ET** la variable elle-même.

## Question 10
On définit d'abord la variable chemin comme :
```
chemin=$HOME
```

Puis ensuite, on joue des guillemets simples et doubles : 
```
echo "$HOME = "'$chemin'
``` 
Ce qui donne ici comme résultat : 
```
$HOME = /home/gwendal
```

# Programmation Bash
## Exercice 2 
```
#!/bin/bash

read -s -p 'Entrez le mot de passe' mdp

if [[ $mdp = $PASSWORD ]]
then 
    echo "Mot de Passe Correct"
else 
    echo "Mot de Passe Incorrect"
fi
```
## Exercice 3 
```

#!/bin/bash
function is_number()
{
    re='^[+-]?[0-9]+([.][0-9]+)?$'

    if ! [[ $1 =~ $re ]] ; then
        echo 1 
    else
        echo 0
    fi
}
verif=$(isnumber $1)

if [[ $verif = 1 ]] ; then
    echo "Ce nombre n'est pas un réel "
else 
    echo "Ce nombre est un réel"
fi 
```

## Question 4 
```
#!/bin/bash

if [[ $# = "1" ]]
then 
    var=$(sudo cat /etc/passwd | cut -d : -f 1 | grep ^$1$ | wc -l)
    if [[ $var = 1 ]]
        echo "L'utilisateur existe"
    else
        echo "L'utilisateur n'existe pas"
    fi
else 
    echo 'Utilisation : ' "$0" 'nom_utilisateur'
fi
```
## Question 5 
```
#!/bin/bash

res=1

for ((i=1;i<=$1;i++))
do
    res=$((res*i))
done
echo "$res"
```
## Question 6 
```
#!/bin/bash

nb=$((RANDOM%1000))
ess=0
while [ 1 ]
do
    read -p "Entrez un nombre" ess
    if [[ $ess > $nb ]]
    then
        echo "Plus petit !"
    elif [[ $ess < $nb ]]
    then
        echo "Plus grand !"
    else
        echo "Gagné ! "
        exit 0
    fi
done
```
## Question 7 
```
```