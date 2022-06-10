# Tableaux : méthodes fonctionnelles (map, forEach, filter, every, some, reduce, includes)

## 1. Map

**Méthode map()**

la méthode map parcourt tous les éléments d'un tableau en exécutant une fonction de rappel (callback). Elle renvoie un nouveau tableau avec tous les éléments transformés par la fonction callback;

**Syntaxe**

  ```javascript
  let newArray = array.map(function)
  ```

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

**exemple :**

```javascript
    const myArray = [3, 2, 40, 15, 20];
    const greaterThanFive = myArray.filter(number => number > 5);
    console.log(greaterThanFive);
```


## 3. forEach

**Méthode forEach()**

la méthode *forEach()* effectue une action sur chaque élément du tableau sans valeur de retour

Attention toutefois, la méthode n’utilise pas une copie du tableau 
lorsqu’elle est appelée, elle manipule le tableau directement. 
Donc si on modifie le tableau en cours de route alors les boucles pourront être impactées.

**syntaxe :**

```javascript
array.forEach(function());
```

**exemple :**

```javascript
let sentences = animals.forEach(
  (animal, index) => `${animal.name} the ${animal.species}, the number ${index}`
);

console.log(sentences); // undefined
```


## 4. Every

**Méthode every()**

La méthode *every()* vérifie si tous les éléments d'un tableau répondent à une condition. Le résultat de la méthode every est un booléen.

**syntaxe**

```javascript
array.every(function());
```

**exemple**

```javascript
const myArray = [11, 34, 54, 32, 54];
console.log(myArray.every(element => element > 10));
// true
```


## 5. Some

**Méthode some()**

la méthode *some()* est très similaire à *every()*, excepté qu'il suffit d'un élément du tableau vérifiant la condition pour que cette méthode renvoie true.

**syntaxe**

```javascript
array.some(function());
```

**exemple**

```javascript
const myArray = [11, 34, 54, 32, 54];
console.log(myArray.some(element => element > 30)); // true 
```


## 5. Reduce

**Méthode reduce()**

La méthode *reduce()* réduira le tableau à une seule valeur.

**syntaxe**

```javascript
array.reduce(function());
```

**exemple**

Ex : Nous avons un tableau de nombres et nous voulons connaître la somme de tous les nombres
```javascript
const myArray = [13, 200, 404, 430, 10];
console.log(myArray.reduce((acc, currentValue) => acc + currentValue));
// 1057
```

Le premier argument donné à la méthode reduce est une fonction de rappel qui sera exécutée pour tous les elements du tableau (par défaut à partir du 2ème).
Cette fonction sera rappelée par reduce avec les arguments suivants :

   **L'accumulateur :** c'est le résultat de toutes les opérations précédentes. Dans notre cas, l'accumulateur commence avec la valeur du premier élément dans le tableau.
   **La valeur de l'element actuellement parcouru dans le tableau**, qui sera égale à 200 au premier tour de la boucle, puis 404, puis 430, et ainsi de suite...
Cette fonction de rappel retourne la valeur de l'accumulateur pour l'itération suivante.
La méthode reduce quand à elle retournera la valeur finale de l'accumulateur une fois les éléments parcourus.

## 6. Includes

**Méthode includes()**

```javascript
const array1 = [1, 2, 3];

console.log(array1.includes(2));
// expected output: true

const pets = ['cat', 'dog', 'bat'];

console.log(pets.includes('cat'));
// expected output: true

console.log(pets.includes('at'));
// expected output: false
```

**Syntaxe**

```javascript
array.includes(élémentRecherché)
array.includes(élémentRecherché, indiceDépart)
```

**élémentRecherché**

La valeur qu'on souhaite trouver dans le tableau (lorsqu'on manipule des caractères et des chaînes, la comparaison est sensible à la casse).


**indiceDépart**

La position du tableau *à partir de laquelle* commencer à chercher élémentRecherché. *Si on utilise une valeur négative*, la recherche commencera à partir de la fin du tableau (autrement dit à l'indice array.length - indiceDépart). La valeur par défaut est 0.



