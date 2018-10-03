---
title: 'Comment : définir un langage spécifique à un domaine'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.domainrelationship
- vs.dsltools.dsldesigner.domainclass
- vs.dsltools.dsldesigner.domaintype
helpviewer_keywords:
- Domain-Specific Language, domain class
- Domain-Specific Language, external types
- Domain-Specific Language, relationships
- Domain-Specific Language, domain properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 56381b86b367d7ca93c43b2918d98eb0fdc092bb
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860483"
---
# <a name="how-to-define-a-domain-specific-language"></a>Comment : définir un langage spécifique à un domaine
Pour définir un langage spécifique à un domaine (DSL), vous créez une solution Visual Studio à partir d’un modèle. Le composant principal de la solution est le diagramme de définition DSL, qui est stocké dans DslDefinition.dsl. La définition DSL définit les classes et les formes de la solution DSL. Après avoir modifié et ajouté à ces éléments, vous pouvez ajouter du code programme pour personnaliser la solution DSL plus en détail.

Si vous ne connaissez pas DSL, nous vous recommandons de collaborer via le **atelier des outils DSL**, que vous trouverez dans ce site : [création and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)

## <a name="templates"></a> Sélection d’une Solution de modèle
 Pour définir un DSL, vous devez avoir installé les composants suivants :

|||
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling||


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]


 Pour créer un nouveau langage spécifique à un domaine, vous créez une nouvelle solution Visual Studio à l’aide du modèle de projet de langage spécifique à un domaine.

#### <a name="to-create-a-dsl-solution"></a>Pour créer une solution DSL

1.  Créer une solution avec le **Domain-Specific Language** modèle, qui peut être trouvée sous **autres Types de projet/extensibilité** dans le **nouveau projet** boîte de dialogue.

     ![Boîte de dialogue Créer DSL](../modeling/media/create_dsldialog.png)

     Lorsque vous cliquez sur **OK**, le **Domain-Specific Language Assistant** s’ouvre et affiche une liste des solutions de modèle DSL.

2.  Cliquez sur chaque modèle pour afficher une description. Choisissez la solution qui ressemble le plus à ce que vous voulez créer.

     Chaque modèle DSL définit une solution DSL de base opérationnelle. Vous modifierez cette solution DSL en fonction de vos exigences.

     Cliquez sur chaque exemple pour obtenir plus d'informations.

    -   Sélectionnez **flux de tâches** pour créer une solution DSL avec des couloirs. Les couloirs sont des partitions verticales ou horizontales du diagramme.

    -   Sélectionnez **modèles de composants** pour créer une solution DSL avec des ports. Les ports sont de petites formes sur le bord d'une forme plus grande.

    -   Sélectionnez **des diagrammes de classes** pour définir une solution DSL avec des formes de compartiment. Les formes de compartiments contiennent des listes d'éléments.

    -   Sélectionnez **langage Minimal** dans d’autres cas, ou si vous avez des doutes.

    -   Sélectionnez **concepteur WinForm Minimal** ou **Concepteur WPF Minimal** pour créer une solution DSL qui s’affiche sur une aire de Windows Forms ou WPF. Vous devrez écrire du code pour définir l'éditeur. Pour plus d’informations, consultez les rubriques suivantes :

         [Création d’un langage spécifique à un domaine basé sur Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

         [Création d’un langage spécifique à un domaine basé sur WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

3.  Entrez une extension de nom de fichier pour votre solution DSL dans la page appropriée de l'Assistant. Il s'agit de l'extension qui sera utilisée par les fichiers contenant des instances de votre solution DSL.

    -   Choisissez une extension de nom de fichier qui n'est associée à aucune application sur votre ordinateur ou sur l'ordinateur où vous voulez installer la solution DSL. Par exemple, **docx** et **htm** serait fichiers inacceptables extensions de nom.

    -   L'Assistant vous avertit si l'extension que vous avez entrée est utilisée actuellement comme DSL. Dans ce cas, utilisez une autre extension de nom de fichier. Vous pouvez aussi réinitialiser l'instance expérimentale du Kit SDK Visual Studio pour effacer les anciennes conceptions expérimentales. Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, **Microsoft Visual Studio 2010 SDK**, **outils**, puis **réinitialiser Microsoft Instance de Visual Studio 2010 expérimental**.

4.  Vous pouvez ajuster les paramètres sur les autres pages ou conserver les valeurs par défaut.

5.  Cliquez sur **Terminer**.

     L'Assistant crée une solution qui contient deux ou trois projets et il génère du code à partir de la définition DSL.

 L'interface utilisateur ressemble maintenant à l'image suivante.

 ![concepteur dsl](../modeling/media/dsl_designer.png)

 Cette solution définit un langage spécifique à un domaine. Pour plus d’informations, consultez [vue d’ensemble de l’Interface utilisateur des outils Domain-Specific Language](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

### <a name="test-the-solution"></a>Tester la solution
 Le modèle de solution fournit une solution DSL opérationnelle, que vous pouvez modifier ou utiliser telle quelle.

 Pour tester la solution, appuyez sur F5 ou Ctrl+F5. Une nouvelle instance de Visual Studio s’ouvre en mode expérimental.

 Dans la nouvelle instance de Visual Studio, dans l’Explorateur de solutions, ouvrez l’exemple de fichier. Il s'ouvre sous forme de diagramme, avec une boîte à outils.

 Si vous exécutez une solution que vous avez créé à partir de la **langage Minimal** modèle, votre expérimentale de Visual Studio doit ressembler à l’exemple suivant :

 ![](../modeling/media/dsl_min.png)

 Expérimentez avec les outils. Créez des éléments et raccordez-les.

 Fermez l’instance expérimentale de Visual Studio.

> [!NOTE]
>  Une fois la solution DSL modifiée, vous ne pourrez plus voir les formes dans l'exemple de fichier test. En revanche, vous pourrez créer des éléments.

### <a name="modifying-the-template-dsl"></a>Modification du modèle de solution DSL
 Renommez et conservez tout ou une partie des classes de domaine et des classes de forme dans le modèle de définition DSL. Vos nouveaux noms de classes doivent être des noms CLR valides, sans espace ni ponctuation.

 Il est particulièrement utile de conserver les classes suivantes :

-   La classe racine apparaît en haut à gauche du diagramme de définition DSL, sous **Classes et relations**. Affectez-lui un nom différent de la solution DSL. Par exemple, un DSL nommée **Bibliothèquemusicale** peut avoir une classe racine nommée **musique**.

-   La classe de diagramme apparaît en bas à droite du diagramme de définition DSL, dans le **éléments de diagramme** colonne. Vous devrez peut-être faire défiler la page vers la droite pour la voir. Il est généralement nommé _Votre_solution_dsl_**diagramme**.

-   Si vous avez utilisé le **flux de tâches** modèle et que vous souhaitez créer des diagrammes avec des couloirs, conservez et renommez la classe de domaine Actor et la forme ActorSwimlane.

 Supprimez ou renommez d'autres classes en fonction de vos exigences.

## <a name="patterns"></a> Modèles pour la définition DSL
 Nous vous recommandons de développer une solution DSL en ajoutant ou en ajustant une ou deux fonctionnalités à la fois. Ajoutez une fonctionnalité, exécutez la solution DSL et testez-la, puis ajoutez une ou deux fonctionnalités supplémentaires. Une solution DSL ordinaire peut être constituée des éléments suivants :

-   Une classe de domaine, la relation d'incorporation qui connecte l'élément au modèle, la forme requise pour afficher les éléments de cette classe sur le diagramme et l'outil d'élément qui permet aux utilisateurs de créer des éléments.

-   Les propriétés de domaine d'une classe de domaine et les décorateurs qui les affichent sur une forme.

-   Une relation de référence et le connecteur qui l'affiche sur le diagramme, ainsi que l'outil de connecteur qui permet aux utilisateurs de créer des liens.

-   Une personnalisation qui nécessite du code de programme, telle qu'une contrainte de validation ou une commande de menu.

 Les sections suivantes expliquent comment construire les types de fonctionnalités DSL les plus utiles. Il existe de nombreux autres modèles avec lesquels vous pouvez construire une solution DSL, mais les modèles suivants sont les plus couramment utilisés.

> [!NOTE]
>  Après avoir ajouté une fonctionnalité, n’oubliez pas de cliquer sur **transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions avant de générer et exécuter votre solution DSL.

 La figure suivante montre la partie classes et relations de la solution DSL qui est utilisée comme exemple dans cette rubrique.

 ![Relations d'incorporation et de référence](../modeling/media/music_classes.png)

 La figure suivante est un exemple de modèle de cette solution DSL :

 ![Modèle d’instance du DSL généré](../modeling/media/music_instance.png)

> [!NOTE]
>  Le terme « modèle » fait référence à une instance de votre solution DSL créée par les utilisateurs. Elle est généralement affichée sous forme de diagramme. Cette rubrique traite du diagramme de définition DSL et des diagrammes de modèles qui apparaissent lors de l'utilisation de votre solution DSL.

## <a name="classes"></a> Définition des Classes de domaine
 Les classes de domaine représentent les concepts de votre solution DSL. Les instances sont *éléments de modèle*. Par exemple dans un **Bibliothèquemusicale** DSL, vous pouvez avoir des Classes de domaine nommé **Album** et **chanson**.

 Pour créer une classe de domaine, vous pouvez faire glisser le **nommé la classe de domaine** outil au diagramme et renommez la classe.

 Pour plus d’informations, consultez [propriétés des Classes de domaine](../modeling/properties-of-domain-classes.md).

### <a name="create-an-embedding-relationship-for-each-domain-class"></a>Créer une relation d'incorporation pour chaque classe de domaine
 Chaque classe de domaine, à l'exception de la classe racine, doit être la cible d'au moins une relation d'incorporation ou elle doit hériter d'une classe qui est la cible d'une relation d'incorporation.

 Dans un modèle, chaque élément de modèle est un nœud dans une arborescence unique de relations d'incorporation. On utilise souvent les termes « parent » et « enfant » pour faire référence à la source et à la cible d'une relation d'incorporation.

 La sélection d'un parent pour une classe de domaine dépend de la façon dont vous souhaitez que la durée de vie de ses éléments dépende d'autres éléments. Si un nœud d'une arborescence est supprimé, sa sous-arborescence est généralement supprimée également. Les classes d'éléments qui ont une existence indépendante sont par conséquent incorporées directement sous la classe racine.

 En général, si vous affichez un élément dans un autre, vous devez indiquer une relation de propriété. Dans ce cas, la classe parente la plus appropriée est la classe du conteneur. Il y a toutefois une exception : quand l'élément que vous voyez dans un conteneur n'est en réalité qu'un lien de référence à un élément indépendant. Dans ce cas, le fait de supprimer le conteneur supprime la référence mais pas sa cible.

 Dans les modèles de définition DSL décrits dans cette rubrique, nous partons du principe que les éléments affichés dans un conteneur seront supprimés lors de la suppression du conteneur. Des schémas plus complexes sont possibles et peuvent être obtenus en définissant des règles.

|Mode d'affichage de l'élément|Classe parente (incorporation)|Exemple dans le modèle de solution DSL|
|------------------------------|--------------------------------|--------------------------------------|
|Forme sur le diagramme.<br /><br /> Couloir.|Classe racine de solution DSL.|Langage minimal.<br /><br /> Flux de tâches : classe Actor.|
|Forme dans un couloir.|Classe de domaine d'éléments qui sont affichés sous forme de couloirs.|Flux de tâches : classe Task.|
|Élément dans une liste dans une forme, où l'élément est supprimé si le conteneur est supprimé.<br /><br /> Port sur le bord d'une forme.|Classe de domaine mappée à la forme de conteneur.|Diagramme de classes : classe Attribute.<br /><br /> Diagramme de composants : classe Port.|
|Élément dans une liste, non supprimé en cas de suppression du conteneur.|Classe racine de solution DSL.<br /><br /> La liste affiche des liens de référence.||
|Non affiché directement.|Classe dont il fait partie.||

 Dans l'exemple de bibliothèque musicale, les albums sont affichés sous forme de rectangles dans lesquels les titres des morceaux sont énumérés. Ainsi, le parent d'Album est la classe racine Music et le parent de Song est Album.

 Pour créer une classe de domaine et son incorporation en même temps, cliquez sur le **relation d’incorporation** outil, puis cliquez sur la classe parente et puis cliquez sur une partie vide du diagramme.

 Il n'est généralement pas nécessaire d'ajuster le nom de la relation d'incorporation et de ses rôles, car ils effectueront le suivi des noms de classes automatiquement.

 Pour plus d’informations, consultez [propriétés des relations de domaine](../modeling/properties-of-domain-relationships.md) et [propriétés des rôles de domaine](../modeling/properties-of-domain-roles.md).

> [!NOTE]
>  L'incorporation n'est pas la même chose que l'héritage. Les enfants dans une relation d'incorporation n'héritent pas des fonctionnalités de leurs parents.

### <a name="add-domain-properties-to-each-domain-class"></a>Ajouter des propriétés de domaine à chaque classe de domaine
 Les propriétés de domaine contiennent des valeurs. En voici quelques exemples : Nom, Titre, Date de publication.

 Cliquez sur **propriétés de domaine** dans la classe, appuyez sur la touche entrée, puis tapez le nom d’une propriété. Le type par défaut d'une propriété de domaine est String. Si vous souhaitez modifier le type, sélectionnez la propriété de domaine et définissez le **Type** dans le **propriétés** fenêtre. Si le type que vous souhaitez n’est pas dans la liste déroulante, consultez [Ajout des Types de propriété](#addTypes).

 **Définir une propriété de nom de l’élément.** Sélectionnez une propriété de domaine qui peut être utilisée pour identifier les éléments dans l’Explorateur de langage. Par exemple, dans la classe de domaine Morceau, vous pourriez sélectionner la propriété de domaine Titre. Dans le **propriétés** fenêtre, définissez **Is Element Name** à `true`.

### <a name="create-derived-domain-classes"></a>Créer des classes de domaine dérivées
 Si vous souhaitez qu'une classe de domaine ait des variantes qui héritent de ses propriétés et relations, créez des classes qui en dérivent. Par exemple, Album peut avoir des classes dérivées WMA et MP3.

 Créez la classe dérivée à l’aide de la **de classe de domaine** outil.

 Cliquez sur le **héritage** d’outils, cliquez sur la classe dérivée, puis cliquez sur la classe de base.

 Envisagez de définir le **modificateur d’héritage** de la classe de base à **abstraite**. Si vous pensez que vous pourriez avoir besoin d'instances de la classe de base, créez plutôt une classe dérivée distincte pour elles.

 Les classes dérivées héritent des propriétés et des rôles de leurs classes de base.

### <a name="tidy-the-dsl-definition-diagram"></a>Mettre en ordre le diagramme de définition DSL
 Quand vous ajoutez des relations, certaines de vos classes apparaissent à plusieurs emplacements. Pour réduire le nombre d’apparences et élargir le diagramme, avec le bouton droit de la classe cible d’une relation, puis cliquez sur **déplacer l’arborescence ici**. Pour obtenir l’effet inverse, la classe cible d’une relation et un clic avec le bouton droit **fractionner l’arborescence**. Si ces commandes de menu ne sont pas visibles, assurez-vous que seule la classe de domaine est sélectionnée.

 Utilisez Ctrl+Haut et Ctrl+Bas pour déplacer des classes de domaine et des classes de forme.

### <a name="test-the-domain-classes"></a>Tester les classes de domaine

##### <a name="to-test-the-new-domain-classes"></a>Pour tester les nouvelles classes de domaine

1.  **Cliquez sur Transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions, pour générer le code du concepteur DSL. Vous pouvez automatiser cette étape. Pour plus d’informations, consultez [comment automatiser transformer tous les modèles](http://msdn.microsoft.com/b63cfe20-fe5e-47cc-9506-59b29bca768a).

2.  **Générez et exécutez la solution DSL.** Appuyez sur F5 ou CTRL + F5 pour exécuter une nouvelle instance de Visual Studio en mode expérimental. Dans l’instance expérimentale de Visual Studio, ouvrez ou créez un fichier qui porte l’extension de nom de fichier de votre DSL.

3.  **Ouvrez l’Explorateur.** AT le côté du diagramme est la fenêtre d’Explorateur de langage, qui se nomme généralement *Votre_langage* Explorer. Si cette fenêtre n'est pas visible, elle est peut-être sous un onglet sous l'Explorateur de solutions. Si vous ne trouvez pas, dans le **vue** menu, pointez sur **Windows autres**, puis cliquez sur *Votre_langage* **Explorer**.

     Votre explorateur présente une arborescence du modèle.

4.  **Créer de nouveaux éléments.** Cliquez sur le nœud racine en haut, puis cliquez sur **Ajouter nouveau**_Votre_classe_.

     Une nouvelle instance de votre classe apparaît dans votre explorateur de langage.

5.  Vérifiez que chaque instance possède un nom différent quand vous créez des instances. Cela se produit uniquement si vous avez défini le **Is Element Name** indicateur sur une propriété de domaine.

6.  **Examinez les propriétés de domaine. Avec une instance de votre classe sectionnée,** Inspecter la fenêtre Propriétés. Elle doit contenir les propriétés de domaine que vous avez définies sur cette classe de domaine.

7.  **Enregistrez le fichier, fermez-le, puis rouvrez ce dernier**. Toutes les instances que vous avez créées doivent être visibles dans l'explorateur, une fois que vous avez développé les nœuds.

## <a name="shapes"></a> Définition de formes sur le diagramme
 Vous pouvez définir des classes d'éléments qui apparaissent sur un diagramme sous forme de rectangles, d'ellipses ou d'icônes.

#### <a name="to-define-a-class-of-elements-that-appear-as-shapes-on-a-diagram"></a>Pour définir une classe d'éléments qui apparaissent en tant que formes sur un diagramme

1.  **Définir et tester une classe de domaine comme décrit dans**[définition des Classes de domaine](#classes) **.** 

    -   Le parent de la classe doit être la classe racine. Autrement dit, il doit y avoir une relation d'incorporation entre la classe racine et la nouvelle classe de domaine.

    -   Si votre diagramme comporte des couloirs, le parent peut être la classe de domaine qui est mappée à un couloir. Avant de poursuivre cette procédure, consultez [définition d’une solution DSL avec des couloirs](#swimlanes).

2.  **Ajoutez une classe de forme** pour représenter les éléments sur le diagramme de modèle. Faites glisser de l'un des outils suivants sur le diagramme de définition DSL :

    -   **Forme géométrique** fournit un rectangle ou une ellipse.

    -   **Forme d’image** affiche une image que vous fournissez.

    -   **Forme de compartiment** est un rectangle qui contient un ou plusieurs listes d’éléments.

     Renommez la classe de forme, qui apparaîtra du côté droit du diagramme de définition DSL sous Formes et connecteurs.

3.  **Définir une image, si vous avez créé une forme d’image**.

    1.  Créez un fichier image de n'importe quelle taille. Les formats BMP, JPEG, GIF et EMF sont pris en charge.

    2.  Dans l'Explorateur de solutions, ajoutez le fichier à la solution sous Dsl\Resources.

    3.  Revenez au diagramme de définition DSL et sélectionnez la nouvelle classe de forme d'image.

    4.  Dans la fenêtre Propriétés, cliquez sur le **Image** propriété.

    5.  Dans le **sélectionner une Image** boîte de dialogue, cliquez sur le menu déroulant sous **nom de fichier**, sélectionnez l’image.

4.  **Ajouter des éléments décoratifs de texte à la forme, pour afficher les propriétés de domaine.**

     Pour afficher le nom ou le titre de l'élément de modèle, vous aurez probablement besoin d'au moins un décorateur de texte.

     Cliquez sur l’en-tête de la classe de forme, pointez sur **ajouter**, puis cliquez sur **décorateur de texte**. Définissez le nom de l’élément décoratif et dans la fenêtre Propriétés, définissez son **Position**.

5.  **Connectez chaque forme avec un mappage d’élément de diagramme à la classe de domaine qu’elle doit afficher**.

     Cliquez sur le **mappage d’élément de diagramme** outil, puis cliquez sur la classe de domaine, puis cliquez sur la classe shape.

6.  **Mapper les propriétés aux décorateurs de texte.**

    1.  Sélectionnez la ligne grise entre la classe de domaine et la forme de classe qui représente le mappage d'élément de diagramme.

    2.  Dans le **détails DSL** fenêtre, cliquez sur le **mappages de décorateurs** onglet. Si vous ne voyez pas le **détails DSL** fenêtre, dans le **vue** menu, pointez sur **Windows autres** puis cliquez sur **détails DSL**. Il est souvent nécessaire d'agrandir cette fenêtre vers le haut pour voir tout son contenu.

    3.  Sélectionnez le nom d'un décorateur. Sous **afficher la propriété**, sélectionnez le nom d’une propriété de la classe de domaine. Répétez cette opération pour chaque décorateur.

         Si vous souhaitez afficher une propriété d’un élément lié, cliquez sur le navigateur de l’arborescence de la liste déroulante sous **chemin d’accès pour afficher la propriété**.

    4.  Vérifiez qu'une coche apparaît à côté de chaque nom de décorateur.

     ![Fenêtre de mappages des formes et des détails DSL](../modeling/media/dsldetailswindow.png)

7.  **Rendre un élément de boîte à outils pour créer des éléments de la classe de domaine.**

    1.  Dans **Explorateur DSL**, développez le **éditeur** nœud et tous ses sous-nœuds.

    2.  Cliquez sur le nœud sous **onglets de boîte à outils** qui porte le même nom que votre solution DSL, par exemple Bibliothèquemusicale. Cliquez sur **Ajouter élément outil**.

        > [!NOTE]
        >  Si vous cliquez sur le **outils** nœud, vous ne verrez pas **ajouter un outil d’élément**. Cliquez plutôt sur le nœud juste au-dessus.

    3.  Dans la fenêtre Propriétés avec le nouvel outil d’élément sélectionné, définissez **classe** à la classe de domaine que vous avez récemment ajouté.

    4.  Définissez **légende** et **info-bulle**.

    5.  Définissez **icône Boîte à outils** à une icône qui s’affiche dans la boîte à outils. Vous pouvez la définir sur une nouvelle icône ou sur une icône déjà utilisée pour un autre outil.

         Pour créer une nouvelle icône, ouvrez Dsl\Resources dans **l’Explorateur de solutions**. Copiez et collez l'un des fichiers BMP d'outil d'élément existants. Renommez la copie collée, puis double-cliquez dessus pour la modifier.

         Revenez au diagramme de définition DSL, sélectionnez l’outil et dans la fenêtre Propriétés, cliquez sur **[...]**  dans **icône Boîte à outils**. Dans le **sélectionner l’image Bitmap** boîte de dialogue, sélectionnez votre. Fichier BMP dans le menu déroulant.

 Pour plus d’informations, consultez [propriétés des formes géométriques](../modeling/properties-of-geometry-shapes.md) et [propriétés des formes d’Image](../modeling/properties-of-image-shapes.md).

#### <a name="to-test-shapes"></a>Pour tester des formes

1.  **Cliquez sur Transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions, pour générer le code du concepteur DSL.

2.  **Générez et exécutez la solution DSL.** Appuyez sur F5 ou CTRL + F5 pour exécuter une nouvelle instance de Visual Studio en mode expérimental. Dans l’instance expérimentale de Visual Studio, ouvrez ou créez un fichier qui porte l’extension de nom de fichier de votre DSL.

3.  **Vérifiez que les outils d’éléments apparaissent dans la boîte à outils.**

4.  **Créer des formes** en faisant glisser à partir d’un outil vers le diagramme de modèle.

5.  **Vérifiez que chaque décorateur de texte s’affiche,** et qui :

    1.  Vous pouvez modifier, sauf si vous avez défini le **Is UI Read Only** indicateur sur la propriété de domaine.

    2.  quand vous modifiez la propriété dans la fenêtre Propriétés ou dans le décorateur, l'autre vue est mise à jour.

 Après avoir testé une forme, vous souhaiterez peut-être ajuster certaines de ses propriétés et ajouter certaines fonctionnalités avancées. Pour plus d’informations, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="references"></a> Définition des relations de référence
 Vous pouvez définir une relation de référence entre n'importe quelle classe de domaine source et n'importe quelle classe de domaine cible. Les relations de référence sont généralement affichées sur un diagramme sous forme de connecteurs, qui sont des lignes entre des formes.

 Par exemple, si Albums et Artistes sont affichés en tant que formes sur votre diagramme, vous pourriez définir une relation nommée ArtistesApparusSurAlbums qui relie des Artistes aux Albums sur lesquels ils ont travaillé. Voir l'exemple sur la figure.

 ![Modèle d’instance du DSL généré](../modeling/media/music_instance.png)

 Les relations de référence peuvent aussi lier des éléments du même type. Par exemple, dans une solution DSL représentant un arbre généalogique, la relation entre les parents et leurs enfants est une relation de référence de Personne à Personne.

### <a name="define-a-reference-relationship"></a>Définir une relation de référence
 Cliquez sur l'outil Relation de référence, sur la classe de domaine source de la relation, puis sur la classe de domaine cible. La classe cible peut être identique à la classe source.

 Chaque relation à deux rôles, représentés par la ligne de chaque côté de la zone de relation. Vous pouvez sélectionner chaque rôle et définir ses propriétés dans la fenêtre Propriétés.

 **Pensez à renommer les rôles**. Par exemple, dans une relation entre Personne et Personne, vous pourriez remplacer les noms par défaut par Parents et Enfants, Responsable et Subordonnés, Enseignant et Élève, et ainsi de suite.

 **Ajustez les multiplicités de chaque rôle**, s’il est nécessaire. Si vous souhaitez que chaque Personne ait au plus un Responsable, affectez la valeur 0..1 à la multiplicité qui apparaît sous l'étiquette Responsable sur le diagramme.

 **Ajouter des propriétés de domaine à la relation.** Dans la figure, la relation Artist-Album a une propriété de rôle.

 **Définissez la propriété Autoriser les doublons de la relation,** si plusieurs liens de la même classe peuvent exister entre la même paire d’éléments de modèle. Par exemple, vous pourriez autoriser un Enseignant à enseigner plusieurs Sujets au même Étudiant.

 ![Mappages de forme pour les connecteurs](../modeling/media/music_connector.png)

 Pour plus d’informations, consultez [propriétés des relations de domaine](../modeling/properties-of-domain-relationships.md) et [propriétés des rôles de domaine](../modeling/properties-of-domain-roles.md).

### <a name="define-a-connector-to-display-the-relationship"></a>Définir un connecteur pour afficher la relation
 Un connecteur affiche une ligne entre deux formes sur le diagramme de modèle.

 Faites glisser le **connecteur** outil sur le diagramme de définition DSL.

 Ajoutez des décorateurs de texte si vous voulez afficher des étiquettes sur le connecteur. Définissez leurs positions. Pour permettre à l’utilisateur de déplacer un décorateur de texte, définissez son **Is Moveable** propriété.

 Utilisez le **mappage d’élément de diagramme** outil pour lier le connecteur à la relation de référence.

 Avec le mappage d’élément de diagramme sélectionné, ouvrez le **détails DSL** fenêtre, puis ouvrez le **mappages de décorateurs** onglet.

 Sélectionnez chaque **Decorator** et définissez **afficher la propriété** à la propriété de domaine correct.

 Assurez-vous qu’une coche apparaît à côté de chaque élément dans le **décorateurs** liste.

### <a name="define-a-connection-builder-tool"></a>Définir un outil générateur de connexion
 Dans le **Explorateur DSL** fenêtre, développez le **éditeur** nœud et tous ses sous-nœuds.

 Cliquez sur le nœud qui a le même nom que votre solution DSL, puis cliquez sur **ajouter un nouvel outil de connexion**.

 Pendant que le nouvel outil est sélectionné, dans la fenêtre Propriétés :

-   Définir le **légende** et **info-bulle**.

-   Cliquez sur **Générateur de connexion** et sélectionnez le générateur approprié pour la nouvelle relation.

-   Définissez **icône Boîte à outils** sur l’icône que vous souhaitez voir apparaître dans la boîte à outils. Vous pouvez la définir sur une nouvelle icône ou sur une icône déjà utilisée pour un autre outil.

     Pour créer une nouvelle icône, ouvrez Dsl\Resources dans **l’Explorateur de solutions**. Copiez et collez l'un des fichiers BMP d'outil d'élément existants. Renommez la copie collée, puis double-cliquez dessus pour la modifier.

     Revenez au diagramme de définition DSL, sélectionnez l’outil et dans la fenêtre Propriétés, cliquez sur **[...]**  dans **icône Boîte à outils**. Dans le **sélectionner l’image Bitmap** boîte de dialogue, sélectionnez votre. Fichier BMP dans le menu déroulant.

##### <a name="to-test-a-reference-relationship-and-connector"></a>Pour tester un connecteur et une relation de référence

1.  **Cliquez sur Transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions, pour générer le code du concepteur DSL.

2.  **Générez et exécutez la solution DSL.** Appuyez sur F5 ou CTRL + F5 pour exécuter une nouvelle instance de Visual Studio en mode expérimental. Dans l’instance expérimentale de Visual Studio, ouvrez ou créez un fichier qui porte l’extension de nom de fichier de votre DSL.

3.  **Vérifiez que l’outil de connexion s’affiche dans la boîte à outils.**

4.  **Créer des formes** en faisant glisser à partir d’un outil vers le diagramme de modèle.

5.  **Créer des connexions** entre les formes. Cliquez sur l'outil de connecteur, cliquez sur une forme, puis sur une autre forme.

6.  **Vérifiez que vous ne pouvez pas créer des connexions entre des classes inappropriées.** Par exemple, si votre relation est entre Albums et artistes, vérifiez que vous ne pouvez pas lier artistes à artistes.

7.  **Vérifiez que les multiplicités sont correctes. Par exemple, vérifiez que vous ne pouvez pas connecter une personne à plusieurs gestionnaires.**

8.  **Vérifiez que chaque décorateur de texte s’affiche,** et qui :

    1.  Vous pouvez modifier, sauf si vous avez défini le **Is UI Read Only** indicateur sur la propriété de domaine.

    2.  quand vous modifiez la propriété dans la fenêtre Propriétés ou dans le décorateur, l'autre vue est mise à jour.

 Après avoir testé un connecteur, vous souhaiterez peut-être ajuster certaines de ses propriétés et ajouter certaines fonctionnalités avancées. Pour plus d’informations, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="compartments"></a> Définition de formes qui contiennent des listes : formes de compartiments
 Une forme de compartiment contient une ou plusieurs listes d'éléments. Par exemple, dans une solution DSL de bibliothèque musicale, vous pourriez utiliser des formes de compartiments pour représenter des albums. Dans chaque album figure une liste de morceaux.

 ![Forme de compartiment](../modeling/media/compartmentshape.png)

 Dans une définition DSL, le moyen le plus simple d'obtenir cet effet consiste à définir une classe de domaine pour le conteneur et une classe de domaine pour chaque liste. La classe de conteneur est mappée à la forme de compartiment.

 ![Mappage de forme](../modeling/media/music_mapcomp.png)

 Pour plus d’informations, consultez [propriétés des formes de compartiments](../modeling/properties-of-compartment-shapes.md).

#### <a name="to-define-a-compartment-shape"></a>Pour définir une forme de compartiment

1.  **Créer la classe de domaine de conteneur**. Cliquez sur le **relation d’incorporation** d’outils, cliquez sur la classe racine du modèle, puis cliquez sur une partie vide du diagramme de définition DSL. Cela crée la classe domaine nommée Album dans la figure de l'exemple.

     En guise d'alternative, au lieu d'incorporer dans la classe racine, vous pouvez incorporer le conteneur dans une classe de domaine mappée à un couloir.

     Ajoutez une propriété de domaine comme nom pour la classe et définissez son **Is Element Name** indicateur dans la fenêtre Propriétés.

2.  **Créer la classe de domaine d’élément liste**. Cliquez sur le **relation d’incorporation** d’outils, cliquez sur la classe de conteneur (Album) et puis cliquez sur une partie vide du diagramme. Cela crée la classe domaine nommée Song dans la figure de l'exemple.

     Ajoutez une propriété de domaine telle que titre à la classe et définissez son **Is Element Name** indicateur.

     Ajoutez d'autres propriétés de domaine.

     Ajoutez une autre classe de domaine d'élément de liste pour chaque liste que vous souhaitez afficher.

3.  **Pour combiner plusieurs types d’élément dans la liste**, créer des classes qui héritent de la classe de liste. Rendre la classe de liste abstraite en définissant son **modificateur d’héritage**.

     Par exemple, si vous souhaitez que la musique classique soit triée par compositeur plutôt que par artiste, vous pourriez créer deux sous-classes de Morceau, Morceau_Classique et Morceau_Non_Classique.

4.  **Créer la forme de compartiment**. Faites glisser à partir de la **forme de compartiment** outil sur le diagramme de définition DSL.

     Ajoutez un décorateur de texte et définissez son nom.

     Ajoutez un compartiment et définissez son nom.

5.  Pour permettre à l’utilisateur masquer les compartiments de listes, avec le bouton droit de la classe de forme de compartiment, pointez sur **ajouter**, puis cliquez sur **développer/réduire le décorateur**. Dans la fenêtre Propriétés, définissez la position du décorateur.

6.  Cliquez sur le **mappage d’élément de diagramme** d’outils, cliquez sur la classe de domaine de conteneur, puis cliquez sur la forme de compartiment.

7.  Sélectionnez le lien de mappage d'élément de diagramme entre la classe de domaine et la forme. Dans le **détails DSL** fenêtre :

    1.  Cliquez sur le **décorateurs** onglet. Cliquez sur le nom de l’élément décoratif, puis sélectionnez l’élément approprié sous **propriété d’affichage**. Vérifiez qu'une coche apparaît à côté du nom du décorateur.

    2.  Cliquez sur le **mappages de compartiments** onglet.

         Cliquez sur le nom du compartiment.

         Sous **chemin d’accès de collection d’éléments affichés**, accédez à la classe d’élément de liste (Song). Cliquez sur la flèche déroulante pour utiliser l'outil de navigation.

         Sous **propriété d’affichage**, sélectionnez la propriété qui doit être affichée dans la liste. Dans l'exemple, il s'agit de Title.

> [!NOTE]
>  En utilisant les champs Chemin d'accès dans les champs Mappage de décorateur et Mappage de compartiment, vous pouvez créer des relations plus complexes entre les classes de domaine et la forme de compartiment.

#### <a name="to-define-a-tool-for-creating-the-shape"></a>Pour définir un outil pour la création de la forme

1.  **Rendre un élément de boîte à outils pour créer des éléments de la classe de domaine.**

2.  Dans **Explorateur DSL**, développez le **éditeur** nœud et tous ses sous-nœuds.

3.  Cliquez sur le nœud sous **onglets de boîte à outils** qui porte le même nom que votre solution DSL, par exemple Bibliothèquemusicale. Cliquez sur **Ajouter élément outil**.

    > [!NOTE]
    >  Si vous cliquez sur le **outils** nœud, vous ne verrez pas **ajouter un outil d’élément**. Cliquez plutôt sur le nœud juste au-dessus.

4.  Dans la fenêtre Propriétés avec le nouvel outil d’élément sélectionné, définissez **classe** à la classe de domaine que vous avez récemment ajouté.

5.  Définissez **légende** et **info-bulle**.

6.  Définissez **icône Boîte à outils** à une icône qui s’affiche dans la boîte à outils. Vous pouvez la définir sur une nouvelle icône ou sur une icône déjà utilisée pour un autre outil.

     Pour créer une nouvelle icône, ouvrez Dsl\Resources dans **l’Explorateur de solutions**. Copiez et collez l'un des fichiers .BMP d'outil d'élément existants. Renommez la copie collée, puis double-cliquez dessus pour la modifier.

     Revenez au diagramme de définition DSL, sélectionnez l’outil et dans la fenêtre Propriétés, cliquez sur **[...]**  dans **icône Boîte à outils**. Dans le **sélectionner l’image Bitmap** boîte de dialogue, sélectionnez votre fichier BMP dans le menu déroulant.

#### <a name="to-test-a-compartment-shape"></a>Pour tester une forme de compartiment

1.  **Cliquez sur Transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions, pour générer le code du concepteur DSL.

2.  **Générez et exécutez la solution DSL.** Appuyez sur F5 ou CTRL + F5 pour exécuter une nouvelle instance de Visual Studio en mode expérimental. Dans l’instance expérimentale de Visual Studio, ouvrez ou créez un fichier qui porte l’extension de nom de fichier de votre DSL.

3.  **Vérifiez que l’outil s’affiche dans la boîte à outils.**

4.  Faites glisser l'outil sur le diagramme de modèle. Une forme est créée.

     Vérifiez que le nom de l'élément apparaît et qu'il est défini automatiquement à une valeur par défaut.

5.  Cliquez sur l’en-tête de la nouvelle forme, puis cliquez sur Ajouter *votre élément de liste.* Dans l'exemple, la commande est Add Song.

     Vérifiez qu'un élément apparaît dans la liste et qu'il a un nouveau nom.

6.  Cliquez sur l'un des éléments de la liste, puis examinez la fenêtre Propriétés. Vous devez voir les propriétés des éléments de liste.

7.  Ouvrez l'explorateur de langage. Vérifiez que les nœuds conteneurs sont visibles, avec les nœuds d'éléments de liste à l'intérieur.

 ![Explorateur généré de DSL](../modeling/media/music_explorer.png)

 Après avoir testé une forme de compartiment, vous souhaiterez peut-être ajuster certaines de ses propriétés et ajouter certaines fonctionnalités avancées. Pour plus d’informations, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

### <a name="displaying-a-reference-link-in-a-compartment"></a>Affichage d'un lien de référence dans un compartiment
 En général, un élément que vous affichez dans un compartiment est un enfant de l'élément qui représenté par la forme de compartiment. Mais parfois, vous souhaitez afficher un élément qui y est lié avec une relation de référence.

 Par exemple, nous pourrions ajouter un second compartiment à AlbumShape qui affiche une liste des artistes liés à l'album.

 Dans ce cas, le compartiment doit afficher le lien au lieu de l'élément référencé. En effet, quand l'utilisateur sélectionne l'élément dans le compartiment et qu'il appuie sur la touche Suppression, vous souhaitez supprimer le lien, et non l'élément référencé.

 Néanmoins, vous pouvez faire en sorte d'afficher l'élément référencé dans le compartiment.

 La procédure suivante part du principe que vous avez déjà créé la classe de domaine, la relation de référence, la forme de compartiment et le mappage d'élément de diagramme, comme décrit précédemment dans cette section.

##### <a name="to-display-a-reference-link-in-a-compartment"></a>Pour afficher un lien de référence dans un compartiment

1.  **Ajoutez un compartiment à la forme de compartiment**. Sur le diagramme de définition DSL, la classe de forme de compartiment avec le bouton droit, pointez sur **ajouter**, puis cliquez sur **compartiment**.

2.  Définissez **chemin d’accès de collection d’éléments affichés** pour accéder à la liaison, au lieu de son élément cible. Cliquez sur le menu déroulant et utilisez l'arborescence pour sélectionner la relation de référence au lieu de sa cible. Dans l’exemple, la relation est **ArtistAppearedOnAlbums**.

3.  Définissez **chemin d’accès à la propriété d’affichage** pour accéder à partir du lien à l’élément cible. Dans l’exemple, il s’agit de **artiste**.

4.  Définissez **propriété d’affichage** à la propriété appropriée de l’élément cible, par exemple **nom**.

5.  **Transformer tous les modèles**, générer et exécuter la solution DSL et ouvrir un modèle de test.

6.  Dans le diagramme de modèle, créez les classes de forme appropriées, définissez leurs noms, puis créez un lien entre elles. Dans la forme de compartiment, les noms des éléments liés doivent apparaître.

7.  Sélectionnez le lien ou l'élément dans la forme de compartiment. Le lien et l'élément doivent tous deux apparaître.

## <a name="ports"></a> Définition des Ports sur la limite d’une autre forme
 Un port est une forme qui se trouve à la limite d'une autre forme.

 Les ports peuvent aussi servir à fournir un point de connexion fixe sur une autre forme, sur lequel l'utilisateur peut dessiner des connecteurs. Dans ce cas, vous pouvez rendre la forme de port transparente.

 Pour voir un exemple qui utilise les ports, sélectionnez le **diagramme de composant** modèle lorsque vous créez une solution DSL. Cet exemple montre les points principaux à prendre en compte lors de la définition des ports :

-   Il existe une classe de domaine qui représente le conteneur des ports, `Component`.

-   Il existe une classe de domaine qui représente des ports. Dans l'exemple, il s'agit de `ComponentPort`.

-   Il existe une relation d'incorporation de la classe de domaine de conteneur à la classe de domaine de port. Pour plus d’informations, consultez [définition des Classes de domaine](#classes).

-   Si vous souhaitez que différents types de ports soient combinés sur le même conteneur, vous pouvez créer des sous-classes de la classe de domaine de port. Dans l'exemple, `InPort` et `OutPort` héritent de `ComponentPort`.

-   La classe de domaine de conteneur peut être mappée à n'importe quel type de forme. Dans l'exemple, il s'agit de `ComponentShape`. Pour plus d’informations, consultez [définition des formes](#shapes).

-   Les classes de domaine de port sont mappées à des formes de ports. Vous pouvez soit mapper les classes dérivées à des classes de formes de ports distinctes, soit mapper la classe de base à une classe de forme de port.

 Dans les autres égards, les formes de port se comportent comme décrit dans [définition des formes](#shapes).

 Pour plus d’informations, consultez [propriétés des formes de Port](../modeling/properties-of-port-shapes.md).

## <a name="swimlanes"></a> Définition d’une solution DSL avec des couloirs
 Les couloirs sont des partitions horizontales ou verticales d'un diagramme. Chaque couloir correspond à un élément de modèle. Votre définition DSL nécessite une classe de domaine pour les éléments de couloirs.

 Le meilleur moyen de créer une solution DSL avec des couloirs consiste à créer une solution DSL et à choisir le modèle de solution Flux de tâches. Dans la définition DSL, la classe Acteur est la classe de domaine mappée au couloir. Renommez celle-ci et les autres classes en fonction de votre projet.

 Pour ajouter une classe qui sera affichée en tant que forme à l'intérieur d'un couloir, créez une relation d'incorporation entre la classe de couloir et votre nouvelle classe. Les utilisateurs pourront faire glisser des éléments d'un couloir à un autre, mais chaque élément sera toujours à l'intérieur d'un couloir particulier. Dans le modèle de solution Flux de tâches, FlowElement est un enfant de la classe de couloir.

 Pour ajouter une classe qui sera affichée en tant que forme indépendamment des couloirs, créez une relation d'incorporation entre la classe racine et votre nouvelle classe. Les utilisateurs pourront placer ces formes n'importe où sur le diagramme, y compris de chaque côté des limites des couloirs et en dehors des couloirs. Dans le modèle de solution Flux de tâches, Comment est un enfant de la classe racine.

 Pour plus d’informations, consultez [propriétés des couloirs](../modeling/properties-of-swimlanes.md).

## <a name="addTypes"></a> Ajout de Types de propriété

### <a name="domain-enumerations-and-literals"></a>Littéraux et énumérations de domaine
 Une énumération de domaine est un type avec plusieurs valeurs littérales.

 Pour ajouter une énumération de domaine, cliquez sur la racine du modèle dans le **Explorateur DSL** puis cliquez sur **ajouter une nouvelle énumération de domaine**. L’élément s’affiche dans le **Explorateur DSL** sous le **des Types de domaine** nœud. Cet élément n'apparaît pas sur le diagramme.

 Pour ajouter des littéraux d’énumération à l’énumération de domaine, cliquez sur l’énumération de domaine dans le **Explorateur DSL** puis cliquez sur **Ajouter nouveau littéral d’énumération**.

 Par défaut, une propriété qui a un type d'énumération ne peut être définie qu'à une seule valeur de l'énumération à la fois. Si vous souhaitez que les utilisateurs et les programmeurs puissent définir n’importe quelle combinaison des valeurs suivantes : « champ de bits » - définir le **IsFlags** propriété de l’énumération.

### <a name="external-types"></a>Types externes
 Lorsque vous définissez le type d’une propriété de domaine, si vous ne trouvez pas le type souhaité dans le **Type** la liste déroulante, vous pouvez ajouter un type externe. Par exemple, vous pouvez ajouter la **System.Drawing.Color** type à la liste.

 Pour ajouter un type, avec le bouton droit de la racine du modèle dans l’Explorateur DSL, puis cliquez sur **ajouter un nouveau Type externe**. Dans la fenêtre Propriétés, définissez le nom sur **couleur** et l’espace de noms **System.Drawing**. Ce type apparaît maintenant dans l’Explorateur DSL sous **des Types de domaine**. Vous pouvez le choisir chaque fois que vous définissez le type d'une propriété de domaine.

## <a name="custom"></a> Personnalisation de la solution DSL
 À l'aide des techniques décrites dans cette rubrique, vous pouvez rapidement créer une solution DSL avec une notation visuelle, un formulaire XML lisible et les outils de base nécessaires pour générer du code et d'autres artefacts.

 Il existe deux méthodes pour étendre la définition DSL :

1.  Affinez la solution DSL en utilisant davantage de fonctionnalités de la définition DSL. Par exemple, vous pouvez créer un outil connecteur capable de créer plusieurs types de connecteurs et vous pouvez contrôler les règles selon lesquelles la suppression d'un élément supprime également les éléments associés. Ces techniques nécessitent la plupart du temps la définition de valeurs dans la définition DSL et certaines nécessitent quelques lignes de code de programme.

     Pour plus d’informations, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).

2.  Étendez vos outils de modélisation à l'aide de code de programme pour obtenir des effets avancés. Par exemple, vous pouvez créer des commandes de menu qui peuvent modifier le modèle et vous pouvez créer des outils qui intègrent plusieurs solutions DSL. Le Kit VMSDK a été conçu spécifiquement pour simplifier l'intégration à vos extensions avec le code généré à partir de la définition DSL.  Pour plus d’informations, consultez [écriture du Code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md).

### <a name="changing-the-dsl-definition"></a>Modification de la définition DSL
 Quand vous créez un élément dans une définition DSL, de nombreuses valeurs par défaut sont définies automatiquement. Une fois ces valeurs définies, vous pouvez les modifier. Cela simplifie le développement des solutions DSL tout en permettant d'effectuer de puissantes personnalisations.

 Par exemple, quand vous mappez une forme à un élément, le chemin d'accès à l'élément parent du mappage est défini automatiquement en fonction de la relation d'incorporation de la classe de domaine. Toutefois, si vous modifiez ultérieurement la relation d'incorporation, le chemin d'accès à l'élément parent n'est pas modifié automatiquement.

 Vous devez donc savoir que quand vous modifiez certaines relations dans votre définition DSL, il n'est pas rare que des erreurs soient signalées quand vous enregistrez la définition ou quand vous transformez tous les modèles. La plupart de ces erreurs sont faciles à corriger. Double-cliquez sur le rapport d'erreur pour afficher l'emplacement de l'erreur.

 Voir aussi [Comment : modifier le Namespace d’un langage spécifique à un domaine](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).

## <a name="trouble"></a> Résolution des problèmes
 Le tableau suivant mentionne certains des problèmes les plus courants qui peuvent être rencontrés lors de la conception d'une solution DSL, avec quelques suggestions de solution. Obtenir des conseils supplémentaires sont disponibles sur le [Forum d’extension des outils de visualisation](http://go.microsoft.com/fwlink/?LinkId=186074).

|Problème|Suggestion|
|-------------|----------------|
|Les modifications que j'ai apportées dans le fichier de définition DSL n'ont aucun effet.|Cliquez sur **transformer tous les modèles** dans la barre d’outils au-dessus de l’Explorateur de solutions, puis regénérez la solution.|
|Les formes indiquent le nom d'un décorateur au lieu de la valeur de propriété.|Configurez le mappage de décorateur. Sur le diagramme de définition DSL, cliquez sur le mappage d'élément de diagramme, c'est-à-dire la ligne grise entre la classe de domaine et la classe de forme.<br /><br /> Ouvrez le **détails DSL** fenêtre. Si vous ne voyez pas, dans le menu Affichage, pointez sur **Windows autres**, puis cliquez sur **détails DSL**.<br /><br /> Cliquez sur le **mappages de décorateurs** onglet. Sélectionnez le nom du décorateur. Vérifiez que la case correspondante est cochée. Sous **afficher la propriété**, sélectionnez le nom d’une propriété de domaine.<br /><br /> Pour plus d’informations, consultez [formes sur le diagramme](#shapes).|
|Dans l'Explorateur DSL, je ne parviens pas à ajouter de collection. Par exemple, quand je clique avec le bouton droit sur Outils, il n'y a pas de commande « Ajouter un outil » dans le menu.<br /><br /> Dans l'explorateur de ma solution DSL, je ne parviens pas à ajouter d'élément à une liste.|Cliquez avec le bouton droit sur l'élément au-dessus du nœud concerné. Quand vous souhaitez ajouter un élément à une liste, la commande Ajouter ne se trouve pas dans le nœud de la liste, mais dans son propriétaire.|
|J'ai créé une classe de domaine, mais je ne parviens pas à créer d'instances dans l'explorateur de langage.|Chaque classe de domaine, à l'exception de la racine, doit être la cible d'une relation d'incorporation.|
|Dans l'explorateur de ma solution DSL, les éléments sont affichés uniquement avec leur nom de type.|Dans la définition DSL, sélectionnez une propriété de domaine de la classe et dans les propriétés de fenêtre, définissez **Is Element Name** sur true.|
|Ma solution DSL s'ouvre toujours dans l'éditeur XML.|Cela peut être dû à une erreur lors de la lecture du fichier. Toutefois, même après avoir corrigé cette erreur, vous devez réinitialiser de manière explicite l'éditeur pour qu'il soit votre concepteur DSL.<br /><br /> Cliquez sur l’élément de projet, cliquez sur **ouvrir avec** et sélectionnez _Votre_langage_**concepteur (par défaut)**.|
|La boîte à outils de ma solution DSL n'apparaît pas après que j'ai modifié les noms des assemblys.|Examiner et mettre à jour **DslPackage\GeneratedCode\Package.tt** pour plus d’informations, consultez [Comment : modifier le Namespace d’un langage spécifique à un domaine](../modeling/how-to-change-the-namespace-of-a-domain-specific-language.md).|
|La boîte à outils de ma solution DSL n'apparaît pas, mais je n'ai pas modifié le nom de l'assembly.<br /><br /> Ou une boîte de message apparaît et signale l'échec du chargement d'une extension.|Réinitialisez l'instance expérimentale et regénérez votre solution.<br /><br /> 1.  Dans le Windows menu Démarrer, sous **tous les programmes**, développez [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)], puis **outils**, puis cliquez sur **réinitialiser l’Instance expérimentale Microsoft Visual Studio**.<br />2.  Sur le **Build** menu, cliquez sur **régénérer la Solution**.|

## <a name="see-also"></a>Voir aussi

- [Bien démarrer avec les langages spécifiques à un domaine](../modeling/getting-started-with-domain-specific-languages.md)
- [Création d’un langage spécifique à un domaine basé sur Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md)
- [Création d’un langage spécifique à un domaine basé sur WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)