## P.O.O.
### ((Programmation Orientée Objet))

+ Elle fournit uniquement une syntaxe plus simple pour créer des objets et manipuler l'héritage et ainsi éviter de répéter du code.
+ Définition : Une classe contient des attributs et des méthodes pour décrire l’objet.
+ Syntaxe : exemple
    *  définir le **constructor** avec ses attributs.
    *  déclarer avec **“this”** les attributs de la classe.
    *  créer une ou des **méthodes**.

```javascript
      class Person {
        construtor(lastName, firstName) {
            this.lastName = lastName;
            this.firstName = firstName;
        }

      sayHello() {
        console.log(`My name is ${this.firstName}`);
        }
      }
```

+ pour créer une instance d’une classe : 

```javascript
      const john = new Person('John', 'Smith');
      john.sayHello();
```

+ pour créer une classe **enfant** à partir d’une classe existante → **“extends”**.

```javascript
      class Character{
        constructor(name, level) {
            this.name = name;
            this.level = level;
        }
      }

      class Enemy extends Character{
        constructor(name, level, emoji, attackName) {
            super(name, level);
            this.emoji = emoji;
            this.attackName =  attackName;
            this.enemy = true;
      }

        attack() {
            return ${this.name} ${this.attackName} you!;
        }
      }

      const spider = new Enemy("Spider", 1, "🕷", "bites");
      console.log(spider.name);
```
+ **“super”** pour reprendre les attributs de la classe parents
+ Il est possible de **surcharger** la classe en lui affectant 
    *   de **nouveaux attributs** : this.__*** = ***__
    *   de  **nouvelles méthodes**.