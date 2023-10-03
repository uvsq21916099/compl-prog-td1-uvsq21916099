# Compléments de programmation - TD 1
Nom, Prénom, No Etudiant, Nc
     > Répondre ici
## Remarques préliminaires
* Pour l'ensemble des TDs, vous créerez un compte individuel sur [github](https://github.com/) si vous n'en possédez pas déjà un.
Vous nommerez ce compte de la façon suivante: `uvsq<MonNuméroÉtudiant>`.
Par exemple, pour un étudiant de numéro *21601234*, le compte sera `uvsq21601234`.
* Les commandes `git` sont à taper en ligne de commande dans un *shell*.
* Vous pouvez utiliser l'IDE de votre choix.
Sur le cartable numérique, [Eclipse](www.eclipse.org), [IntelliJ IDEA](http://www.jetbrains.com/idea/) et [Visual Studio Code](https://code.visualstudio.com/) sont installés.
* Vous répondrez aux questions directement dans ce fichier en complétant les emplacements correspondants.
Ajoutez ensuite ce fichier au dépôt `git`.

## Partie I (à faire durant le TD) : découverte de `git`
Dans cet exercice, vous créerez une classe `Fraction` représentant un nombre rationnel et une classe `Main` qui testera les méthodes de la classe `Fraction` **avec des assertions** (cf. [Utilisation d'assertions](https://koor.fr/Java/Tutorial/java_assert.wp)).
À chaque étape, consultez le statut des fichiers du projet (`git status`) ainsi que l'historique (`git log`).

1. Sur la forge, créez le dépôt (_repository_) `SimpleFraction`;
En terme de *commits*, quelle différence constatez-vous entre cocher une (ou plusieurs) des cases *Initialize this repository with* et n'en cocher aucune ?
    > si on coche cette case, le dépot s'initialise avec un fichiers README

    *Pour la suite, ne cochez aucune de ces cases*.
1. Localement, configurez `git` avec votre nom (`user.name`) et votre email (`user.email`) (cf. [Personnalisation de Git](https://git-scm.com/book/fr/v2/Personnalisation-de-Git-Configuration-de-Git));
    ```bash
    git config --global user.name
    git config --global user.email
    ```
1. Initialisez le dépôt `git` local pour le projet (cf. [Démarrer un dépôt Git](https://git-scm.com/book/fr/v2/Les-bases-de-Git-D%C3%A9marrer-un-d%C3%A9p%C3%B4t-Git));
    ```bash
    git init
    ```
1. Dans votre IDE, créez la classe `Fraction` (vide pour le moment) et la classe `Main` (avec un simple affichage) dans le projet (cf. [Méthode `main`](https://docs.oracle.com/javase/specs/jls/se19/html/jls-12.html#jls-12.1.4));
Vérifiez que le projet compile et s'exécute dans l'IDE;
Validez les changements (cf. [Enregistrer des modifications dans le dépôt](https://git-scm.com/book/fr/v2/Les-bases-de-Git-Enregistrer-des-modifications-dans-le-d%C3%A9p%C3%B4t));
    ```bash
    fichier Fraction :
    public class Fraction {
    }

    fichier Main :
    public class Main {
    public static void main(String[] args){
        System.out.println("Hello !");
        }
    }

    git commit -m "Fraction"
    ```
1. Ajoutez la méthode `toString` à la classe `Fraction` (cf. [`Object.toString`](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/lang/Object.html#toString())) qui retournera la chaîne `"Je suis une fraction."` et modifiez la classe `Main` en conséquence;
Validez les changements;
    ```Java
    on ne peut pas appeler la fonction toString() car il existe déja une fonctioon native portant le même nom dans java

    public class Fraction {
    public static String quisuije(){
        return "Je suis une fraction";
        }
    }

    public class Main {
    public static void main(String[] args){
        String jesui = Fraction.quisuije();
        System.out.println(jesui);
        }
    }
    ```
1. Publiez vos modifications sur le dépôt distant (cf. [Travailler avec des dépôts distants](https://git-scm.com/book/fr/v2/Les-bases-de-Git-Travailler-avec-des-d%C3%A9p%C3%B4ts-distants));
Vous utiliserez le protocole `https` pour cela;
Vérifiez avec le navigateur;
    ```bash
    git add -A
    git commit -m "Premier depot"
    git remote add Fractions https://github.com/uvsq21916099/Fractions.git
    git push
    ```
1. Sur la forge, ajoutez un fichier de documentation `README.md`.
Quelle syntaxe est utilisée pour ce fichier ?
    > un fichier markdown
1. Récupérez localement les modifications effectuées sur la forge.
    ```bash
    git log
    ```
1. Ajoutez les répertoires et fichiers issus de la compilation aux fichiers ignorés par `git` (cf. [`.gitignore` pour Java](https://github.com/github/gitignore/blob/main/Java.gitignore));
    ```bash
    Fraction.class
    Main.class
    ```
1. Retirez les fichiers de configuration de l'IDE du projet;
    ```bash
    VSCODE ne créé pas de fichiers
    ```
    Ajoutez-les aux fichiers ignorés par `git`.
    ```bash
    ref questions avant
    ```
1. Configurez l'accès par clé publique/clé privée à la forge (cf. [Connecting to GitHub with SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)).
    > Expliquez la procédure de façon synthétique

## Partie II (à faire durant le TD) : compléter la classe `Fraction`
Dans cet partie, vous compléterez les classes `Fraction` et `Main`.
Un exemple d'interface pour une telle classe est donné par la classe [`Fraction`](http://commons.apache.org/proper/commons-math/javadocs/api-3.6.1/org/apache/commons/math3/fraction/Fraction.html) de la bibliothèque [Apache Commons Math](http://commons.apache.org/math/).

Vous respecterez les consignes ci-dessous :
* chaque méthode de `Fraction` sera testée dans `Main` **avec des assertions** (cf. [Utilisation d'assertions](https://koor.fr/Java/Tutorial/java_assert.wp));
* à la fin de chaque question, consultez le statut des fichiers du projet (`git status`) ainsi que l'historique (`git log`) puis validez les changements.

1. Ajoutez les attributs représentants le numérateur et le dénominateur (nombres entiers).
    ```Java
    public class Fraction {
        int denominateur;
        int numerateur;
    }
    ```
1. Ajoutez les constructeurs (cf. [Constructor Declarations](https://docs.oracle.com/javase/specs/jls/se19/html/jls-8.html#jls-8.8)) suivants :
    * initialisation avec un numérateur et un dénominateur,
    * initialisation avec juste le numérateur (dénominateur égal à _1_),
    * initialisation sans argument (numérateur égal _0_ et dénominateur égal à _1_),
    ```Java
    Fraction(int numerateur,int denominateur) {
        this.numerateur = numerateur;
        this.denominateur = denominateur;
    }
    Fraction(int numerateur) {
        this.numerateur = numerateur;
        this.denominateur = 1;
    }
    Fraction() {
        this.numerateur = 0;
        this.denominateur = 1;
    }
    public static String quisuije(){
        return "Je suis une fraction";
    }
    
    Fraction y = new Fraction(0,1);
    Fraction x = new Fraction();
    assert x.getNumerateur() == y.getNumerateur();
    assert x.getDenominateur() == y.getDenominateur();

    Fraction y1 = new Fraction(4,1);
    Fraction x1 = new Fraction(4);
    assert x1.getNumerateur() == y1.getNumerateur();
    assert x1.getDenominateur() == y1.getDenominateur();


    ```
1. Ajoutez les fractions constantes ZERO (0, 1) et UN (1, 1) (cf. [Constants in Java](https://www.baeldung.com/java-constants-good-practices)),
    ```Java
    final Fraction ZERO = new Fraction();
    final Fraction UN = new Fraction(1);
    ```
1. Ajoutez une méthode de consultation du numérateur et du dénominateur (par convention, en Java, une méthode retournant la valeur de l'attribut `anAttribute` est nommée `getAnAttribute`),
    ```Java
    public int getNumerateur() {
        return this.numerateur;
    }

    public int getDenominateur() {
        return this.denominateur;
    }
    ```
1. Ajoutez une méthode de consultation de la valeur sous la forme d'un nombre en virgule flottante (méthode `doubleValue()`) (cf. [`java.lang.Number`](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/lang/Number.html)),
   ```Java
    Fraction x = new Fraction(5,8);
    assert x.doubleValue() == 0.625;


    ```
1. Ajoutez une méthode permettant l'addition de deux fractions (la méthode `add` prend en paramètre *une* fraction et *retourne* la somme de la fraction courante et du paramètre),
   ```Java
    Fraction x = new Fraction(2,4);
    Fraction y = new Fraction(3,4);

    Fraction p = new Fraction(5,4);

    Fraction res = x.add(y);
    assert res.doubleValue() == p.doubleValue();
    ```
1. Ajoutez le test d'égalité entre fractions (deux fractions sont égales si elles représentent la même fraction réduite) (cf. [`java.lang.Object.equals`](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/lang/Object.html#equals(java.lang.Object))),
   ```Java
    assert x.doubleValue() == y.doubleValue();
    
    ```
1. Ajoutez la comparaison de fractions selon l'ordre naturel (cf. [`java.lang.Comparable`](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/lang/Comparable.html)).
   ```Java
    Fraction x = new Fraction(4,1);
    Fraction y = new Fraction(8,2);
    assert x.equals(y);
    ```
1. Faites hériter votre classe `Fraction` de la classe [`java.lang.Number`](https://docs.oracle.com/en/java/javase/19/docs/api/java.base/java/lang/Number.html) et complétez les méthodes
   ```Java
    // Vérifiez avec le code ci-dessous
    Number aNumber = java.math.BigDecimal.ONE;
    Number anotherNumber = new Fraction(1, 2);
    assert java.lang.Math.abs(aNumber.doubleValue() + anotherNumber.doubleValue() - 1.5) < 1E-8;
    ```

## Partie III (à faire à la maison) : révisions et perfectionnement *shell* et *IDE*
### Maîtriser le *shell* de commandes
L'objectif de cet exercice est de vous faire réviser/découvrir les commandes de base du *shell* de votre machine.
Vous pouvez répondre en utilisant le shell de votre choix (*bash*, *Powershell*, …).
Pour répondre à ces questions, vous devez effectuer les recherches documentaires adéquates (livre, web, …).

1. Quel OS et quel shell de commande utilisez-vous ?
    > Répondre ici
1. Quelle commande permet d'obtenir de l'aide ?
Donnez un exemple.
    ```bash
    # Répondre ici
    ```
1. Donnez la ou les commandes shell permettant de
    1. afficher les fichiers d'un répertoire triés par taille (taille affichée lisiblement)
        ```bash
        # Répondre ici
        ```
    1. compter le nombre de ligne d'un fichier
        ```bash
        # Répondre ici
        ```
    1. afficher les lignes du fichier `Main.java` contenant la chaîne `uneVariable`
        ```bash
        # Répondre ici
        ```
    1. afficher récursivement les fichiers `.java` contenant la chaîne `uneVariable`
        ```bash
        # Répondre ici
        ```
    1. trouver les fichiers (pas les répertoires) nommés `README.md` dans une arborescence de répertoires
        ```bash
        # Répondre ici
        ```
    1. afficher les différences entre deux fichiers textes
        ```bash
        # Répondre ici
        ```
1. Expliquez en une ou deux phrases le rôle de ces commandes et dans quel contexte elles peuvent être utiles pour un développeur.
    * `ssh`
        > Répondre ici
    * `screen`/`tmux`
        > Répondre ici
    * `curl`/[HTTPie](https://httpie.org/)
        > Répondre ici
    * [jq](https://stedolan.github.io/jq/)
        > Répondre ici

### Découverte de votre *IDE*
Dans cet exercice, vous expliquerez en quelques phrases comment vous réalisez les actions ci-dessous dans votre IDE.
Vous pouvez choisir l'IDE/éditeur de texte de votre choix.
Pour réaliser cette exercice, vous devez bien évidemment vous reporter à la documentations de l'IDE ([IntelliJ IDEA](https://www.jetbrains.com/help/idea/discover-intellij-idea.html#developer-tools), [Visual Studio Code](https://code.visualstudio.com/docs), [Eclipse](https://help.eclipse.org/2020-09/index.jsp), …).

1. Quels IDE ou éditeurs de texte utilisez-vous pour le développement Java ?
    > Répondre ici

    Pour la suite, ne considérez que l'un de vos choix.
1. Comment vérifier/définir que l'encodage utilisé est *UTF-8* ?
    > Répondre ici
1. Comment choisir le JDK à utiliser dans un projet ?
    > Répondre ici
1. Comment préciser la version Java des sources dans un projet ?
    > Répondre ici
1. Comment ajouter une bibliothèque externe dans un projet ?
    > Répondre ici
1. Comment reformater un fichier source Java ?
    > Répondre ici
1. Comment trouver la déclaration d'une variable ou méthode ?
    > Répondre ici
1. Comment insérer un bloc de code prédéfini (*snippet*) ?
    > Répondre ici
1. Comment renommer une classe dans l'ensemble du projet ?
    > Répondre ici
1. Comment exécuter le programme en lui passant un paramètre en ligne de commande ?
    > Répondre ici
1. Comment déboguer le programme en visualisant le contenu d'une ou plusieurs variables ?
    > Répondre ici
1. Quels paramètres ou fonctionnalités vous semblent particulièrement importants/utiles pour le développement Java ?
    > Répondre ici