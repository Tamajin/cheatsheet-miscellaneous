## NODE NPM
1.	Initialise avec  commande :npm init (npm init -y = valeur par défaut)
2.	Répondre à une série de questions  création fichier package.json

3.	Installe module, tape : npm install nomDuModule

4.	Ne jamais versionner nodes_modules dans github

Ajouter node_modules au fichier .gitignore :
	# Dependency directories
	Nodes_modules/

Si tu clones un dépôt, exécuter npm install pour générer le dossier nodes_modules et ainsi installer toutes les dépendances.

Index.js
Const chalk = import(« chalk ») ;
Console.log(chalk.blue(« Hello, npm !)) ;
+ ajouter 
Type : module dans fichier package.json

Ajouter un “scripts” au sein du package.Json
Package.Json
“scripts”: {
“start”: “node index.js”
},

https://www.codecademy.com/learn/learn-node-js/modules/intro-to-node-js/cheatsheet
