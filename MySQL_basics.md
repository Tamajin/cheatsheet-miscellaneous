# MySQL 1: les bases <img src="assets/mysql-logo.png" width="200" heigh="fit-content">


## 1. Vocabulaire

**SGBDR** (**S**ystème de **G**estion de **B**ase de **D**onnées **R**elationnelle) :  logiciel permettant de créer et administrer des bases de données. Tu peux créer dedans autant de bases de données que tu le souhaites. Il existe de nombreux SGBDR, comme MySQL, PostgreSQL, Oracle, etc.

**Base de données** : conteneur permettant de stocker des informations diverses, de manière structurée, dans des tables.

**Table** : sous-unité d’une base de données, contenant des informations de même type, que l'on peut regrouper par des propriétés communes, ce qui permet de les structurer de manière cohérente.

**Champ** : propriété qui caractérise chaque donnée d’une table. Les champs possèdent des caractéristiques précises (type, longueur, nullable, unicité, etc.).

**Clé** **primaire** : C’est un identifiant **unique** qui permet d’identifier rapidement un enregistrement. La clé primaire est constituée par un (parfois plusieurs) champ(s).

><font color="blue">Le plus souvent, le champ servant de clé primaire sera de type entier et auto-incrémenté (de 1 à N) à chaque nouvelle insertion de données dans la table (l’auto-incrémentation est une technique simple pour obtenir un identifiant unique), mais il est possible d’avoir des clés primaires sous d’autres formats.</font>

**Tuple** : valeurs d’une seule ligne d’une table.

><font color="orange">Si tu imagines une base de données comme un tableur, la table serait une feuille de tableur, le champ serait une colonne, le tuple une ligne. Par convention, le nom des tables et champs s’écrivent généralement en anglais, en snake_case (underscores séparant les mots). Les noms de tables sont toujours au singulier.</font>

**Primary** **Key** : Dans le langage SQL la “PRIMARY KEY”, autrement la clé primaire, permet d’identifier chaque enregistrement dans une table de base de données. Chaque enregistrement de cette clé primaire doit être UNIQUE et ne doit pas contenir de valeur NULL.

La clé primaire est un index, chacune des tables ne peut contenir qu’une seule clé primaire, composée d’une ou plusieurs colonnes.

L’usage le plus fréquent consiste à créer une colonne numérique qui s’incrémente automatiquement à chaque enregistrement grâce à AUTO_INCREMENT.


## 2. Créer et utiliser une base de données

Avant toute choses, il faut se connecter à mysql. Dans le terminal:
```
mysql -u <identifiant> -p
```
Votre mot de passe vous sera alors demandé.

Étape 1 : créer une base de donnée:

**syntaxe**
```mysql
mysql> CREATE DATABASE nom_de_database;
```

**exemple**
On veut créer une base de donnée sur notre session Click & Mousse à la Wild Code School:
```
mysql> CREATE DATABASE click_and_mousse;
```

Étape 2 : utiliser cette base de donnée pour pouvoir la manipuler par la suite:

**syntaxe**
```
mysql> USE nom_de_database;
```

**exemple**
Pour pouvoir manipuler notre base de données(BDD) Clic & Mousse, il faut comment par taper la commande ci dessous:
```
mysql> USE click_and_mousse;
```

Étape 3 : créer un ou plusieurs tableaux dans cette BDD

**syntaxe**
```
mysql> CREATE TABLE `nom_de_tableau` (
    `champ` TYPE ET REGLES
);
```

**exemple**
On reprend notre base de données Clic & Mousse. On souhaite créer un tableau `wilders` avec:
-un champ `id` unique non null
-un champ `firstname` et `lastname` avec 50 caractères maximum et obligatoires (donc non null).
Le champ `id` nous servira de clé primaire.

```
mysql> CREATE TABLE `wilders` (
    `id` INT NOT NULL AUTO_INCREMENT,
    `firstname` VARCHAR(50) NOT NULL,
    `lastname` VARCHAR(50) NOT NULL,
    PRIMARY KEY (`id`)
);
```

## 3. Quelques commandes dans mySQL

**SHOW** : la commande `SHOW` permet d’afficher de nombreux types d’informations sur ce que contient ton SGBDR. Par exemple :
`SHOW DATABASES;` permet de lister toutes les BDD et `SHOW TABLES;` permet de lister toutes les tables de la base de données actuellement sélectionnée.

**DESCRIBE** : permet d’afficher des informations détaillées sur les colonnes d’une table.

**ALTER** :  il existe de nombreuses commandes commençant par ALTER, qui te permettent de modifier la structure d’une BDD/Table existante. En voici quelques exemples:`

-ajouter une colonne à un tableau:
```
mysql> ALTER TABLE nom_table
    ADD nom_colonne type_donnes;
```

-supprimer une colonne:
```
mysql> ALTER TABLE nom_table
    DROP nom_colonne;
```

-modifier une colonne (changer le type de colonne par exemple):
```
mysql> ALTER TABLE nom_table
    MODIFY nom_colonne type_donnees;
```

## 4. Manipulation d'une base de données

Une fois sur une base de données, voici quelques commandes pour lire, ajouter ou modifier les données d'une table:


**SELECT**

Syntaxe | Action | Exemple
--------|-------|---------
mysql> SELECT `*` FROM `<table>`; | selectionner tout les champs dans un tableau | mysql> SELECT `firstname` FROM `wilders`;
mysql> SELECT `<champs>` FROM `<table>`; | selectionner un ou plusieurs champs précis dans un tableau | mysql> SELECT `firstname` FROM `wilders`;
--------| **SELECT avec AS (alias)** | ------
mysql> SELECT `<champs>` AS `<alias>` FROM `<table>`; | selectionner un ou plusieurs champs précis dans un tableau en créant un alias (renommage temporaire) | mysql> SELECT `firstname` AS `wilders_first_name` FROM `wilders`;
--------| **SELECT avec WHERE** | ------
mysql> SELECT `<champs>` FROM `<table>` WHERE `<champ>` = `<condition>`; | selectionner dans un ou plusieurs champs précis, une liste de tuples répondant à une condition | mysql> SELECT `firstname`,`lastname`  FROM `wilders` WHERE `firstname`=`"amina"`;
--------| **SELECT avec WHERE LIKE** | ------
mysql> SELECT `<champs>` FROM `<table>` WHERE `<champ>` LIKE `<string>%`; (commencant par le string) *ou* mysql> SELECT `<champs>` FROM `<table>` WHERE `<champ>` LIKE `%<string>`; (terminant par le string) | selectionner dans un ou plusieurs champs précis, une liste de tuples répondant à une condition prenant en compte le début ou la fin d'une chaîne de caractères | mysql> SELECT `firstname`,`lastname`  FROM `wilders` WHERE `firstname` LIKE `%mina`;
--------| **SELECT avec WHERE BETWEEN** | ------
mysql> SELECT `<champs>` FROM `<table>` WHERE `<champ>` BETWEEN `<string> ou <number> ou <date>` AND `<string> ou <number> ou <date>`; | selectionner dans un ou plusieurs champs précis, une liste de tuples dans un intervalle de données de type _chaine de caractères_, _nombres_ ou _dates_ | mysql> SELECT `firstname`,`lastname`  FROM `wilders` WHERE `birthday` BETWEEN `'1970-01-01'` AND `'1995-01-01'`;
--------| **SELECT avec LIMIT et LIMIT OFFSET** | ------
mysql> SELECT `<champs>` FROM `<table>` LIMIT `<number_of_results>`; | selectionner dans un ou plusieurs champs précis, un nombre de tuples précis en partant du premier tuple | mysql> SELECT `firstname`,`lastname`  FROM `wilders` LIMIT 5;
mysql> SELECT `<champs>` FROM `<table>` LIMIT `<nombre_de_resultats>` OFFSET `<a_partir du_nombre>`; | selectionner dans un ou plusieurs champs précis, un nombre de tuples précis à partir d'un tuple précis (le 10ième, le 20ième, etc...) | mysql> SELECT `firstname`,`lastname`  FROM `wilders` LIMIT 5 OFFSET 10;
--------| **SELECT avec ORDER BY  ASC et DESC** | ------
mysql> SELECT `<champs>` FROM `<table>` ORDER BY `<champ>` DESC;  | selectionner dans un ou plusieurs champs précis, et trier les tuples en ordre croissant `ASC` ou décroissant `DESC` | mysql> SELECT `firstname`,`lastname`  FROM `wilders` ORDER BY `firstname` ASC;


**INSERT**

Syntaxe | Action | Exemple
--------|-------|---------
mysql> INSERT INTO `<table>` (`<champ_1>`, `<champ_2>`, ...) VALUES (`<valeur1_champ_1>`, `<valeur1_champ_2>`), (`<valeur2_champ_1>`, `<valeur_champ_2>`); | insérer des tuples dans un tableau  | mysql> INSERT INTO `wilders` (`firstname`,`lastname`) VALUES (`Simon`,`Jérémie`), (`Odile`,`Deray`), (`Serge`,`Karamazov`);


**UPDATE**

Syntaxe | Action | Exemple
--------|-------|---------
mysql> UPDATE `<table>` SET `<champ_1>`=`<nouvelle_valeur>`, `<champ_2>`=`<nouvelle_valeur>`, etc ... WHERE `<conditions>`; | mettre à jour un tuple dans un tableau | mysql> UPDATE `wilders` SET `lastname`=`'Karamazov'` WHERE `firstname`=`'Odile'`;

>Attention à le jamais oublier le WHERE sinon la modification s'appliquera à l'ensemble des tuples.


**DELETE**

Syntaxe | Action | Exemple
--------|-------|---------
mysql> DELETE FROM `<table>` WHERE `<conditions>`; | supprimer des données précises | mysql> DELETE FROM `wilders` WHERE `firstname`=`'Simon'`;

>Attention à le jamais oublier le WHERE sinon la suppression s'appliquera à l'ensemble des tuples.


**TRUNCATE**

Syntaxe | Action | Exemple
--------|-------|---------
mysql> TRUNCATE `<table>`; | supprimer toutes les données d'un tableau, sans supprimer ce tableau | mysql> TRUNCATE `wilders`;
