# GLOSSAIRE

- [Général](#général)
- [Front-end](#front-end)
- [UX / UI](#ux-ui)
- [Architecture](#architecture)
- [Modélisation / Base de données](#modélisation--base-de-données)
- [Symfony](#symfony)
- [Sécurité](#sécurité)
- [RGPD](#rgpd)
- [SEO](#seo)
- [Gestion de projets / DevOps](#gestion-de-projets--devops)
- [English](#english)

## Général

1. **Quel est l’environnement à installer pour exécuter un script PHP ? Citer 2 exemples de logiciels permettant ce contexte.**
   - Exécuter un script PHP : mettre en place un environnement qui comprend l’installation d’un logiciel comme Laragon ou WampServer.
   - Dans un contexte de développement web, ces deux plateformes sont adaptées à Windows et regroupent les outils nécessaires à l'exécution d’un script PHP : Serveur web (Apache), Base de données (MySQL) et PHP comme langage de programmation côté serveur.

2. **Qu’est-ce qu’un algorithme ?**
   - Un algorithme est une série d'instructions que l’on suit pour résoudre un problème ou accomplir une tâche. C’est une liste d’étapes à suivre pour atteindre un résultat.

3. **Qu’est-ce qu’une variable ? Par quel symbole est préfixée une variable en PHP ?**
   - Une variable est un espace de mémoire/stockage qui comprend un nom, une valeur, et éventuellement un type. Les variables sont utilisées pour stocker des informations qui peuvent changer au cours de l'exécution d'un programme.
   - En PHP, une variable est préfixée par le symbole `$`.

4. **Qu’est-ce que la portée d’une variable ?**
   - La portée d'une variable est le contexte dans lequel elle est définie, la zone de code où elle a été déclarée. PHP possède une portée de fonction et une portée globale. Toute variable définie en dehors d'une fonction est limitée à la portée globale.

5. **Qu’est-ce qu’une constante ? Quelle est la différence avec une variable ?**
   - Une constante est une valeur fixe qui ne change pas durant l'exécution d'un programme. Contrairement à une variable, une fois qu'une constante est définie, sa valeur ne peut pas être modifiée.

6. **Qu’est-ce qu’une superglobale, combien en existent-ils et donner un exemple d’utilisation**
   - Les superglobales sont des variables prédéfinies en PHP : toujours accessibles quelle que soit leur portée, accessibles depuis n’importe quelle fonction, classe ou fichier et sans manipulation particulière.
   - Il en existe 9 principales : `$_GET`, `$_POST`, `$_REQUEST`, `$_SERVER`, `$_FILES`, `$_ENV`, `$_COOKIE`, `$_SESSION`, `$_GLOBALS`
   - Par exemple, dans un fichier d'action, nous pouvons utiliser la variable `$_GET` pour collecter la valeur des champs de saisie :
     ```html
     <html>
     <body>
     Welcome <?php echo $_GET["name"]; ?><br>
     Your email address is: <?php echo $_GET["email"]; ?>
     </body>
     </html>
     ```

7. **Quels sont les différents types (primitifs) que l’on peut associer à une variable en PHP ? Les citer et en donner des exemples (ne pas oublier le type d’une variable sans valeur)**
   - Les types primitifs associables à une variable en PHP :
     - Integer : Nombres entiers, `25`
     - Float : Nombres réels, `3.14`
     - String : Chaînes de caractères, `"Bonjour"`
     - Boolean : Valeurs booléennes `true` ou `false`
     - Array : Tableaux (indexés ou associatifs), par exemple `array(1, 2, 3)` ou `array("nom" => "Alice")`
     - Object : Instances de classes définies par l'utilisateur
     - NULL : Absence de valeur, par exemple `NULL`

8. **Existe-t-il plusieurs types de tableaux en PHP, si oui lesquels ?**
   - Il existe plusieurs types de tableaux en PHP :
     - Tableaux indexés : utilisent des indices numériques
     - Tableaux associatifs : utilisent des clés personnalisées (généralement des chaînes de caractères)
     - Tableaux multidimensionnels : contiennent des tableaux imbriqués à l'intérieur
     - Tableaux vides : ne contiennent pas d’élément, mais peuvent être remplis
     - Tableaux mixtes : combinent des indices numériques et des clés associatives

9. **Quelles sont les différentes structures de contrôles qu’il existe en algorithmie ? Donner un exemple pour chacune d’entre elles**
   - Il existe 5 principales structures de contrôle en algorithmie :
     - **Structure conditionnelle (ou de sélection)** :
       - Permet de choisir une ou plusieurs actions en fonction de conditions.
       - Exemples : `if`, `if-else`, `switch`.
     - **Structure de répétition (ou itérative)** :
       - Permet de répéter un bloc d'instructions plusieurs fois tant qu'une condition est vraie.
       - Exemples : `while`, `for`, `do-while`.
     - **Structure de saut (ou contrôle de flux)** :
       - Permet de modifier l'exécution du programme en sortant d'une boucle ou d'une fonction de manière anticipée.
       - Exemples : `break`, `continue`, `return`.
     - **Structure de sélection multiple (switch)** :
       - Permet de tester plusieurs conditions pour exécuter une action selon la valeur d'une variable donnée.
       - Exemple : `switch-case`.
     - **Structure de fonction/procédure** :
       - Permet d’organiser un programme en sous-programmes ou blocs réutilisables (fonctions ou procédures).
       - Exemples : Définition de fonctions ou procédures (par exemple `function` en PHP).

10. **Quelle est la fonction PHP permettant de demander la longueur d’une chaîne de caractères ?**
    - La fonction PHP permettant de demander la longueur d’une chaîne de caractères est `strlen()`. Exemple :
      ```php
      $length = strlen($string);
      ```

11. **Qu’est-ce qu’une session ? Quelle fonction permet de démarrer une session en PHP ? Donner un exemple d’utilisation en PHP**
    - Une session en PHP permet de conserver des informations (ou des données) pendant la période de navigation de l’utilisateur, et permet de partager des données entre les pages web de manière automatique. C'est essentiel pour gérer des fonctionnalités comme la connexion d'un utilisateur ou le suivi d'un panier d'achats.
    - La fonction `session_start()` est utilisée pour démarrer une session. Elle doit être appelée au tout début de la page, avant toute sortie envoyée au navigateur.
    - Démarrage d’une session et stockage des infos dans la variable de session :
      ```php
      <?php
      // Démarre la session
      session_start();
      // Stocke des informations dans la session
      $_SESSION['username'] = 'Marie';
      $_SESSION['email'] = 'marie@exemple.com';
      // Redirige l'utilisateur vers la page suivante
      header('Location: page2.php');
      exit;
      ?>
      ```
      - Les données de session sont conservées sur le serveur, ce qui est plus sécurisé que les cookies côté client. Par défaut, les sessions PHP expirent après un certain temps d'inactivité (configurable dans le fichier `php.ini`).

12. **Qu’est-ce qu’un cookie ? Donner un exemple d’utilisation en PHP**
    - Un cookie est un petit fichier stocké sur le navigateur d'un utilisateur. Il contient des informations sous forme de paires clé-valeur et peut être utilisé pour stocker des données spécifiques à un utilisateur sur un site web.
    - Syntaxe de `setcookie()` :
      ```php
      setcookie(name, value, expiration, path, domain, secure, httponly);
      ```
    - Exemple d’utilisation :
      ```php
      <?php
      // Définir un cookie nommé "username" avec la valeur "Marie" qui expire dans 30 jours
      $cookie_name = "username";
      $cookie_value = "Marie";
      $expiration = time() + (30 * 24 * 60 * 60);  // Expiration dans 30 jours
      // Définir le cookie
      setcookie($cookie_name, $cookie_value, $expiration, "/");
      // Le symbole "/" signifie qu'il est accessible pour tout le domaine
      echo "Le cookie a été défini !";
      ?>
      ```

13. **Quelle est la différence entre les instructions `require` et `include` en PHP ?**
    - `require` : inclut le contenu d'un autre fichier appelé, et provoque une erreur bloquante s'il est indisponible.
    - `include` : inclut le contenu d'un autre fichier appelé, mais ne provoque pas d'erreur bloquante s'il est indisponible.
    - Exemple d’utilisation :
      ```php
      <?php require "fichier2.html"; ?>
      ```

14. **Comment effectuer une redirection en PHP ?**
      On peut utiliser la fonction `header()` de la manière suivante :
      
      ```php
      header("Location: http://www.homepage.com");
      exit(); ?>
       ```
      - ajouter exit() après header() permet d'arrêter l'exécution du script  

15.	Définir la partie « front-end » et « back-end » d’une application  
   - **Frontend et backend** sont des termes généraux qui regroupent logiquement les différentes technologies et **couches logicielles** d'une application ou d'un site.  
- La partie front-end s'intéresse à l'interface **visible** par l'utilisateur, celle avec laquelle il interagit directement.  
- À l'inverse, le back-end est toute la partie dite **'cachée'** à l'utilisateur, celle qui gère la logique, les données et l'interaction avec la **base de données**. c'est grâce au back-end que les informations sont traitées et envoyées au front-end.  

- **Front-end** : Partie visible, côté client (interface utilisateur). Techno courantes: **HTML**, **CSS**, **JavaScript**.  
- **Back-end** : Partie cachée, côté serveur (gestion des données et logique métier). Techno courantes:  
  Langages de programmation : **PHP**, **Python**, **Java**, **Ruby**, **Node.js**.  
  Base de données : **MySQL**, **PostgreSQL**, **MongoDB**.  
  Serveurs web : **Apache**, **Nginx**.  

16.	Définir le contrôle de version ? Qu’est-ce que Git ?  
Les outils de contrôle de versions permettent aux équipes de développement de gérer les changements apportés au code source au fil du temps.  
Ils permettent notamment de :  
- **Garder un historique complet** des changements apportés  
- **Revenir en arrière** et comparer les versions antérieures du code  
- **Corriger les erreurs** tout en minimisant les perturbations pour l'équipe  
- **Travailler sur des flux de changements indépendants** (branching et merges)  

**Git** est un système de contrôle de version (le plus largement utilisé).  
- Il est gratuit et **open-source**, c'est-à-dire qu'il est conçu pour être accessible au public à la consultation, modification et distribution.  
- Il est **décentralisé** : permet un travail **indépendant et désynchronisé** (il existe plusieurs dépots, sur plusieurs machines).  
**GitHub** est une plateforme web qui intègre les fonctionnalités de contrôle de version de Git afin de pouvoir les utiliser en **collaboration**.  

17.	Qu’est-ce qu’un CMS ? Citer au moins 2 exemples  
**CMS** est l'acronyme de Content Management System, c'est-à-dire système de gestion de contenu.  
- **logiciel en ligne** qui permet de créer, gérer, modifier facilement un **site web**.  
- ne nécessite pas de connaissances techniques en langage informatique.  
- adapté aux **sites vitrines et sites e-commerce** (woo-commerce :WP, **shopify** :CMS).  
- en 2024, près de 70% des sites web dans le monde utilisaient un système de gestion de contenu.  
- **WordPress**, leader des CMS dans le monde (+de 60%), représente +de 40% de l'ensemble des sites webs.  

## Front-end
18.	Définir HTML  
   - Le **HTML** (Hypertext Markup Language) définit la **structure** du frontend et les différents éléments du **DOM**  
   - Document Object Model (DOM) : interface de programmation normalisée par le **W3C**, modèle de document chargé dans le navigateur.  
   -  World Wide Web Consortium (W3C) : organisme international à but non lucratif. Son rôle est de définir les standards techniques liés au web.  

19.	Définir CSS  
   - Les feuilles de style en cascade (**CSS**) définissent le **style** d'une application Web, notamment la mise en page, les polices, les couleurs, le style visuel ainsi que la prise en charge de certaines **animations**  

20.	Définir Javascript  
   - **JavaScript** est un **langage de script**. Il ajoute une couche de **fonctionnalités dynamiques** en manipulant le DOM, il permet de créer et de contrôler des éléments dynamiques, pour rendre la **page interactive**.  

21.	Définir JSON. Dans quel contexte ce format est-il utilisé ?   
**JSON** (JavaScript Object Notation) est un **format de données textuel** conçu pour l'échange de données:  
- Facile à lire par les humains et à comprendre par les ordinateurs.  
- Très utilisé pour échanger des données entre un serveur et un navigateur web.  
- Prend en charge plusieurs types de données (objets, tableaux, chaines de car., booléens, null, nombres).  
**Cas d'utilisation** du format JSON :  
  - Transfert de données entre systèmes.  
  - Création d'un objet JSON à partir de données générées par l'utilisateur.  
  - Configuration d'applications.  
  - Simplification des modèles de données complexes.  
  - Fichiers de configuration et stockage de données.  
  
### 22. Peut-on interpréter du Javascript côté serveur ? Si oui, comment ?

Il est possible d'interpréter du JavaScript côté serveur comme s'il était un langage backend classique (comme PHP ou Python). On peut notamment utiliser **Node.js**, dont l'environnement permet d'exécuter du JavaScript en dehors du navigateur, directement sur un serveur.

---

### 23. Qu’est-ce qu’un sélecteur CSS ?

Les sélecteurs CSS sont des expressions qui permettent de cibler des éléments HTML présents sur une page web pour leur appliquer une règle CSS.

- **Sélecteur de type :**  
  HTML : `<a>Lien vers le site à cibler</a>`  
  CSS : `a { color : blue }`

- **Sélecteur de classe :**  
  HTML : `<p class="introduction">Introduction de l’article</p>`  
  CSS : `.introduction`

- **Sélecteur d'identifiant :**  
  HTML : `<nav  id="menu">Menu du site</nav>`  
  CSS : `#menu`

- **Sélecteur universel :**  
  CSS : `*`

---

### 24. Quelle balise HTML permet de créer un lien hypertexte ?

La balise HTML qui permet de créer un lien hypertexte est la balise `<a>`.  
La balise `<a>` seule ne suffit pas. Pour qu'elle fonctionne comme un lien hypertexte, il faut obligatoirement lui ajouter l'attribut `href` qui indique la destination du lien.

**Exemple :** `<a href="https://www.example.com">Cliquez ici</a>`

---

### 25. Qu’est-ce qu’une requête AJAX ?

Une requête **AJAX (Asynchronous JavaScript and XML)** est une technique qui permet de faire des requêtes HTTP (GET, POST, etc.) vers un serveur, de manière asynchrone, sans recharger la page web entière.  
Cela rend les applications web plus interactives et rapides.

1. JavaScript envoie une requête HTTP vers un serveur.  
2. Le serveur traite la requête et renvoie une réponse (généralement en JSON, XML, ou HTML).  
3. JavaScript met à jour une partie de la page web avec les nouvelles données sans recharger toute la page.

---

### 26. Quel sélecteur CSS permet de sélectionner tous les éléments d’une classe spécifique ? D’un identifiant spécifique ?

- Pour sélectionner tous les éléments d’une classe spécifique, on utilise le **sélecteur de classe** qui commence par un point (`.`) suivi du nom de la classe.
- Pour un identifiant spécifique, on utilise le **sélecteur d’identifiant** qui commence par un dièse (`#`) suivi du nom de l'identifiant.

---

### 27. Définir le responsive design

Le **responsive design** désigne une manière de concevoir des sites web (préalablement conçus pour un format desktop) qui deviennent parfaitement adaptés à tous les types et toutes les tailles d'écrans. Cela consiste à rendre un site web accessible et adaptable à tous les appareils (tablettes, smartphones, etc.) de façon automatique grâce à différentes techniques de développement (CSS, media queries, etc.).

---

### 28. Qu’est-ce que le templating ?

Le **templating** permet de créer des pages dynamiques en remplaçant des variables dans un modèle HTML par des données réelles. C'est très pratique pour générer des interfaces personnalisées en fonction d'un utilisateur ou d’un contenu.  
Cette création de “modèles” permet un processus de création d'un format ou d'une mise en page réutilisable pour présenter des données.

---

### 29. Qu’est-ce qu’une fonction anonyme en Javascript ?

Les **fonctions anonymes** sont des fonctions qui ne possèdent pas de nom. Elles sont souvent utilisées lorsqu’on n’a pas besoin de réutiliser une fonction ailleurs dans le script. Généralement, on utilise les fonctions anonymes lorsqu'elles sont appelées qu’à un seul endroit dans le code.

---

### 30. Quelle méthode JavaScript est utilisée pour ajouter un élément à la fin d'un tableau ?

Pour ajouter une valeur à un tableau, on utilise la méthode **`push()`**. Cette méthode retourne la longueur du tableau une fois les nouvelles valeurs ajoutées.  
La méthode `push()` peut prendre plusieurs valeurs comme arguments et accepte autant de valeurs qu’on le souhaite.

---

### 31. Qu’est-ce qu’un « media query » ?

Les **media queries** permettent de définir des règles CSS spécifiques qui s’appliquent uniquement lorsque certaines conditions sont remplies, telles que :
- La largeur de l'écran (responsive),
- La résolution,
- L'orientation (portrait/paysage),
- Les thèmes et contrastes (clair/sombre).

Elles sont définies à l’intérieur d’une règle `@media` dans une feuille de style CSS. Exemple :
```css
@media screen and (max-width: 768px) {
    body {
        background-color: lightblue;
    }
}
```

---

### 32. Qu’est-ce qu’un pseudo élément en CSS ?

Les **pseudo-éléments CSS** permettent de cibler une partie spécifique d’un élément HTML pour lui appliquer des styles.  
Il existe 4 pseudo-éléments recommandés par le W3C :
- `::first-letter`
- `::first-line`
- `::before`
- `::after`

À ne pas confondre avec les **pseudo-classes** comme `:hover` qui ciblent un état spécifique d’un élément.

---

### 33. Qu’est-ce que Bootstrap ? Donner d’autres exemples équivalents

**Bootstrap** est un framework CSS (frontend) composé d'un ensemble de fichiers CSS et JavaScript qui contiennent des règles prédéfinies pour créer des composants (boutons, formulaires, navigation, etc.).  
Les meilleures alternatives à Bootstrap sont **Tailwind CSS** (qui permet de construire des interfaces sur mesure directement dans le HTML) et **UIKit**.

---

### 34. Quand un formulaire HTML est créé, quelles sont les 2 méthodes qui peuvent lui être associées ? Donner la différence entre ces 2 méthodes

Les deux méthodes qui peuvent être associées à un formulaire HTML sont : **GET** et **POST**.

- La méthode **GET** envoie les données en les ajoutant directement à l'URL, ce qui les rend visibles et peu sécurisées. Elle est généralement utilisée pour des recherches ou des requêtes simples qui ne nécessitent pas de confidentialité.

- La méthode **POST** envoie les données dans le corps de la requête HTTP, ce qui les rend invisibles dans l’URL. C'est une méthode sécurisée, idéale pour envoyer des informations sensibles, des fichiers ou de grandes quantités de données.



## UX UI
### 35. Quelle est la différence entre UX Design et UI Design ?  
Acronymes pour User Experience et User Interface.  

L'**UX Designer** travaille sur l'optimisation et l'amélioration de l'expérience utilisateur.  
Il étudie les parcours possibles des utilisateurs qui se rendent sur des sites ou des applications afin de travailler les points suivants : accessibilité, ergonomie (facilité d'utilisation), cohérence du design, fonctionnalités intuitives.  
Le but est de proposer un produit ou une solution digitale à la fois crédible, intelligente, et compatible sur tous les supports.  

L'**UI Designer**, quant à lui, se charge de concevoir l'interface, c'est-à-dire le point d'interaction et de communication entre l'homme et la machine.  
Ici, on parle de ce que voit un utilisateur sur son écran lorsqu'il parcourt un site ou une application web. L'UI Designer veille à l'apparence de l'interface dite graphique : l'aspect et l'agencement des différents éléments au service des besoins de l'utilisateur.  
Il définit une charte graphique, les boutons de navigation, la typographie, etc.  
Il est également responsable de l'image que renvoie le site d'une entreprise, par exemple.  

---

### 36. Qu’est-ce qu’un wireframe ?  
Parmi les étapes de **conception et de maquettage**, on peut considérer que le wireframe est la première représentation visuelle de l'interface utilisateur d'un site web ou d'une application logicielle. Elle peut être précédée par un **Zoning**, une étape de schématisation pour dégrossir l'apparence d'une future page.  
Le **Wireframe** permet de définir l'emplacement et l'organisation des éléments et des formes nécessaires au fonctionnement du site (ou projet). Il permet de représenter l’architecture du site et la façon dont les différentes pages et éléments sont liés entre eux. On ne se concentre pas sur l'aspect du rendu visuel. Le graphisme interviendra plus tard, lors de la phase **Maquette**.  
Les wireframes facilitent le travail d'échange et de réflexion avec le client (ou ses collègues) car ils sont facilement modulables et modifiables.  

---

### 37. Qu’est-ce qu’un prototype ?  
Un **Prototype** est une représentation dite "fonctionnelle" des interfaces du produit final. Il permet de tester la navigation et les fonctionnalités en intégrant des **éléments d'interactivité** (et non du code réel). Ainsi, il permet de tester le produit pour détecter d'éventuels problèmes d'ergonomie ou d'accessibilité. C'est une étape essentielle avant de passer au développement. Il peut également servir d'outil de présentation et de démarchage dans un cadre commercial.  

---

### 38. Qu’est-ce que la hiérarchie visuelle en UI Design ?  
En **UI Design**, la hiérarchie visuelle permet de respecter l'importance du contenu qui doit être mis en avant sur une page. Ce concept permet de faciliter la recherche d'information et l'accès aux fonctionnalités nécessaires à la **qualité de l'expérience utilisateur**.  
Pour guider l'utilisateur, on peut construire une page selon des schémas visuels comme le **F-Pattern** ou le **Z-Pattern**. Ou au contraire, casser ces schémas selon l'effet voulu.  
D'autres éléments peuvent intervenir comme la typographie, les espaces blancs, la cohérence des couleurs. La conception mobile requiert une attention particulière car il faut prioriser davantage. À savoir qu'un utilisateur préfère généralement se trouver sur un site qui lui paraît familier, avec une structure reconnaissable.  

---

### 39. Qu’est-ce que l’accessibilité en UX Design ?  
En UX Design, l'**accessibilité** est un concept qui consiste en la création de produits numériques qui répondent à des critères d'accessibilité, c'est-à-dire qui peuvent être utilisés par tous les individus quel que soient leur aptitude physique ou mentale, mais aussi leur infrastructure réseau, leur langue ou leur culture.  
Il s’agit d’une obligation légale en France.  

---

### 40. Qu’est-ce qu’une grille de mise en page ?  
En Design d’interface, une **grille de mise en page** agit comme un cadre servant à organiser les éléments d’une page. Les différentes lignes et colonnes créent des repères et permettent de positionner les éléments.  
Les grilles apportent structure, harmonie, rythme, et contribuent à respecter la hiérarchisation du contenu.  
Dans un processus de maquettage avec Figma, on peut par exemple utiliser l’outil **Layout Grid** pour faire apparaître des lignes et des colonnes et ainsi faciliter le design.  

---

### 41. Qu’est-ce que la notion d’affordance en UX Design ?  
En UX Design, la notion d’**affordance** désigne les propriétés ou les caractéristiques d'un élément qui permettent d’indiquer ce qui peut être fait avec celui-ci.  
Les affordances sont des indices qui donnent une idée de la manière dont les utilisateurs peuvent interagir avec.  
Par exemple, la vue d’un bouton rouge indique un danger ou une action indésirable, tandis qu’un bouton vert se veut plus engageant ou digne de confiance.  
Les icônes doivent également respecter cette notion pour mieux guider l’utilisateur.  

---

### 42. Qu’est-ce qu’un « mobile first design » ?  
Le **Mobile First Design** est une approche qui consiste à concevoir un site en se focalisant d’abord sur sa **version mobile**. Beaucoup de sites sont consultés avec un téléphone mobile, d’où l’importance et son succès auprès des Designers.  
Contrairement au principe de Responsive, cette approche adapte le design pour les écrans larges (tablettes ou ordinateurs) en deuxième intention.



## Programmation orientée objet (POO)
43.	Donner une définition de la programmation orientée objet 
44.	Qu’est-ce qu’une classe ? Comment la déclare-t-on ?
45.	Qu’est-ce qu’un objet ?
46.	Définir la notion de propriété / attribut / méthode
47.	Qu’est-ce que la visibilité d’une propriété ou d’une méthode ? Citer les différents types de visibilité
48.	Quelle est la méthode spécifique utilisée pour créer un nouvel objet à partir d’une classe ?
49.	Qu’est-ce que l’encapsulation ?
50.	Que signifie « étendre une classe » ? Quelle est le concept clé mis en œuvre ? Donner un exemple
51.	Définir l’opérateur de résolution de portée
52.	Définir une méthode / propriété statique
53.	Définir le polymorphisme en POO
54.	Définir une méthode / classe abstraite ?
55.	Définir le chaînage de méthodes
56.	Qu’est-ce que la méthode __toString() ? Existe-t-il d’autres méthodes « magiques »
57.	Qu’est-ce qu’un « autoload » ?
58.	Comment appelle-t-on en français les « getters » et les « setters » ?
59.	Qu’est-ce que la sérialisation en PHP ? 

## Architecture 
### 60. Qu’est-ce que l’architecture client / serveur ? Grâce à quel type de requête peut-on interroger le serveur. Définir l’acronyme de ce type de requête. Si on ajoute un « S » à cet acronyme, expliquer la différence

L'**architecture client/serveur** est un modèle d'organisation des applications où deux entités principales interagissent : un **client** (qui envoie des requêtes) et un **serveur** (qui traite les requêtes et renvoie des réponses).

Les clients peuvent interroger le serveur via des requêtes de type **HTTP (HyperText Transfer Protocol)**. Lorsqu’on ajoute un **S** (ce qui donne **HTTPS**), cela signifie que les données échangées sont **sécurisées par un chiffrement SSL/TLS**. Cela permet de protéger les informations sensibles pendant leur transmission.

---

### 61. Donner la définition d’un design pattern. Citer au moins 3 exemples de design pattern

Un **design pattern (ou modèle de conception)** est une **solution réutilisable à un problème courant** rencontré lors de la conception logicielle. Les design patterns permettent de **standardiser les bonnes pratiques** de programmation, en facilitant la maintenance, l'évolutivité et la lisibilité du code.

**Exemples de design patterns :**
- **Singleton :** Garantit qu'une classe n'a qu'une seule instance et fournit un point d'accès global à cette instance.
- **Factory Method :** Définit une interface pour créer un objet, mais laisse aux sous-classes la décision de la classe à instancier.
- **Observer :** Permet à un objet de notifier automatiquement des changements d'état à une liste d'observateurs qui sont automatiquement mis à jour.

---

### 62. Qu’est-ce que l’architecture MVC ?

L'**architecture MVC (Model-View-Controller)** est un **design pattern** qui permet de **séparer une application en trois couches distinctes** pour mieux organiser le code et faciliter sa maintenance. Ces trois couches sont : **Modèle (Model)**, **Vue (View)** et **Contrôleur (Controller)**.

---

### 63. Quel est le rôle de chaque couche du design pattern MVC : Model, View, Controller ?

- **Modèle (Model) :**
  - Gère la logique métier et les données de l'application.
  - Interagit avec la base de données.
  - Ne contient pas de logique d'affichage.

- **Vue (View) :**
  - Gère l'affichage des données à l'utilisateur.
  - Ne contient pas de logique métier.
  - Reçoit les données du contrôleur et les affiche de manière formatée.

- **Contrôleur (Controller) :**
  - Sert d'intermédiaire entre le Modèle et la Vue.
  - Reçoit les requêtes de l'utilisateur, interagit avec le modèle, et sélectionne la vue appropriée pour afficher les données.

---

### 64. Quels sont les avantages de l’architecture MVC ?

- **Séparation des responsabilités :** Chaque couche a un rôle bien défini, ce qui facilite la maintenance.
- **Réutilisabilité du code :** Les composants peuvent être utilisés indépendamment les uns des autres.
- **Testabilité améliorée :** Le modèle et le contrôleur peuvent être testés séparément.
- **Modularité :** Permet de faire évoluer chaque partie de l’application sans impacter les autres.

---

### 65. Existe-t-il des variantes à l’architecture MVC ?

Oui, il existe plusieurs variantes de l’architecture MVC, parmi lesquelles :
- **MVVM (Model-View-ViewModel) :** Souvent utilisé pour les interfaces graphiques en JavaScript ou applications mobiles, introduit une couche `ViewModel` qui gère la logique de présentation.
- **MVP (Model-View-Presenter) :** Simplifie l’interaction entre la Vue et le Modèle en introduisant un `Presenter` qui gère la logique de présentation.
- **HMVC (Hierarchical Model-View-Controller) :** Introduit une hiérarchie entre les contrôleurs pour améliorer l’organisation du code.

---

### 66. Qu’est-ce qu’une API ? Définir l’architecture REST

Une **API (Application Programming Interface)** est un **ensemble de règles et d’outils permettant à différentes applications de communiquer entre elles**. Elle définit les méthodes par lesquelles une application peut interagir avec une autre.

L’**architecture REST (Representational State Transfer)** est un style d’architecture permettant de concevoir des **API web** qui utilisent **les requêtes HTTP standard (GET, POST, PUT, DELETE, etc.)** pour manipuler des ressources identifiées par des URLs.

**Principes de REST :**
- **Stateless (sans état) :** Chaque requête est indépendante des précédentes.
- **Uniformité de l’interface :** Les interactions sont standardisées par des méthodes HTTP bien définies.
- **Cachabilité :** Les réponses peuvent être mises en cache pour améliorer les performances.
- **Architecture client-serveur :** Séparation claire entre le client (interface utilisateur) et le serveur (stockage et traitement des données).

Les **APIs RESTful** sont largement utilisées car elles sont simples à implémenter, évolutives, et compatibles avec de nombreux clients.



## Modélisation - Base de données
67.	Qu’est-ce que la modélisation de données ? Définir la méthode Merise
68.	Quelles sont les 3 étapes principales de la méthode Merise ? 
a.	Analyse, conception et réalisation
b.	Planification, exécution et contrôle
c.	Création, modification et suppression
69.	Qu’est-ce qu’un modèle conceptuel de données (MCD) en Merise ?
70.	Qu’est-ce qu’un modèle logique de données (MLD) en Merise ?
71.	Donner la définition des mots suivants :
a.	Entité
b.	Relation
c.	Cardinalité
d.	Clé primaire / clé étrangère
72.	Que devient une relation de type « Many To Many » dans le modèle logique de données ?
73.	Qu’est-ce qu’une base de données ?
74.	Définir les notions suivantes : 
a.	SQL
b.	MySQL
c.	SGBD (donner 2 exemples de SGBD)
75.	Dans une base de données, les données sont stockées dans des ___. Celles-ci sont constituées de lignes appelées ___ et de colonnes appelées ___
76.	Quelle est la différence entre une base de données relationnelle et non relationnelle ?
77.	Qu’est-ce qu’une jointure dans une base de données ? En existe-t-il plusieurs ? Si oui lesquelles ?
78.	A quoi sert une vue dans une base de données ?
79.	Qu’est-ce que l’intégrité référentielle dans une base de données ?
80.	Quelles sont les fonctions d’agrégation en SQL ?
81.	Qu’est-ce qu’un CRUD dans le contexte d’une base de données ?
82.	Quelles sont les clauses qui permettent de :
a.	Insérer un nouvel enregistrement dans une table
b.	Modifier un enregistrement dans une table
c.	Supprimer un enregistrement dans une table
d.	Supprimer la base de données
e.	Filtrer les résultats d’une requête SQL
f.	Trier les résultats d’une requête SELECT
g.	Regrouper les résultats d'une requête SELECT en fonction d'une colonne spécifique
h.	Concaténer 2 chaînes de caractères 
83.	Comment se connecter à une base de données en PHP ? Quelle est la classe native utilisée ?

## Symfony
84.	Qu’est-ce que Symfony ?
85.	Sur quel langage de programmation et design pattern repose Symfony ? 
86.	Quelle est la dernière version en date de Symfony ?
87.	Qu’est-ce qu’un bundle ? 
88.	Quel est le moteur de template utilisé par défaut dans Symfony ?
89.	Qu’est-ce qu’un ORM ? Quel est son utilité et comment s’appelle-t-il au sein de Symfony ?
90.	Qu’est-ce que l’injection de dépendances ? Quel est l’outil utilisé dans ce contexte et quel fichier contient l’intégralité des dépendances du projet ?
91.	Que permet le bundle Maker au sein de Symfony ? 
92.	Quel est le langage de requêtage exploité au sein d’un projet Symfony ?
93.	Quel est le composant qui garantit l’authentification et l’autorisation des utilisateurs ?

## Sécurité
94.	Qu’est-ce que l’injection SQL ? Comment s’en prémunir ?
95.	Qu’est-ce que la faille XSS ? Comment s’en prémunir ?
96.	Qu’est-ce que la faille CSRF ? Comment s’en prémunir ?
97.	Définir l’attaque par force brute et l’attaque par dictionnaire
98.	Existe-t-il d’autres failles de sécurité ? Citer celles-ci et expliquer simplement leur comportement
99.	A quoi servent l’authentification et l’autorisation dans un contexte d’application web ?
100.	Définir la notion de hachage d’un mot de passe et citer des algorithmes de hachage
101.	Qu’est-ce qu’une politique de mots de passe forts ?
102.	Qu’est-ce que l’hameçonnage ?
103.	Définir la « validation des entrées »

## RGPD
104.	Qu’est-ce que le RGPD ?
105.	Quel est son objectif principal ?
106.	Quelle est la date d’entrée en vigueur du RGPD ?
107.	Quelles sont les sanctions possibles en cas de non-respect du RGPD ?
108.	En France, quel est l’autorité administrative qui s’occupe de faire appliquer le RGPD ?
109.	Quel est le consentement valide selon le RPGD ?
110.	Qu’est-ce qu’une politique de confidentialité ?
111.	Quelle est la durée de conservation maximale des données personnelles selon le RGPD ?
112.	Quels sont les droits des utilisateurs selon le RGPD ?
113.	Qu’est-ce que le principe de minimisation des données selon le RGPD ?

## SEO
114.	Qu’est-ce que le SEO ? 
115.	Quel est l’objectif principal du SEO ?
116.	Existe-t-il plusieurs types de référencement ? Lesquels ?
117.	Qu’est-ce que la densité de mots-clés en SEO ?
118.	Qu’est-ce qu’une balise « alt » ?
119.	Qu’est-ce que la balise « meta description » ?
120.	Qu’est-ce que le « nofollow » en SEO ?
121.	Quelle est l'importance du contenu de qualité pour le référencement d'un site web ?
122.	Pourquoi est-il important d'utiliser des balises de titre (h1, h2, h3, etc.) de manière structurée ?
123.	Quelle est la recommandation pour les URL d'un site web bien référencé ?
124.	Qu'est-ce que le maillage interne et pourquoi est-il important pour le référencement ?
125.	Qu'est-ce que l'optimisation des images pour le référencement ?
126.	Qu'est-ce qu'un plan de site (sitemap) et pourquoi est-il important pour le référencement ?

## Gestion de projets - DevOps
127.	Qu’est-ce que la gestion de projet ?	
128.	Qu’est-ce qu’une méthode Agile de gestion de projet ? 
129.	Expliquer la méthode MoSCoW en quelques lignes et citer ses avantages
130.	A quoi sert la méthodologie MVP ? Citer les caractéristiques clés
131.	Qu’est-ce que la planification itérative ?
132.	Citer 3 méthodes Agiles dans le cadre d’un projet informatique
133.	Qu’est-ce qu’une réunion de revue de projet ?
134.	Qu’est-ce qu’un livrable dans un projet ? 
135.	Quels sont les 3 piliers SCRUM ? Définir chacun d’entre eux
136.	Qu’est-ce que le DevOps et quel est son objectif principal ?
137.	Qu’est-ce que l’intégration continue ? 
138.	Qu’est-ce que Docker ? Et en quoi est-il utile dans le cadre du DevOps ?
139.	Qu’est-ce qu’un test unitaire ? 
140.	Quelle est l'unité de code testée lors d'un test unitaire ?
141.	Quelles sont les caractéristiques d'un bon test unitaire ?
142.	Qu'est-ce qu'une assertion dans un test unitaire ?
 
## English
1)	What does JavaScript enable you to do on a website ?
a.	Add interactive behavior and dynamic content
b.	Define the layout and design of web pages
c.	Handle server-side operations
2)	Which programming language is primarily used for server-side web development ?
a.	PHP
b.	JavaScript
c.	HTML
3)	What is the purpose of a web browser ?
a.	To render and display web pages
b.	To execute serve-side code
c.	To manage databases
4)	What is the difference between GET and POST methods in HTTP ?
a.	GET retrieves data from a server, while POST submits data to a server
b.	GET submits data to a server, while POST retrieves data from a server
c.	GET and POST methods are interchangeable
5)	What is the purpose of version control systems (e.g., Git) in web development ?
a.	To track changes and manage collaborative development
b.	To optimize website loading speed
c.	To handle server-side scripting
6)	What is the purpose of a framework in web development ?
a.	To provide a structured environment for building web applications
b.	To handle network protocols and data transfer
c.	To create visual designs and layouts for websites
7)	What does NoSQL stand for ?
a.	Not Only SQL
b.	Non-Structured Query Language
c.	New Object-Oriented Language
8)	Which of the following is a characteristic of NoSQL databases ?
a.	Strict schema enforcement
b.	Support for complex transactions
c.	Scalability and flexible data models
