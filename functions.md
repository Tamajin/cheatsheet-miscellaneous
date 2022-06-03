# Tableaux : méthodes fonctionnelles (map, forEach, filter, reduce)

## 1. Map

**Méthode map()**

la méthode map parcourt tous les éléments d'un tableau en exécutant une fonction de rappel (callback). Elle renvoie un nouveau tableau avec tous les éléments transformés par la fonction callback;

**Syntaxe**

  ```let newArray = array.map(function)```

**Exemple**

```javascript
  const numbers = [1, 2, 5, 7];

      const doubles = numbers.map(function (currentNumber) {
      return currentNumber * 2;
      });

      console.log(doubles);  [2, 4, 10, 14];
```

**Exemple en version fléchée** 

```Javascript
    const triples = numbers.map(number => number*3);
```


## 2. Filter

**Méthode filter()**

La méthode filter crée un nouveau tableau avec seulement les éléments qui vérifient une condition donnée.

**Syntaxe :**

```javascript
    let newArray = array.filter(function(item) {
       return condition;
  });
```

  >L’argument **item** est une référence à 
  >l’élément courant dans le tableau, 
  >car filter() le vérifie par rapport à la condition.


```javascript
    const myArray = [3, 2, 40, 15, 20];
    const greaterThanFive = myArray.filter(number => number > 5);
    console.log(greaterThanFive);
```


## 3. forEach

**Méthode forEach()**

la méthode forEach() effectue une action sur chaque élément du tableau sans valeur de retour


Attention toutefois, la méthode n’utilise pas une copie du tableau 
lorsqu’elle est appelée, elle manipule le tableau directement. 
Donc si on modifie le tableau en cours de route alors les boucles pourront être impactées.

**syntaxe :**

```javascript
array.forEach(function());
```
