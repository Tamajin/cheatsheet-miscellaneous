## JS BASICS

# Cours 7 : JavaScript Basics
Utilisation du camelCase pour déclarer les variables : pas de caract speciaux, première lettre min, pas de chiffre au début.
###  Déclarer variable :
```const toto = "string";``` //const variable non modifiable
```let tata = 2;``` let variable modifiable
Pour modifier une variable let 
```tata = 3;``` //on la rappelle et on lui donne une nouvelle valeur

CAREFUL ! On n'utilise plus var pour déclarer une variable

### Type de données:

- Primitives ==> String (ex: "toto"), Number (ex: 10), Booleans (ex:True/False), Undefined, Null ==> Elles sont immutables;
- Non primitives ==> Objet(ex: {}) , Fonction ==> Elles sont mutables;

typeof permet de connaître le type de variable :
```typeof toto;``` //doit retourner "string"
```typeof tata;``` //doit retourner "number"


## Les tableaux (Array):
    Pour déclarer un tableau (array)
```const array = [🎅, 👳‍♂️, 👨‍🍳];```
    Modifier le contenu d'un tableau
Rajouter du contenu 
```array.push(👨‍💻);``` //à la fin du tableau
```array.unshift(👵);``` //au début du tableau
Retirer du contenu
```array.pop();``` //à la fin du tableau
```array.shift();``` //au début du tableau
Connaître la longueur d'un tableau
```console.log(array.length);```
    Les tableaux comportent des index. Le premier élément d'un tableau [0]
```console.log(array[0]);``` //doit retourner "🎅"

## Les Objets {} : 
Ce sont des sortes de conteneurs ayant des propriétés
 avec des valeurs ou des actions.
 pour accéder à une propriété, on utilise soit le "." ou les "[]"
 On peut ajouter une propriété mais aussi faire un tableau d'objet,
 en combinant : tableau et objet.
 Une fonction à l’intérieur d’un objet est appelée une méthode.
    Exemple :
 

    const person1 = {
        name : "Bob",
        age : 30,
        food : 🍕,
        sayHello : function(){
            console.log("Hello, I'm Bob")
        }
    }


## Créer une fonction : 
Une fonction sert à stocker un bloc de code afin de pouvoir le réutiliser plus tard sans avoir à le réécrire :


    function toto() {
        //instruction
        return "toto";
    }
    console.log(toto());


Ou à la place:

    function tata() {
        console.log("tata");
    }
    tata();

Fonction avec paramètres :

    function sayHello(firstName, lastName){
        console.log(`Hello ${firstName} ${lastName}`)
    }
    sayHello("Mickey", "Mouse");

Ou :

    function sum(a, b){
        return a + b;
    }
Ou :

    const sum = (a,b) => {
        return a+b;
    };

En fonction fléchée on aura :

    const sum = (a+b) => a + b 

Autre exemple :

    let userNumber = 2;
    function double (){
        userNumber = userNumber * 2;
    }
Ou :

    let userNumber = 2;
    function double(number){
        return number * 2;
    }

Ou :

    let userNumber = 2;
    userNumber = double(userNumber);

## Le mot-clé return : 
return != console.log();
il arrête immédiatement l'éxécution de la fonction
et retourne une valeur;
Alors que console.log() affiche du contenu dans la console pour
les tests,
la bonne pratique : une fonction qui a une valeur retour afin d'éviter les effets de bord indésirables.
    Exemple : 

    let userName = 2;
    function double(){
        userNumber=userNumber* 2
    } //la fonction double change la variable en dehors de la fonction.
    function double(number){
        return number * 2
    } 

Meilleure approche : il est impossible d'utiliser une variable en dehors de la fonction dans laquelle elle a été créée.

## Les conditions if et else : 
Quand il s'agit de faire un choix, nous pouvons utiliser  les "if - else" ou "switch"

if-else :


    const name = "Paul";
    if(name === "Paul"){
    console.log("Welcome, Paul");
    }
    else{
    console.log("Go away !");
    }

### Utilisation switch :


    let userCountry = prompt("Where are you from ?");

    switch(userCountry){
        case "France":
            console.log("Bonjour");
            break;
        case "England":
            console.log("Hello");
            break;
        case "Germany":
            console.log("Hallo");
            break;
        case "Italy":
            console.log("Ciao");
            break;
        default:
            console.log("Hey there");
            break;
}

On peut remplacer if et else par un opérateur ternaire ( => if = true = ?)  (else = false = :)


    function getFee(isMember){
        return (isMember ? `$2.00` : `$10.00`);
    }
    console.log(getFee(true)); //on paiera 2$
    console.log(getFee(false));//on paiera 10$

## Les opérateurs : 
modulo = % (retourne l'unité d'une division. 
Exemple : 10 % 2 résultat = 0 car 2*5 = 10 donc il ne reste rien; 
13 % 5 => résultat = 3 car 5*2 = 10, il reste 3); 

multiplier  *, diviser  /, additionner  +, soustraire -
< : inférieur;
> : supérieur;
<= : inférieur ou égal;
>= : supérieur ou égal;
inégalité strict !==
égalité strict === : valeurs et types sont les mêmes (exemple : "Bob" === "Bob");
égalité == : valeurs sont les mêmes mais pas le type (exemple : "0" == 0);

## Les opérateurs logiques : 
&& : et => pour ajouter une condition;
|| : ou => une condition ou une autre;

Exemple :

    const userName = "Paul";
    const password = "secret";
    //Si le nom est Paul ou Bob => bonjour
    if(userName === "Paul" || userName === "Bob"){
        console.log("Welcome");
    }// et si le nom est Paul ET que le mot de passe est secret =>
    if(userName === "Paul" && password === "secret"){
        console.log("Welcome");
    }

## Les boucles: 
Les boucles permettent de répéter une suite d'instructions plusieurs fois :


    for(let i = 0; i < 5; i++){
    console.log("Turn number " + i) //Va renvoyer 5 fois "Turn number"
    }
La boucle "for" est la plus classique.

Il existe aussi les boucles :
  - while,
  - do ... while,
  - foreach.
La boucle est infinie si une condition est toujours vraie.
La conséquence est de bloquer notre code.



