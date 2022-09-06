# VSCode : astuces et raccourcis pratiques

## _Gagnez en temps et en productivité_

Avant de vous lancer dans la grande et fantastique aventure de l'autocomplétion quelques prérequis sont nécessaires :

- intallation de [ES7+ React/Redux/React-Native snippets];
- vérification de votre fichier settings.json (voir section spéciale juste en dessous);
- believe in ✨Magic ✨.

### Settings VSCode

Pour accéder rapidement au fichier settings : `CTRL + SHIFT + P`

```sh
dans le champs de recherche écrivez "settings"
ouvrez "préférences: Open Settings (JSON)"
```

Une fois ouvert le contenu devrait ressembler à ceci[^bignote] :
[^bignote]: les préférences relatives au thème, au terminal par défaut, au navigateur par défaut avec LiveServer, sont à votre discrétion. Les lignes qui nous intéressent ici sont les deux dernières commençant par "emmet".

```json
{
    "workbench.colorTheme": "Default High Contrast",
    "files.autoSave": "afterDelay",
    "liveServer.settings.donotShowInfoMsg": true,
    "diffEditor.renderSideBySide": false,
    "terminal.explorerKind": "external",
    "terminal.integrated.defaultProfile.windows": "Git Bash",
    "liveServer.settings.AdvanceCustomBrowserCmdLine": "C:\\Program Files\\Firefox Developer Edition\\firefox.exe --private-window",
    "liveServer.settings.donotVerifyTags": true,
    "codesnap.showLineNumbers": false,
    "codesnap.showWindowControls": false,
    "workbench.startupEditor": "none",
    "emmet.includeLanguages": {
        "javascript": "javascriptreact"
      },
      "emmet.triggerExpansionOnTab": true
}
```

Copiez ces quelques lignes dans votre propre fichier settings.json et vous serez prêts pour la suite.

## Raccourcis généraux

Ici, quelques astuces valables quel que soit le langage utilisé, que vous soyez ou non dans un projet _React_.

1. Remplacer rapidement du texte.

_"Shit ! J'ai fait une faute de frappe dans le nom d'une classe, et j'ai copié cette erreur sur des centaines de lignes de code. J'en ai pour une heure de temps perdu à tout retrouver[^2]"_
VSCode a la solution ! Sélectionnez le texte à modifier puis faites un **CTRL+H**. Une boîte de dialogue s'ouvre en haut de la page et vous propose de renseigner le texte de remplacement. Pressez **entrée** autant de fois que nécessaire (le nombre d'occurences du texte sélectionné apparaît dès le départ). Un **CTRL+SHIFT+H** fera de même dans _tous les fichiers de votre projet_.
>astuce : vous pouvez combiner un `CTRL + SHIFT + F`suivi de la commande de remplacement de texte, très utile pour remplacer les console.log() par un espace vide et ainsi tous les supprimer

[^2]: un autre bon exemple d'utilité aurait été une modification de plusieurs props dans un composant React en une seule fois.

2. Déplacer/copier une ou plusieurs lignes de code.

Très simplement, placez-vous sur la ligne à déplacer (ou sélectionnez un bloc de lignes) et combinez **ALT + ⬆️ ou⬇️** pour monter ou descendre dans votre code. C'est la fin des copier/coller pour déplacer une balise HTML fermée par l'autocomplétion !
Si vous combinez **ALT + SHIFT + ⬆️ ou⬇️**  vous copierez cette fois la zone de texte sélectionnée.
>astuce : peut notamment s'avérer très utile en CSS pour reprendre tout un style, en changeant seulement le sélecteur, ou pour copier des zones **HTML** tout en les positionnant à l'endroit souhaité.

3. Afficher / masquer

Vous pouvez gagner en visibilité en maximisant l'espace disponible pour votre code. Plutôt que de redimensionner sans arrêt les fenêtres du terminal (en bas) ou de l'explorateur de fichiers (à gauche), vous pouvez les faire apparaître ou disparaître. En tableau ci-dessous une synthèse des raccourcis les plus pratiques pour gagner en visibilité :

| Raccourci clavier    | Action réalisée                          |
|----------------------|------------------------------------------|
| **CTRL + J**         | affiche/masque le terminal               |
| **CTRL + B**         | affiche/masque la barre latérale |
| **CTRL + SHIFT + V** | affiche la prévisualisation Markdown     |
| **F11**              | active/désactive le plein écran          |

4. Raccourcis d'édition

D'autres raccourcis vous seront très utiles, en voici un tableau :

| Raccourci clavier        | Action réalisée                       |
|--------------------------|---------------------------------------|
| **CTRL + ENTER**         | insérer une ligne en dessous          |
| **CTRL + SHIFT + ENTER** | insérer une ligne au dessus           |
| **ALT + Z**              | activer le retour à la ligne          |
| **CTRL + ⬆️ OU ⬇️**        | scroller dans le fichier              |
| **CTRL + /**             | commente/décommente une ligne         |
| **SHIFT + ALT + A**      | commente/décommente un bloc de lignes |
| **CTRL + K CTRL + S**    | affiche tous les raccourcis clavier[^3]   |

[^3]: cerise sur le gâteau vous pouvez éditer vos propres raccourcis clavier !

## Autocomplétion

Nous allons présenter quelques exemples pratiques, gardez bien à l'esprit que la liste est très loin d'être exhaustive, et que si vous vous sentez capable vous pouvez créer vos propres scripts personnalisés. Une liste complète est disponible [ICI].
D'une manière générale, n'oubliez pas que la touche **TAB** est votre amie, _VSCode_ est un éditeur bien fourni nativement en autocomplétion.

- Exemple 1 : rédiger une fonction fléchée dans un composant fonctionnel

Écrivez `rafce` pour obtenir ce résultat, une pression sur la touche **TAB** vous fera naviguer directement du nom de la fonction au paramètre, puis du paramètre au contenu de la fonction. Le tout bien indenté automatiquement.

```javascript
import React from 'react'
const $1 = () => {
  return <div>$0</div>
}
export default $1
```

- Exemple 2 : fonction fléchée classique
`nfn` :

```javascript
const first = (second) => { third }
```

> astuce : la touche **TAB** permet toujours de passer de "first" à "second" etc.

- Exemple 3 : console.log()

Entrez `clg` :

```javascript
console.log(first)
```

- Exemple 4 : les imports _React_ (liste non exhaustive)

|      Prefix | Method                                                                      |
| ----------: | --------------------------------------------------------------------------- |
|      `imr→` | `import React from 'react'`                                                 |
|     `imrd→` | `import ReactDOM from 'react-dom'`                                          |
|     `imrc→` | `import React, { Component } from 'react'`                                  |
|     `imrr→` | `import { BrowserRouter as Router, Route, NavLink} from 'react-router-dom'` |

- Exemple 5 : un peu de **HTML** ?

Imaginons que vous souhaitiez créer plusieurs paragraphes, vous seriez tentés d'écrire `<p></p>` et de faire du copier/coller autant de fois que nécessaire, n'est-ce pas ? (ou si vous avez bien suivi jusque-là **ALT + SHIFT + ⬇️**). Il y a encore plus simple. Essayez `p*6` suivi de **ENTER** ou **TAB** et vous obtiendrez :

```html
<p></p>
<p></p>
<p></p>
<p></p>
<p></p>
<p></p>
```

Vous pouvez réaliser la manipulation avec toutes les balises !

Un peu plus poussé encore. Vous souhaitez une balise `<img>` dans chacun de ces paragraphes. Commandez `p*6>img` et vous serez servis :

```html
<p><img src="" alt="" /></p>
<p><img src="" alt="" /></p>
<p><img src="" alt="" /></p>
<p><img src="" alt="" /></p>
<p><img src="" alt="" /></p>
<p><img src="" alt="" /></p>
```

Les possibilités en matière d'imbrication de balises sont assez incroyables, vous pouvez vous structurer un squelette _html_ en une seule ligne de code. En voici un cas pratique : "je veux une section comportant deux div, chacune comportant trois paragraphes avec du contenu générique". En ligne de code ça donnerait `section>div*2>p*3>lorem20` , pour ce résultat :

```html
<section>
    <div>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Sapiente velit unde fuga vitae sit ipsam eum provident molestias vero temporibus.</p>
        <p>Rerum aperiam cupiditate vel deleniti accusantium error perspiciatis tempora veniam! Animi, magnam maxime omnis iusto rem dolorem tenetur natus vel.</p>
        <p>Minus suscipit recusandae at vitae! Nesciunt ex ratione nam est possimus explicabo quod in saepe eum, maiores aspernatur vero quas.</p>
    </div>
    <div>
        <p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Illo temporibus tempore doloremque inventore soluta, impedit cupiditate natus nemo earum modi?</p>
        <p>Doloremque molestiae enim architecto ducimus? Nobis voluptatum neque fuga quidem ipsam enim. Ex voluptates odio distinctio delectus sunt obcaecati et?</p>
        <p>Alias ipsum laborum sunt facere porro deserunt placeat ratione veritatis ab, nulla, impedit commodi a dolorem in ex assumenda distinctio?</p>
    </div>
</section>
```

- BONUS : un peu de typescript ?

Si vous souhaitez essayer typescript[^4] essayez donc de rajouter `ts` devant un des raccourcis déjà présentés. Tous ne sont pas compatibles, mais ça vaut le coup d'essayer.
`tsrafce` donnera par exemple:

```javascript
import React from 'react'

type Props = {}

const typescript = (props: Props) => {
  return (
    <div>typescript</div>
  )
}

export default typescript
```

[^4]: note du rédacteur : "et vous auriez raison !"

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [ES7+ React/Redux/React-Native snippets]: <https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets>
   [ICI]: <https://github.com/chillios-ts/vscode-react-javascript-snippets/blob/HEAD/docs/Snippets.md?plain=1#>
