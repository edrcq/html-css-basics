## 1/ HTML5

### Balises inline, block

Un des premiers concepts à maîtriser quand on parle d’HTML est le « type d’affichage » *inline *ou *block *(nous ne parlerons pas des autres types minoritaires, table-cell, inline-block etc).

Voici quelques exemples des balises couramment utilisés.

Balises block :

*   p
*   footer
*   h1 h2 etc
*   ul
*   div

Balises inline :

*   a
*   span
*   em
*   img

Alors qu’elle est la différence entre une balise *block *et *inline *?

*block *: une balise de type block crée automatiquement un retour à la ligne (clear) avant et après, on imagine alors facilement un véritable « bloc » qui délimite une zone (`article`, `header`, `footer` etc). Vous le comprenez, un site est constitué de plusieurs de ces blocks, imbriqués les uns dans les autres dans lesquels ont imbrique des contenus textuel, images, etc.

*inline *: une balise de type inline se trouve **obligatoirement ** à l’intérieur d’une balise block. Une balise inline ne crée pas de retour à la ligne, le texte qui se trouve à l’intérieur s’écrit donc à la suite du texte précédent, sur la même ligne.

La **mauvaise pratique** que l’on dénonce ici est l’utilisation d’une balise *block* à l’intérieur d’une balise *inline* (à l’exception de l’élément `a` qui peut envelopper n’importe quel type de contenu, *block* comme *inline*.)

> En gros, la différence, c’est juste un retour à la ligne ?

Non, les différences entre les comportements natifs d’une balise *inline* et *block* sont plus nombreuses.

Voici une petite liste des différences :

*   Un élément *block* prendra toute la largeur de son élément parent, si aucune largeur n’est définie.
*   Un élément *block* prendra la hauteur de ses éléments enfants, si aucune hauteur n’est définie (et si aucun `float` ou positionnement changé).
*   Un élément *inline* accepte la propriété white-space, et vertical-align mais ignore width et height.
*   Un élément *inline* s’il est flotté à gauche ou à droite, devient automatiquement de type block, et prend toutes ses caractéristiques.

La **mauvaise pratique** ici, est l’utilisation d’une balise sans prendre en compte ses comportements natifs, il est inutile par exemple de définir `width:100%` sur une balise de type block, car elle adopte par défaut ce comportement.

Pour généraliser, les éléments *block* sont **structurels **alors que les éléments *inline* sont relatifs au **texte**.

### Balises fortement typés (html5)

Avec HTML5, de nouvelles balises ont été mis en place, afin de rendre le web plus **typé** sémantiquement et donc plus **compréhensible **par l’homme/machine. Il peut être difficile depuis de savoir quelle balise utilisée à quel moment et avec quel contenu.

Voici un schéma qui peut aider dans la prise de décision:

![html 5](https://openclipart.org/download/193523/cyberscooty-diagramme-HTML5.svg)

Les principales balises à retenir sont :

*   Header: définit le haut d’une section ou d’une page.
*   Nav: définit les principaux liens de navigation, généralement le menu.
*   Section: définit une section qui regroupe des contenus cohérents entre eux.
*   Article: définit un contenu autonome et indépendant.
*   Aside: définit des informations complémentaires(souvent sur un côté).
*   Footer: définit le bas d’une section ou d’une page.

Voici un exemple de site développé avec ses nouvelles balises :

![site](https://user.oc-static.com/files/343001_344000/343677.png)

La** bonne pratique** mise en lumière ici, est de **typer** votre site au maximum. Vous avez de nouvelles armes, correspondant à des **situations **précises, il faut les utiliser.

Fini le temps des sites composés uniquement de `div`, désormais, on utilise directement la balise qu’il nous faut.

### Balises obsolètes

Les évolutions du langage ont laissé dans leurs passages quelques balises devenus obsolètes, qui malgré l’apparition de remplaçantes, sont toujours implantées.

Voici une liste non-exhaustive de quelques balises à bannir/limiter au profit de plus récentes :

*   basefont: autrefois utilisé pour définir les polices.Aujourd’hui, on préférera déclarer les polices dans le CSS.
*   center: autrefois utilisé pour centrer les textes. Aujourd’hui, on préférera centrer dans le CSS.
*   l’ancienne balise menu: autrefois utilisé pour déclarer un menu de navigation. Aujourd’hui, on préférera utiliser des `UL`, `LI` à la place. (/!\ depuis HTML 5 **menu **est réimplanté** **avec une signification différente => Menu contextuel).

Quelques cas spéciaux :

*   Table: autrefois utilisé pour mettre en page ! Aujourd’hui ne dois être utilisé que pour faire des tableaux (comme son nom l’indique)
*   div et span: autrefois utilisé pour faire nos blocks. Il est préférable aujourd’hui d’utiliser le moins de div et de span possible, en privilégiant les balise HTML5

La liste n’est pas complète, j’ai essentiellement mis les balises inutiles aujourd’hui (dans certains cas, comme les newsletters certaines vieilles balises sont toujours utiles, tout comme le CSS inline).

### Ordre des attributs

On attaque ici un point de **bonnes pratiques** pur, l’ordre des attributs des balises HTML. Il y a plusieurs « design pattern » pour l’organisation du CSS dans les fichiers CSS, mais un seul qui semble vraiment sortir du lot concernant l’ordre des attributs dans les fichiers HTML.

Afin de faciliter la lecture du code, l’ordre suivant des attributs est à privilégier :

*   class
*   id, name
*   data-*
*   src, for, type, href, value
*   title, alt
*   role, aria-*

Les **class **sont des composants **réutilisables**, ils doivent donc apparaître en premier et être choisis en priorité pour sélectionner nos éléments (écrire le maximum de code réutilisable étant une bonne pratique globale dans n’importe quel langage). Les **Id **sont plus spécifiques et doivent donc être utilisés moins souvent (ex: Ancre, Script JS, etc). Viens ensuite **data** qui permet d’étendre les informations de notre élément, puis les attributs **type, source, value** qui aide à identifier le contenu (normalement déjà explicite avec le nom de **class, name** etc).

**exemple:**

![html](https://i1.wp.com/img4.hostingpics.net/pics/72964453.png)

### Règles diverses

Je vais lister pour finir quelques bonnes pratiques qui peuvent paraître évidentes, mais qui nécessitent tout de même d’être appliquées :

*   Ne **pas** écrire de CSS Inline, le CSS doit être dans un ou plusieurs fichiers séparés (sauf cas newsletter)
*   Utiliser les **listes** (`ul, li`) pour un menu de navigation, oubliez les `span` ou `ahref` tout seul
*   Faite une déclaration spécial **IE**, `[if lt IE 7]` pour la gestion de style particulier
*   Utiliser **modernizr**, pour augmenter la capacité des navigateurs de vos visiteurs et rendre vos balises compatibles
*   Renseigner les attributs **alt **de toutes vos images pour l’accessibilité et le SEO
*   Respecter/Utiliser les **balises de titre **(*h1 jusqu’à h6*), elles sont un des éléments les plus important après la balise *title (de page) *pour le SEO
*   Déclaré, les fichiers CSS au début du document, le JS à la fin du document pour des soucis de **performances**

Voilà pour les quelques règles faciles à mettre en place dans un projet, qui permettent d’avoir une meilleure :

*   Relecture
*   Accessibilité
*   Performance
*   Compatibilité
*   SEO

## 2/ CSS

Quand on parle de CSS, on ne peut s’empêcher de penser à des documents interminables, plus long les uns que les autres, où l’on écrase nos déclarations précédentes au fur et à mesure que le projet évolue. Mais le CSS peu aussi être optimisé et bien utilisé, dans un souci d’optimisation et de maintenabilité.

### Spécificité

Les sélecteurs sont des variables globales **mutables**. Elles sont donc écrasées suivant **l’ordre **de déclaration, mais aussi suivant la **spécificité**.

![html](https://i0.wp.com/img11.hostingpics.net/pics/872638speci.png)

Suivant cet exemple, nous pouvons voir que la spécificité en CSS est une des notions les plus importantes, mais aussi les plus pénibles à comprendre.

Ici on peu voir que le premier « coucou » est de couleur rouge, alors que si on suit la cascade, la couleur verte est appliqué après le rouge sur l’élément `p`. La raison est que le sélecteur ` body p` à un poids plus important que `p` tout seul, il est plus **spécifique**.

Ensuite, on voit que « coucou 2 » est de couleur bleue, en effet il à une class `blue`, qui posséde une spécificité encore plus grande. Quoi qu’il arrive, un sélecteur de **class** prendra toujours le dessus sur des sélecteurs d »éléments.

Enfin, le « coucou 3 » est en noir, car la fourberie de CSS est d’accorder plus d’importance, quoi qu’il arrive, à une propriété **directement **déclarée dans l’élément.

La spécificité étant un point assez difficile à intégrer, je vous laisse un article en guise de référence : [Developer-Moz](https://developer.mozilla.org/fr/Apprendre/CSS/Les_bases/La_cascade_et_l_h%C3%A9ritage)

### Nom de classes

Maintenant qu’on a appris a utiliser le bon élément HTML afin d’avoir un code sémantique fort, il faut penser aux noms des classes. Concernant le naming, plusieurs courant sont possible et en confrontation, la bonne pratique veut tout de même :

*   Que le nom des classes soit compréhensible et explicite (Eviter entre autres les abréviations du type « Mnp » pour « Menu Principal »)
*   Ne pas utiliser de camel case, la class `liens-nav-footer` est plus lisible que `LiensNavFooter`
*   Ne pas dépasser 2 (allez 3, si vraiment, tu ne peux pas faire autrement) mots pour une class (bad ex: Menu-haut-trop-mignon)

Si je devais vous conseiller une nomenclature, je choisirais celle de [BEM](http://getbem.com/naming/) (Block Element Modificateur), elle a pour avantage :

*   De pouvoir identifier une class par son type (block, element, modificateur)
*   De montrer explicitement les parents et enfants de la class cible (ex: nav__lien nous montre directement que nous ciblons les liens du menu « Nav »)
*   D’appliquer des modificateurs sur des éléments existants, suivant leurs états (ex: nav–size-big nous indique que l’on modifie « Nav » avec un modificateur de taille

Voilà pour un premier aperçus du naming CSS, comme je vous l’ai dit, le naming reste une convention non figée, et chacun doit choisir ce qui lui parait le plus simple et efficace sur le long terme. Libre à vous d’utiliser une convention qui existe déjà ou de faire la vôtre.

### Design Fluid

A moins de travailler sur une ancienne version d’un site, et qu’on vous demande précisément de ne pas faire de « responsive » design, ou du moins « fluid », je vous conseille de suivre ces bonnes pratiques pour un site visible par le plus grand nombre. Le fluid design, consiste à utiliser des éléments qui vont s’adapter naturellement à la place environnante. Intégrer ses éléments avec des valeurs relatives est la première étape pour faire un site « responsive ».

Afin d’obtenir un design « fluid », on évite d’utiliser les unités de valeurs absolues (cm,pt,px,in,pc) et on utilise les unités suivantes :

*   Utiliser des `%` au lieu de px sur des blocs, le `%` se réfère à l’élément parent contrairement au px
*   Utiliser des `Em` à la place des points et pixels (`1em` = 100% du parent), pour les polices, il se réfère à l’élément texte parent de manière relative
*   Utiliser des `Rem` à la place des points et pixels, pour les polices, si vous souhaitez avoir une uniformité des polices (relatif au `font-size` de la balise `HTML`)

Ainsi, peu importe la taille de police par défaut dans le navigateur, ou la taille de l’écran, vos blocs et polices feront toujours la même taille (proportionnellement au reste du site), 1% restant toujours 1/100 = 0,01.

Je rajouterais même une combinaison des deux pratiques, après avoir définis une `font-size` dans la balise `HTML` (en px) utiliser `rem` pour les balises de type block (aside, article etc) et `em` pour les balises de type inline (h2, p etc). Ainsi, chaques élément conteneur est compartimenté et fluid.

> Et après ?

Je rajouterais une deuxième étape, pour nous rapprocher encore un peu plus du responsive, l’utilisation de `flexbox`, au lieu des éternels `display:block`, `display:inline`.

L’utilisation de `flexbox` va vous permettre de mettre en forme de façons fluid vos éléments très simplement. Vous aurez accès à des propriétés permettant :

*   D’organiser les éléments de manière horizontale ou verticale
*   D’aligner et centrer de manière horizontale et verticale
*   De réorganiser les éléments en contrecarrant l’ordre du flux du DOM
*   De gérer les espaces disponibles, en affichant ou non des espaces entre les éléments, ou en augmentant la taille des éléments suivant la place disponible.

Vous pouvez tester [les différentes configurations ici](https://demos.scotch.io/visual-guide-to-css3-flexbox-flexbox-playground/demos/).

### Factoriser

Comme dans tout langage de programmation, il est de plus en plus commun et souhaité de factoriser son code. La factorisation consiste à éviter les doublons, les redondances de code au seins d’une application, en trouvant les facteurs communs, on peut regrouper le code et éviter les répétitions.

Un exemple simple avec des boutons :

![factorisation](https://i0.wp.com/img11.hostingpics.net/pics/293974Factoriser.png)

une fois factorisé, afin d’éviter la redondance, on créé une class commune à nos boutons afin de regrouper les attributs partagés.

![factorisation](https://i0.wp.com/img11.hostingpics.net/pics/659978Factoriser2.png)

Et si on veut allez plus loin, on sépare la structure de l’apparence pour rendre le code encore plus factorisable à l’avenir.

![factorisation](https://i1.wp.com/img11.hostingpics.net/pics/654859factoriser3.png)

Grâce à cette méthode, on gagne en lisibilité, en performance, mais aussi en maintenabilité.

### Découper ses fichiers SCSS/SASS

Cette bonne pratique pourrait être utilisé avec du CSS classique, mais par soucis de performance (chargement long à cause des multiples fichiers), nous préférerons l’utiliser avec des pré-processeurs tels que [SASS](http://sass-lang.com/), [LESS](http://lesscss.org/), [Stylus ](http://stylus-lang.com/)etc.

Un pré-processeur CSS est un outil permettant de générer dynamiquement du CSS, tout en apportant des fonctionnalités plus poussées au développeur (nested rules, variables, héritage, etc) Nous ne verrons pas ici le fonctionnement de ses technologies, qui méritent un article dédié, en revanche la bonne pratique pouvant être appliqué sur un projet CSS, il est toujours bon d’en avoir conscience.

Afin d’éviter d’avoir un seul et même fichier CSS pour l’ensemble du site, de plusieurs centaines ou milliers de lignes, il est préférable de le découper, segmenter en plusieurs parties. Attention toutefois à le faire intelligemment, il ne s’agit pas ici de **segmenter **nos fichiers n’importe comment et de dupliquer nos styles dans plusieurs fichiers.

Un exemple à ne pas faire (selon moi):

*   contact.scss
*   historique.scss
*   home.scss

Ici, vous allez **dupliquer **vos éléments communs tels que le footer, le header, les titres etc

Il vaut mieux alors adopter une segmentation par « types »:

*   Typo.scss
*   Forms.scss
*   Grilles.scss
*   Blocs.scss

Ainsi, vos éléments sont rangés et **segmentés **par type, vous n’avez plus qu’à les importer dans votre fichier main.scss pour les utiliser.

### Quelques truc divers

Voici une liste de différentes petites règles simples à appliquer dans son CSS:

*   **box-sizing:** Pour ne plus avoir de soucis de taille avec vos block, quand vous ajoutez des bordures, pensez à utiliser `box-sizing:border-box`. Ainsi les propriétés width et height incluront le contenu, le padding, et les bordures.
*   **!important:** Evitez d’utiliser `!important` pour surcharger vos propriétés.
*   **Js:** Utilisez le maximum de CSS pour faire vos animations et transitions, pas besoin de Js pour faire cela.
*   **Découpage CSS:** Découpez vos fichiers CSS afin de réduire la taille du fichier et d’éviter les surcharges non voulues.
*   **Unité null:** Ne suffixez pas vos unité null (ex : `padding: 0` n’a pas besoin de « px »).

### Pour aller plus loin

Si après cet article, vous avez encore envie de creuser un peu plus le sujet, je peux vous conseiller quelques pistes de recherches à faire sur Google.

*   voir le type html : flex, inline-flex, inline-block
*   Si vous n’utilisez pas de Sass/Less, vous pouvez tout de même regarder les variables Css (encore mal implémenté par les navigateurs)
*   voir Sass/Less pour un CSS encore plus efficace (nested rules, variables, héritage, etc)
*   Creuser encore plus le responsive design, où comment avec un seul code, adapter un contenu sur plusieurs supports
*   Voir les pseudo-class et pseudo-élément qui permettent d’ajouter du dynamisme et de cibler précisément sans JS
*   Verifier votre code avec [CSSlint](http://csslint.net)
*   Un [petit guide](https://github.com/bendc/frontend-guidelines) regroupant des bonnes pratiques HTML et CSS.
*   Vérifier que notre CSS et HTML seront correctement interprétés : [canisuse.com](http://caniuse.com/).
*   Utiliser [CSSreset](http://cssreset.com/) pour ne plus blâmer les navigateurs quand son design foire.

Et **surtout**,** **continuer à faire de la **veille**, que ce soit sur des nouvelles technos, des anciennes, ou des technos considérées comme « facile » il y a toujours de nouvelles pratiques à maîtriser.
