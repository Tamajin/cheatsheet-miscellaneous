# React : bases

## 1. Initialisation d'un projet react dans VSCode

Pour les applications à grande échelle, il existe Create React App, qui dispose de nombreux outils intégrés pour vous aider dans vos développements. 

Dans le terminal, une fois situé dans votre dossier **projets** vous pouvez taper cette commande :

` npx create-react-app contact-app `

Dans cet exemple un sous-dossier *contact-app* va se créer dans votre dossier *projets*. Si vous vous situez déjà dans votre dossier d'application vous pouvez utiliser cette commande : 

` npx create-react-app . `

> Note : l'utilisation du `.` permet d'installer le CRA dans le dossier courant. 

## 2. Gérer l'import et l'export des fichiers JS

Afin de rendre l'application plus facilement maintenable, il est préférable de diviser le code en plusieurs petits fichiers appelés "modules", plutôt que de tout écrire dans un énorme fichier. Pour afficher le composant *App*, l'instruction *ReactDOM.render* aura besoin d'un mécanisme pour le rechercher dans le fichier où il se trouve.

### -Import

**syntaxe**

>En haut de page

```javascript
import Componentname from "component_file_adress.js"
```

**exemple**

Nous souhaitons importer le composant Avatar contenu dans le fichier Avatar.js, lui même situé dans le sous dossier components du dossier src

```javascript
import Avatar from "./src/components/Avatar.js"
```

### -Export

**syntaxe**

>En bas de page, sous votre composant:

```javascript
export default Componentname
```

>ou bien directement avant le nom de votre composant:

```javascript
export const Componentname = (props) => {}
```

**exemple**

```javascript
const Contact = props => {
  return (
    <div className="friend-item">
      <div>
        <h3>{props.name}</h3>
        <h4>{props.mail}</h4>
        <h4>{props.phone}</h4>
      </div>
      {props.isDeletable ? <button onClick={() => onPressDelete("Contact supprimé")}>Delete</button> : ""}
    </div>
  );
};

export default Contact;
```

>ou bien avec la seconde possibilitée:

```javascript
export const Contact = props => {
  return (
    <div className="friend-item">
      <div>
        <h3>{props.name}</h3>
        <h4>{props.mail}</h4>
        <h4>{props.phone}</h4>
      </div>
      {props.isDeletable ? <button onClick={() => onPressDelete("Contact supprimé")}>Delete</button> : ""}
    </div>
  );
};
```

// Créer un composant dans dossier source 

// Props


### Comment utiliser useState ?

```javascript
const [state, setState] = React.useState('initialValue');
```
 exemple du hook useState:
 
 ```javascript
import React from 'react';
import './style.css';

export default function App() {
  // This is a react hooks 👇🏻
  const [counter, setCounter] = React.useState(0);
  return (
    <div className="App">
      <h1>Counter with Hook State</h1>
      <h1>{counter}</h1>
      <button onClick={() => setCounter(counter + 1)}>Increment</button>
    </div>
  );
}
 ```
Dans cet exemple, nous créons un compteur en utilisant useState.
Nous aurons accès à notre compteur en utilisant la variable counter, et si nous voulons mettre à jour le compteur, nous devons simplement utiliser la fonction setCounter() avec la nouvelle valeur en argument. Chaque fois que nous appelons setCounter, le composant s'affiche à nouveau automatiquement pour mettre à jour l'interface utilisateur.
[visitez ce site](https://daveceddia.com/usestate-hook-examples/)
[exemple](https://stackblitz.com/edit/react-qqzadd?file=src%2FApp.js)
// la méthode map pour parcourir un tableau d'objets

### L'Opérateur Ternaire


```javascript
 const isOnline = true; 
 isOnline ? "User is Online" : "User is Offline"; 
 ```


L’exemple ci-dessus utilise l’opérateur ternaire qui renvoie une valeur selon une condition. La première valeur entre le “?” et le “:” est retournée quand la condition est vraie. La seconde la valeur après le “:” est retournée quand la condition est fausse.
Dans cet exemple, la ligne 3 peut être remplacée par la valeur “User is online”. C’est parce que la variable isOnline de la ligne 1 est associée à true.


// À faire : gestion des évènements (onClick, onChange, onSubmit, etc.)

