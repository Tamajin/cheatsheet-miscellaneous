# VSCode : astuces et raccourcis pratiques

## _Gagnez en temps et en productivité_

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Avant de vous lancer dans la grande et fantastique aventure de l'auto-complétion quelques prérequis sont nécessaires :

- intallation de [ES7+ React/Redux/React-Native snippets];
- vérification de votre fichier settings.json (voir section spéciale juste en dessous);
- believe in ✨Magic ✨.

### Settings VSCode

Pour accéder rapidement au fichier settings : 
```sh
CTRL + SHIFT + P
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

## Raccourcis généraux.

Ici, quelques astuces valables quel que soit le langage utilisé, que vous soyez ou non dans un projet __React__.
1. Remplacer rapidement du texte.
*"Shit ! J'ai fait une faute de frappe dans le nom d'une classe, et j'ai copié cette erreur sur des centaines de lignes de code. J'en ai pour une heure de temps perdu à tout retrouver[^2]"*
VSCode a la solution ! Sélectionnez le texte à modifier puis faites un **CTRL+H**. Une boîte de dialogue s'ouvre en haut de la page et vous propose de renseigner le texte de remplacement. Pressez **entrée** autant de fois que nécessaire (le nombre d'occurences du texte sélectionné apparaît dès le départ).
[^2]: un autre bon exemple d'utilité aurait été une modification de plusieurs props dans un composant React en une seule fois.

2. Déplacer/copier une ou plusieurs lignes de code.
Très simplement, placez-vous sur la ligne à déplacer (ou sélectionnez un bloc de lignes) et combinez **ALT + ⬆️ ou⬇️** selon que vous voulier monter ou descendre dans votre code. C'est la fin des copier/coller pour déplacer une balise HTML fermée par l'autocomplétion !
Si vous combinez **ALT + SHIFT + ⬆️ ou⬇️**  vous copierez cette fois la zone de texte sélectionnée.
>peut notamment s'avérer très utile en CSS pour reprendre tout un style, en changeant seulement le sélecteur, ou pour copier des zones **HTML** tout en les positionnant à l'endroit souhaité.



[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job.)

   [ES7+ React/Redux/React-Native snippets]: <https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets>