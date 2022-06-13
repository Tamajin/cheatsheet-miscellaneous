# React 2: le hook UseEffect

## 1. Définition

Le hook `useEffect` est un hook qui va permettre de déclencher une fonction de manière asynchrone lorsque l'état du composant change.
`useEffect` permet d'exécuter du code sans rapport avec le rendu tout au long du cycle de vie d'un composant.

**syntaxe**

```javascript
React.useEffect(() => {callback}, [tableau_de_dependances]);
```

## 2. Cycle de vie d'un composant

Pour comprendre le fonctionnement du hook `useEffect`, il est important de comprendre le cycle de vie d'un composant:

### 🏗️ Phase de montage - Naissance du composant

C'est lorsque le composant est monté sur le DOM avec tous ses composants enfants. C'est un bon moment pour déclencher des appels d'API ou pour déclencher des fonctions une fois que tous les composants sont chargés à l'écran.

>Pendant la phase de montage : le callback passé en premier argument de useEffect sera toujours exécuté lorsque le composant est monté.

**exemple**
Le composant Message crée une div avec le texte "Coucou les Click'n Mousse" au click sur un bouton. Le `useEffect` affichera alors le même message dans la console:

```javascript
function Message() {
    React.useEffect(() => {
        console.log("Coucou les Click'n Mousse") 
    });

    return <h1>Coucou les Click'n Mousse<h1>;
}
```

### ♻️ Phase de mise à jour - Évolution du composant

Cette phase se produit lorsque le composant reçoit des modifications (nouvelles valeurs pour les props, état mis à jour...). Au cours de cette phase, tu dois surveiller toute modification apportée au composant et déclencher les effets secondaires associés (par exemple, rappelez ton API).

>le callback sera executé lors de cette phase si aucun tableau de dépendances n'est spécifié ou si un élément présent dans le tableau des dépendances a changé (cas d'un tableau vide, rien ne se passera pendant la phase de mise à jour).

**exemple**
Dans cet exemple, le `useEffect` est muni d'un tableau de dépendances. Le message "Youhou you clicked" s'affichera uniquement lors de la mise à jour du "state" de count (via `useState`)

```javascript
 React.useEffect(() => {
    console.log(`Youhou you clicked ${count}`);
  }, [count]);
```
>Tableau des dépendances avec des variables = le callback du useEffect s'exécute chaque fois qu'une variable répertoriée voit sa valeur modifiée (phase de mise à jour).

### 💥 Phase de démontage - Fin du composant

C'est le moment où le composant est démonté, enlevé du DOM. C'est la phase où tu dois faire un nettoyage sur ton composant (par exemple, arrêter les timers, annuler les abonnements...).

>le callback sera executé lors de cette phase s'il retourne une fonction

**exemple**
On retrouve notre composant Message de tout à l'heure, mais cette fois ci nous voulons qu'il affiche un message "A bientôt" dans la console lorsqu'il disparait lors d'un nouveau click sur le bouton:

```javascript
function Message() {
    React.useEffect(() => {
        console.log("Coucou les Click'n Mousse") // s'affiche lors de la phase de montage
        return () => console.log("A bientôt") // s'affiche lors de la phase de démontage
    });

    return <h1>Coucou les Click'n Mousse<h1>;
}
```

## 3. Les dépendances

L’utilisation du deuxième paramètre du hook useEffect va nous permettre de faire une utilisation plus fine de cet effet de bord “contrôlé” : la liste de dépendances de notre hook.
Ces dépendances sont des valeurs que le useEffect va étudier à chaque re-render. Si les valeurs listées ne sont pas modifiées, le useEffect ne sera pas déclenché. Si au contraire, la valeur d’une des dépendances listées a changé le useEffect sera bien déclenché.

**exemple**

Voici un exemple, avec ce coup-ci le deuxième paramètre dans notre useEffect ainsi qu’un autre useState qui viendra causer un re-render de notre composant :

```javascript
const MonComposant = () => {
  const [shouldLog, setShouldLog] = useState(false);
  const [isWhatever, setIsWhatever] = useState(false);

  useEffect(() => {
    // N'est jamais appelé lors que l'utilisateur clique sur "Rafraîchir"
    if (shouldLog) {
      console.log('Coucou !');
    }
  }, [shouldLog]);

  return (
    <div>
      <button onClick={() => setShouldLog(true)}>Afficher</button>
      <button onClick={() => setIsWhatever(!isWhatever)}>Rafraîchir</button>
    </div>
  );
};
```
>Ici, le fait d’avoir listé dans le deuxième paramètre de notre useEffect la dépendance shouldLog fait que le code à l’intérieur n’est appelé que si shouldLog change. Si l’utilisateur clique sur le bouton “Rafraîchir”, rien ne sera affiché dans la console.