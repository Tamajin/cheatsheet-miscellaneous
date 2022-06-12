## Fiche sur les fonctions intéressantes liées au DOM

## Accéder aux éléments

`document.getElementsByTagName("baliseHTML")` - Sélectionne tous les éléments avec la balise entre parenthèses

`document.getElementById("#Id")` - Sélectionne un seul élément : le premier ayant l'ID entre parenthèses

`document.getElementsByClassName(".className")` - Sélectionne tous les éléments avec la classe entre parenthèses et les retournent dans un tableaux

`document.querySelector("element")` - Sélectionne un seul élément : celui avec le sélecteur entre parenthèses

`document.querySelectorAll("element")` - Sélectionne tous les éléments avec le sélecteur entre parenthèses (attention crée un tableau !)


## Modifier les éléments

`element.innertext` - Modifie le texte d'un élément

`element.innerHTML` - Modifie l'HTML d'un élément

## Ajouter et supprimer des éléments

`document.createElement("tagName")` - Crée un élément

`element.prepend("texte ou balise html")` - Ajoute l'élément entre parenthèses devant l'élément cible

**exemple**
Ajouter du texte
```javascript
let div = document.createElement("div");
div.append("Du texte");
div.prepend("Titre : ");

console.log(div.textContent); // "Titre : Du texte"
```

`element.append()` - Ajouter l'élément entre parenthèses derrière l'élément cible (peut contenir du texte)

**exemple**
Voir ci dessus

`elementparent.appendChild(enfant)` - Ajouter l'élément entre parenthèses derrière l'élément cible (ne peut pas contenir du texte)


## Modifier le style d'un élément

`element.style.propriété` - Modifie la propriété CSS spécifiée

**exemple**
Modifier la couleur du texte en orange d'une div avec une classe "madiv"
```javascript
let maDiv = document.querySelector(".madiv") //on stocke la div dans une variable
maDiv.style.color = "orange" //on modifie la couleur en orange
```

## Ajouter ou supprimer une classe à un élement

### Ajouter une classe

`element.className.add("ClassName)`

**exemple**
Ajouter la classe "superdiv" à une div qui a déjà la class "madiv"
```javascript
let maDiv = document.querySelector(".madiv") //on stocke la div dans une variable
maDiv.className.add = "superdiv" //on y ajoute la classe "superdiv"
```

### Supprimer une classe

`element.className.remove("ClassName)`

**exemple**
Supprimer la classe "superdiv" ajoutée dans l'exemple précédent
```javascript
maDiv.className.remove = "superdiv" //on supprime la classe "superdiv" de la variable maDiv
```







