# Cheat Sheet Java
## Structure d'un programme Java
### Méthode Main
```Java
static void Main(String args[]){
    //Ici on peut écrire du code qui sera executé
}
```
## Bases de l'algorithmie
### Variables
Une variable est une case mémoire qui peut contenir une donnée.
En Java, cette donnée est dite “fortement typée”, c’est à dire qu’une fois que l’on a définit son type, elle ne peut changer.
Voici une liste (non exhaustive) des types les plus couramment utilisés :
* Les entiers : int (avec des déclinaisons : byte, short, long)
* Les décimaux : double
* Les flottants : float (nombre à virgule flottante, c’est compliqué..)
* Les caractères : char
* Les chaînes de caractères : String
* ...

Pour déclarer (créer) une variable, il faut donc spécifier son type, mais aussi son nom.
```Java
int variable; // Variable de type int qui s'appelle variable
```
Pour instancier (donner une valeur) à une variable, on peut le faire à 2 moments différents : au moment de la création de la variable, après la création de la variable.
```Java
int variable = 5; // Instanciation et déclaration en même temps
int variable;
var = 5; // Instanciation après la déclaration
```
Il est important de retenir qu’une variable qui n’a pas de valeur n’est pas utilisable. Par exemple : 
```Java
int variable;
System.out.println(var); // Cette ligne renvoie une erreur car la variable n'a pas été initialisée.
```
### Opérations sur les variables de base
#### Nombres (Entiers, Décimaux)
On peut effectuer les opérations de base sur les nombres :
* Addition / Soustraction
```Java
int x = 5+6; // Equivalent à x = 11
int y = 41 - 3; // Equivalent à y = 38
int z = x + y; // Equivalent à z = 11 + 38
int z = z + z // Equivalent à z = 49 + 49. On note ici l'utilisation de la même variable à gauche et à droite de l'égalité. C'est tout à faire possible et c'est même souvent utilisé ! En effet, on "met à jour" la variable z en utilisant son ancienne valeur.
```

* Multiplication / Division
```Java
int a = 3 * 4; // a contient 12.
int x = 4/5; // On s'attend à avoir un résultat à virgule, non ? Attention ! int ne peut contenir que des nombres entiers. Une division avec des nombres entiers correspond à une division euclidienne dont on récupère le quotient. Ici x contient donc 0.
double y = 4/5; //Bon cette fois on a ce qu'on veut.. NON ?! Attention ! Double peut contenir des nombres à virgule, mais l'opération (4/5) ne contient que des nombres entiers. y contient donc 0.
double z = 4.0/5.0; //Cette fois c'est la bonne ! 4.0 et 5.0 sont des doubles et la division est donc juste. z contient 0.8.
```
* Modulo
La division de nombre entiers nous donne le quotient mais il y a des fois, pour des raisons algorithmiques, on souhaite récupérer le reste de cette division.
```Java
int a = 5%4; // a contient 1.
int b = 10%2 // b contient 0.
```
#### Chaînes de caractères
```Java
String a = "Kono DIO da !";
System.out.print.ln(a); // Imprime Kono DIO da ! dans la console.
String b = "Yare Yare Daze.";
String c = a + " " + b; // c contient Kono DIO da ! Yare Yare Daze.
```
#### Affichage
On l'a vu plusieurs fois avant mais je le rappelle ici 
```Java
System.out.print("Truc à afficher"); // Sans saut de ligne à la fin
System.out.print.ln("Truc à afficher"); // Avec saut de ligne à la fin
```
### Structure de contrôle
En algorithmie, on a souvent besoin de faire des choix dépendants des valeurs de nos variables.
```Java
int a = 4; // On définit une variable a qui contient 4
if (a % 2 == 0){ // SI le reste de la division euclidienne de a par 2 est égal à 0
    // On execute le code ici
    a = a/2;
} else {
    // Sinon on execute le code ici
    a = 2*a;
}
```
On peut imposer différentes conditions sur nos expressions :
* Les valeurs sont elles égales ? a == b
* La première valeur est elle inférieure à la deuxième valeur ? a < b
* La première valeur est elle inférieure ou égale à la deuxième valeur ? a <= b
* La première valeur est elle supérieure à la deuxième valeur ? a > b
* La première valeur est elle supérieure ou égale à la deuxième valeur ? a >= b

Ces différentes conditions sont en réalité des expressions booléennes que l'on peut combiner.
Je vous met ici un tableau qui récapitule les différentes combinaisons possibles.
![Algebre Boolean](/algebre_boole.png)
0 veut dire faux et 1 veut dire vrai
* "+" veut dire "ou" et en Java on écrit "||"
* "." veut dire "et" et en Java on écrit "&&"
* "-" au dessus veut dire "non" et en Java on écrit "!" devant la proposition

### Boucles
Lorsque l'on veut répeter plusieurs fois la même instruction, on utilise des boucles.
#### While
While ("tant que" dans la langue de Molière) est utile lorsque l'on ne sait pas exactement combien de fois on veut repeter l'action, mais que l'on connait la condition d'arrêt de la boucle.
```Java
int a = 4;
boolean fini = false;
while(fini == false){ // Tant que le booleen fini vaut false
    a = a/2;
    if(a == 1){
        fini = true; // On change la valeur du booléen fini pour invalider la condition de la boucle et donc en sortir
    }
}
```
#### For
For ("pour") est utile lorsque l'on sait combien de fois on veut repeter l'action
```Java
int a = 0;
for(int i = 1; i <= 10; i++){ // On initialise i à 1 et s'il est inférieur ou égal à 10 alors on éxécute le code entre {} puis i est incrémenté
    a = a+i;
}
```
## Tableaux
### Tableaux 1D
### Tableaux 2D
## Orienté Objet
### Qu'est-ce qu'un objet ?
### Attributs
### Méthodes
### Structures de données
### Héritage et Polymorphisme
### IHM

