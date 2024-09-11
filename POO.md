### Programmation Orientée Objet (POO)

#### Concepts Théoriques de la POO

La Programmation Orientée Objet (POO) est un paradigme de programmation qui utilise des "objets" pour modéliser des concepts du monde réel. Voici les concepts de base :

1. **Classes et Objets** :
   - **Classe** : C'est un modèle qui définit des propriétés et des méthodes communes à un type particulier d'objet. Par exemple, une classe `Voiture` peut avoir des propriétés comme `couleur`, `marque`, et `modèle`, et des méthodes comme `démarrer()` et `arrêter()`.
   - **Objet** : Une instance de la classe. Par exemple, `maVoiture` peut être un objet de la classe `Voiture`.

2. **Encapsulation** :
   - Principe de restreindre l'accès à certains composants d'un objet, ce qui est fait en définissant des propriétés et méthodes comme publiques, privées ou protégées.
   - **Public** : Accessible depuis n'importe où.
   - **Private** : Accessible uniquement depuis la classe elle-même.
   - **Protected** : Accessible depuis la classe elle-même et les classes dérivées.

3. **Héritage** :
   - Permet à une nouvelle classe d'hériter des propriétés et méthodes d'une classe existante. Par exemple, une classe `VoitureDeSport` peut hériter de `Voiture`.

4. **Polymorphisme** :
   - Capacité des objets de différents types de répondre à des méthodes spécifiques de manière appropriée. Cela peut être réalisé par des méthodes de même nom dans des classes différentes (redéfinition).

5. **Abstraction** :
   - Le processus de simplification en cachant les détails complexes et en exposant uniquement les fonctionnalités essentielles.

#### Application en PHP

PHP supporte pleinement la POO et offre des moyens de définir des classes, créer des objets, et appliquer les principes de la POO. Voici comment cela fonctionne en PHP :

1. **Définition d'une Classe et Création d'un Objet** :
   ```php
   class Voiture {
       // Propriétés
       public $couleur;
       public $marque;
       private $vitesse = 0;

       // Constructeur
       public function __construct($couleur, $marque) {
           $this->couleur = $couleur;
           $this->marque = $marque;
       }

       // Méthodes
       public function démarrer() {
           echo "La voiture démarre";
           $this->vitesse = 10;
       }

       public function arrêter() {
           echo "La voiture s'arrête";
           $this->vitesse = 0;
       }

       public function obtenirVitesse() {
           return $this->vitesse;
       }
   }

   // Création d'un objet
   $maVoiture = new Voiture("Rouge", "Toyota");
   $maVoiture->démarrer();
   echo $maVoiture->obtenirVitesse();  // Affiche 10
   ```

2. **Encapsulation** :
   ```php
   class CompteBancaire {
       private $solde = 0;

       public function déposer($montant) {
           if ($montant > 0) {
               $this->solde += $montant;
           }
       }

       public function retirer($montant) {
           if ($montant > 0 && $montant <= $this->solde) {
               $this->solde -= $montant;
           }
       }

       public function obtenirSolde() {
           return $this->solde;
       }
   }

   $compte = new CompteBancaire();
   $compte->déposer(100);
   $compte->retirer(50);
   echo $compte->obtenirSolde();  // Affiche 50
   ```

3. **Héritage** :
   ```php
   class Voiture {
       public $marque;
       public function __construct($marque) {
           $this->marque = $marque;
       }
       public function démarrer() {
           echo "La voiture démarre";
       }
   }

   class VoitureDeSport extends Voiture {
       public function démarrer() {
           echo "La voiture de sport démarre rapidement";
       }
   }

   $voitureSport = new VoitureDeSport("Ferrari");
   $voitureSport->démarrer();  // Affiche "La voiture de sport démarre rapidement"
   ```

4. **Polymorphisme** :
   ```php
   class Animal {
       public function faireDuBruit() {
           echo "L'animal fait du bruit";
       }
   }

   class Chien extends Animal {
       public function faireDuBruit() {
           echo "Le chien aboie";
       }
   }

   class Chat extends Animal {
       public function faireDuBruit() {
           echo "Le chat miaule";
       }
   }

   $animaux = [new Chien(), new Chat()];
   foreach ($animaux as $animal) {
       $animal->faireDuBruit();  // Affiche "Le chien aboie" puis "Le chat miaule"
   }
   ```

5. **Abstraction** :
   ```php
   abstract class Forme {
       abstract protected function aire();
   }

   class Cercle extends Forme {
       private $rayon;

       public function __construct($rayon) {
           $this->rayon = $rayon;
       }

       public function aire() {
           return pi() * $this->rayon * $this->rayon;
       }
   }

   $cercle = new Cercle(5);
   echo $cercle->aire();  // Affiche l'aire du cercle
   ```

La POO en PHP permet de structurer le code de manière claire, modulaire et réutilisable. En maîtrisant ces concepts, vous pouvez développer des applications complexes de manière plus efficace et maintenable.
