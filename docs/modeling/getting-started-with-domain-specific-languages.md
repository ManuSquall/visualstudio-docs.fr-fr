---
title: Mise en route des langages spécifiques à un domaine
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93a121a103d18d886fafa2368d8669276a8010e8
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938281"
---
# <a name="get-started-with-domain-specific-languages"></a>Bien démarrer avec les langages spécifiques à un domaine

Cette rubrique explique les concepts de base dans la définition et utilisation d’un langage spécifique à un domaine (DSL) créé avec le SDK de modélisation pour Visual Studio.

> [!NOTE]
> Dans Visual Studio 2017, le SDK de Transformation de modèle de texte et le SDK de modélisation de Visual Studio sont installés automatiquement lorsque vous installez des fonctionnalités spécifiques de Visual Studio. Pour plus d’informations, consultez [ce billet de blog](https://blogs.msdn.microsoft.com/devops/2016/12/12/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

Si vous ne connaissez pas DSL, nous vous recommandons de collaborer via le **atelier des outils DSL**, que vous trouverez dans ce site : [SDK de création et de modélisation](http://go.microsoft.com/fwlink/?LinkID=186128)

## <a name="what-can-you-do-with-a-domain-specific-language"></a>Que pouvez-vous faire avec un langage spécifique à un domaine ?

Un langage spécifique à un domaine est une notation, en général graphique, qui est conçue pour être utilisé pour un usage particulier. En revanche, les langages tels que UML sont à usage général. Dans une solution DSL, vous pouvez définir les types d’élément de modèle et leurs relations, et comment elles sont présentées à l’écran.

Lorsque vous avez conçu une solution DSL, vous pouvez le distribuer dans le cadre d’un package d’Extension d’intégration Visual Studio (VSIX). Les utilisateurs travaillent avec la solution DSL dans Visual Studio :

![Diagramme d’arbre généalogique, boîte à outils et explorateur](../modeling/media/familyt_instance.png)

La notation n'est qu’une partie d’une solution DSL. Avec la notation, votre package VSIX inclut des outils que les utilisateurs peuvent appliquer pour les aider à modifier et générer le matériel à partir de leurs modèles.

L’une des applications de DSL principal consiste à générer du code de programme, les fichiers de configuration et les autres artefacts. En particulier dans les grands projets et des gammes de produits, où plusieurs variantes d’un produit doit être créés, générer de nombreux aspects de la variable à partir de langages DSL peut fournir une augmentation importante de la fiabilité et une réaction rapide aux changements d’impératifs.

Le reste de cette vue d’ensemble est une procédure pas à pas qui présente les opérations de base de la création et à l’aide d’un langage spécifique à un domaine dans Visual Studio.

## <a name="prerequisites"></a>Prérequis

Pour définir un DSL, vous devez avoir installé les composants suivants :


| | |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580) |
| SDK Modeling pour Visual Studio | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="create-a-dsl-solution"></a>Créer une Solution DSL

Pour créer un nouveau langage spécifique à un domaine, vous créez une nouvelle solution Visual Studio en utilisant le modèle de projet de langage spécifique à un domaine.

1.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

2.  Sous **types de projets**, développez le **autres Types de projets** nœud, puis cliquez sur **extensibilité**.

3.  Cliquez sur **Domain-Specific Language concepteur**.

     ![Boîte de dialogue Créer DSL](../modeling/media/create_dsldialog.png)

4.  Dans le **nom** , tapez **FamilyTree**. Cliquez sur **OK**.

     Le **Domain-Specific Language Assistant** s’ouvre et affiche une liste des solutions de modèle DSL.

     Cliquez sur chaque modèle pour afficher la description,

     Les modèles sont utiles points de départ. Chacun d’eux fournit un complète DSL, que vous pouvez modifier selon vos besoins. En règle générale, vous devez choisir le modèle le plus proche de ce que vous voulez créer.

5.  Pour cette procédure pas à pas, choisissez le **langage Minimal** modèle.

6.  Entrez une extension de nom de fichier pour votre solution DSL dans la page appropriée de l'Assistant. Il s'agit de l'extension qui sera utilisée par les fichiers contenant des instances de votre solution DSL.

    -   Choisissez une extension qui n’est pas associée à n’importe quelle application sur votre ordinateur, ou dans n’importe quel ordinateur où vous souhaitez installer la solution DSL. Par exemple, **docx** et **htm** serait fichiers inacceptables extensions de nom.

    -   L'Assistant vous avertit si l'extension que vous avez entrée est utilisée actuellement comme DSL. Dans ce cas, utilisez une autre extension de nom de fichier. Vous pouvez aussi réinitialiser l'instance expérimentale du Kit SDK Visual Studio pour effacer les anciennes conceptions expérimentales. Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, **Microsoft Visual Studio 2010 SDK**, **outils**, puis **réinitialiser Microsoft Instance de Visual Studio 2010 expérimental**.

7.  Inspecter les autres pages, puis cliquez sur **Terminer**.

     Une solution contenant deux projets est générée. Ils sont nommés Dsl et DslPackage. Un fichier de diagramme s’ouvre qui est nommé DslDefinition.dsl.

    > [!NOTE]
    > La plupart du code que vous pouvez le voir dans les dossiers dans les deux projets est généré à partir de DslDefinition.dsl. Pour cette raison, la plupart des modifications à votre solution DSL sont effectuées dans ce fichier.

L'interface utilisateur ressemble maintenant à l'image suivante.

![concepteur dsl](../modeling/media/dsl_designer.png)

Cette solution définit un langage spécifique à un domaine. Pour plus d’informations, consultez [vue d’ensemble de l’Interface utilisateur des outils Domain-Specific Language](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

## <a name="the-important-parts-of-the-dsl-solution"></a>Les parties importantes de la solution DSL

Notez les aspects suivants de la nouvelle solution :

-   **Dsl\DslDefinition.DSL** c’est le fichier que vous voyez lorsque vous créez une solution DSL. Presque tout le code dans la solution est généré à partir de ce fichier, et la plupart des modifications que vous apportez à une définition DSL est effectuée ici. Pour plus d’informations, voir Utilisation de la [fonctionne avec le diagramme de définition DSL](../modeling/working-with-the-dsl-definition-diagram.md).

-   **Projet DSL** ce projet contient le code qui définit la langue spécifique à un domaine.

-   **Projet DslPackage** ce projet contient le code qui permet aux instances du DSL pour pouvoir ouvrir et modifier dans Visual Studio.

##  <a name="Debugging"></a> La solution DSL en cours d’exécution

Vous pouvez exécuter la solution DSL dès que vous l’avez créé. Une version ultérieure, vous pouvez modifier la définition DSL progressivement, l’exécution de la solution après chaque modification.

### <a name="to-experiment-with-the-dsl"></a>Pour faire des essais avec la solution DSL

1.  Cliquez sur **transformer tous les modèles** dans le **l’Explorateur de solutions** barre d’outils. Cette opération régénère la plupart du code source à partir de DslDefinition.dsl.

    > [!NOTE]
    > Chaque fois que vous modifiez *DslDefinition.dsl*, vous devez cliquer sur **transformer tous les modèles** avant de reconstruire la solution. Vous pouvez automatiser cette étape. Pour plus d’informations, consultez [comment automatiser transformer tous les modèles](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

2.  Appuyez sur **F5**, ou dans le menu **Déboguer** , choisissez **Démarrer le débogage**.

     La solution DSL génère et est installé dans l’instance expérimentale de Visual Studio.

     Une instance expérimentale de Visual Studio démarre. L’instance expérimentale prend ses paramètres à partir d’une sous-arborescence distincte du Registre, où les extensions de Visual Studio sont enregistrées pour le débogage. Les instances normales de Visual Studio n’ont pas de l’accès aux extensions y est inscrit.

3.  Dans l’instance expérimentale de Visual Studio, ouvrez le fichier de modèle nommé **Test** de **l’Explorateur de solutions**.

     \- ou -

     Cliquez sur le projet de débogage, pointez sur **ajouter**, puis cliquez sur **élément**. Dans le **ajouter un élément** boîte de dialogue, sélectionnez le type de fichier de votre DSL.

     Le fichier de modèle s’ouvre sous forme de diagramme vide.

     La boîte à outils s’ouvre et affiche les outils appropriés pour le type de diagramme.

4.  Utilisez les outils pour créer des formes et connecteurs sur le diagramme.

    1.  Pour créer des formes, faites glisser à partir de l’outil de forme d’exemple vers le diagramme.

    2.  Pour relier deux formes, cliquez sur l’outil de connecteur de l’exemple, cliquez sur la première forme, puis cliquez sur la deuxième forme.

5.  Cliquez sur les étiquettes des formes pour les modifier.

Votre expérimentale de Visual Studio doit ressembler à l’exemple suivant :

![](../modeling/media/dsl_min.png)

### <a name="the-content-of-a-model"></a>Le contenu d’un modèle

Le contenu d’un fichier qui est une instance d’une solution DSL est appelé un *modèle*. Le modèle contient *modèle*<em>éléments</em> et *liens* entre les éléments. La définition DSL spécifie quels types d’éléments de modèle et des liens peuvent exister dans le modèle. Par exemple, dans un DSL créé à partir du modèle de langage Minimal, il est a un seul type d’élément de modèle et un type de lien.

La définition DSL peut de spécifier comment le modèle apparaît dans un diagramme. Vous pouvez choisir parmi un éventail de styles de formes et connecteurs. Vous pouvez spécifier que certaines formes apparaissent dans d’autres formes.

Vous pouvez afficher un modèle sous forme d’arborescence dans le **Explorer** afficher lorsque vous modifiez un modèle. Lorsque vous ajoutez des formes au diagramme, les éléments de modèle apparaissent également dans l’Explorateur. L’Explorateur peut être utilisé même s’il n’existe aucun diagramme.

Si vous ne voyez pas l’Explorateur de l’instance de débogage de Visual Studio, sur le **vue** menu, pointez sur **Windows autres**, puis cliquez sur  *\<votre langue >* **Explorer**.

### <a name="the-api-of-your-dsl"></a>L’API de votre DSL

Votre solution DSL génère une API qui vous permet de lire et mettre à jour de modèles qui sont des instances du DSL. Une application de l’API consiste à générer des fichiers texte à partir d’un modèle. Pour plus d’informations, consultez [génération de Code au moment du Design à l’aide de modèles de texte T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Dans la solution de débogage, ouvrez les fichiers de modèle avec l’extension « .tt ». Ces exemples montrent comment vous pouvez générer du texte à partir de modèles et vous permettent de tester l’API de votre DSL. Un des exemples est écrit [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], les autres dans [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].

Sous chaque modèle de fichier est le fichier qu’il génère. Développez le fichier de modèle dans l’Explorateur de solutions et ouvrez le fichier généré.

Le fichier modèle contient un petit segment de code qui répertorie tous les éléments dans le modèle.

Le fichier généré contient le résultat.

Lorsque vous modifiez un fichier de modèle, vous verrez les modifications correspondantes dans les fichiers générés une fois que vous régénérez les fichiers.

#### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Pour régénérer les fichiers texte après avoir modifié le fichier de modèle

1.  Dans l’instance expérimentale de Visual Studio, enregistrez le fichier de modèle.

2.  Assurez-vous que le paramètre de nom de fichier dans chaque fichier .tt fait référence au fichier de modèle que vous utilisez des expériences. Enregistrez le fichier .tt.

3.  Cliquez sur **transformer tous les modèles** dans la barre d’outils de **l’Explorateur de solutions**.

     \- ou -

     Cliquez sur les modèles que vous souhaitez régénérer, puis cliquez sur **exécuter un outil personnalisé**.

Vous pouvez ajouter n’importe quel nombre de fichiers de modèle de texte à un projet. Chaque modèle génère un fichier de résultat.

> [!NOTE]
> Lorsque vous modifiez la définition DSL, l’exemple de code de modèle de texte ne fonctionne pas, sauf si vous mettez à jour.

Pour plus d’informations, consultez [génération du Code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md) et [écriture du Code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md).

## <a name="customizing-the-dsl"></a>Personnalisation de la solution DSL

Lorsque vous souhaitez modifier la définition DSL, fermez l’instance expérimentale et mettre à jour de la définition dans l’instance principale de Visual Studio.

> [!NOTE]
> Une fois que vous avez modifié la définition DSL, vous risquez de perdre des informations dans les modèles de test que vous avez créé à l’aide de versions antérieures.  Par exemple, la solution de débogage contient un fichier nommé exemple, qui contient des formes et les connecteurs. Une fois que vous commencez à développer votre définition DSL, ils ne seront pas visibles, et ils seront perdus lorsque vous enregistrez le fichier.

Un large éventail d’extensions possibles pour votre DSL. Les exemples suivants vous donner une impression des possibilités.

Après chaque modification, enregistrez la définition DSL, cliquez sur **transformer tous les modèles** dans **l’Explorateur de solutions**, puis appuyez sur **F5** à faire des essais avec la solution DSL modifiée.

### <a name="rename-the-types-and-tools"></a>Renommer les Types et les outils

Renommez les classes de domaine existants et les relations. Par exemple, à partir d’une définition Dsl créé à partir du modèle de langage Minimal, vous pourrez effectuer les opérations de changement de nom suivantes, pour rendre la solution DSL représentent des arborescences de famille.

#### <a name="to-rename-domain-classes-relationships-and-tools"></a>Pour renommer des outils, les relations et les classes de domaine

1.  Dans le diagramme DslDefinition, renommez **ExampleModel** à **FamilyTreeModel**, **ExampleElement** à **personne**,  **Cibles** à **Parents**, et **Sources** à **enfants**. Vous pouvez cliquer sur chaque étiquette pour la modifier.

     ![Diagramme de définition DSL &#45; modèle d’arbre généalogique](../modeling/media/familyt_person.png)

2.  Renommez les outils de l’élément et le connecteur.

    1.  En cliquant sur l’onglet Explorateur de solutions, ouvrez la fenêtre Explorateur DSL. Si vous ne s’affiche pas, sur le **vue** menu, pointez sur **Windows autres** puis cliquez sur **Explorateur DSL**. Explorateur DSL est visible uniquement lorsque le diagramme de définition DSL est la fenêtre active.

    2.  Ouvrez la fenêtre Propriétés et positionnez-le de sorte que vous puissiez voir Explorateur DSL et des propriétés en même temps.

    3.  Dans l’Explorateur DSL, développez **éditeur**, **onglets de boîte à outils**,  *\<votre DSL >*, puis **outils**.

    4.  Cliquez sur **ExampleElement**. Il s’agit de l’élément de boîte à outils qui est utilisé pour créer des éléments.

    5.  Dans la fenêtre Propriétés, modifiez le **nom** propriété **personne**.

         Notez que le **légende** propriété change également.

    6.  Dans la même manière, remplacez le nom de la **ExampleConnector** outil pour **ParentLink**. Modifier le **légende** propriété afin qu’elle n’est pas une copie de la propriété Name. Par exemple, entrez **lien Parent**.

3.  Régénérez la solution DSL.

    1.  Enregistrez le fichier de définition DSL.

    2.  Cliquez sur **transformer tous les modèles** dans la barre d’outils de l’Explorateur de solutions

    3.  Appuyez sur F5. Patientez jusqu'à ce que l’instance expérimentale de Visual Studio s’affiche.

4.  Dans la solution de débogage dans l’instance expérimentale de Visual Studio, ouvrez un fichier de modèle de test. Faites glisser des éléments sur la boîte à outils. Notez que les légendes de l’outil et les noms de types dans l’Explorateur DSL ont été modifiés.

5.  Enregistrez le fichier de modèle.

6.  Ouvrir un fichier .tt et remplacer les occurrences les anciens noms de types et propriétés avec les nouveaux noms.

7.  Assurez-vous que le nom de fichier spécifié dans le fichier .tt Spécifie votre modèle de test.

8.  Enregistrez le fichier .tt. Ouvrez le fichier généré pour voir le résultat de l’exécution du code dans le fichier .tt. Vérifiez qu’il est correct.

### <a name="add-domain-properties-to-classes"></a>Ajouter des propriétés de domaine aux Classes
 Ajouter des propriétés à une classe de domaine, par exemple pour représenter les années de naissance et de décès d’une personne.

 Pour rendre les nouvelles propriétés visibles dans le diagramme, vous devez ajouter *décorateurs* à la forme qui affiche l’élément de modèle. Vous devez également mapper les propriétés pour les éléments décoratifs.

##### <a name="to-add-properties-and-display-them"></a>Pour ajouter des propriétés et les afficher

1. Ajoutez les propriétés.

   1.  Dans le diagramme de définition DSL, cliquez sur le **personne** de classe de domaine, pointez sur **ajouter**, puis cliquez sur **de propriété de domaine**.

   2.  Tapez une liste de nouveaux noms de propriété, tel que **naissance** et **mort**. Appuyez sur **entrée** après chacune d’elles.

2. Ajouter des éléments décoratifs qui affichent les propriétés de la forme.

   1.  Suivez la ligne grise qui s’étend la classe de domaine de personne à l’autre côté du diagramme. Il s’agit d’un mappage d’élément de diagramme. Il lie la classe de domaine à une classe de forme.

   2.  Avec le bouton droit de cette classe de forme, pointez sur **ajouter**, puis cliquez sur **décorateur de texte**.

   3.  Ajouter deux éléments décoratifs avec des noms tels que **BirthDecorator** et **DeathDecorator**.

   4.  Sélectionnez chaque nouvel élément décoratif et dans la fenêtre Propriétés, définissez la **Position** champ. Ce paramètre détermine où la valeur de propriété de domaine s’affichera sur la forme. Par exemple, définissez **InnerBottomLeft** et **InnerBottomRight**.

        ![Définition de forme de compartiment](../modeling/media/familyt_compartment.png)

3. Mapper les éléments décoratifs aux propriétés.

   1.  Ouvrez la fenêtre Détails DSL. Il est généralement dans un onglet en regard de la fenêtre Sortie. Si vous ne s’affiche pas, sur le **vue** menu, pointez sur **Windows autres**, puis cliquez sur **détails DSL**.

   2.  Sur le diagramme de définition DSL, cliquez sur la ligne qui relie le **personne** de classe de domaine à la classe de forme.

   3.  Dans **détails DSL**, dans le **mappages de décorateurs** , cliquez sur la case à cocher sur un élément décoratif non mappé. Dans **propriété d’affichage**, sélectionnez la propriété de domaine auquel il est mappé. Par exemple, mapper **BirthDecorator** à **naissance**.

4. Enregistrer la solution DSL, cliquez sur Transformer tous les modèles et appuyez sur F5.

5. Dans un exemple de diagramme de modèle, vérifiez que vous pouvez maintenant cliquer les positions que vous avez choisi et tapez des valeurs dans les. En outre, lorsque vous sélectionnez un **personne** forme, la fenêtre Propriétés affiche les nouvelles propriétés de naissance et décès.

6. Dans un fichier .tt, vous pouvez ajouter le code qui obtient les propriétés de chaque personne.

   ![Diagramme d’arbre généalogique, boîte à outils et explorateur](../modeling/media/familyt_instance.png)

### <a name="define-new-classes"></a>Définir de nouvelles Classes
 Vous pouvez ajouter des classes de domaine et les relations à un modèle. Par exemple, vous pouvez créer une nouvelle classe pour représenter les villes et une nouvelle relation pour représenter qu’une personne vécu dans une ville.

 Pour rendre les différents types distincts sur un diagramme de modèle, vous pouvez mapper les classes de domaine à différents types de forme, ou à des formes avec les couleurs et de géométrie différentes.

##### <a name="to-add-and-display-a-new-domain-class"></a>Ajout et affichage d’une nouvelle classe de domaine

1.  Ajoutez une classe de domaine et définissez-la comme enfant de la racine du modèle.

    1.  Dans le diagramme de définition DSL, cliquez sur le **relation d’incorporation** outil, cliquez sur la classe racine **FamilyTreeModel**, puis cliquez sur une partie vide du diagramme.

         Une nouvelle classe de domaine apparaît, qui est connecté à la FamilyTreeModel avec une relation d’incorporation.

         Définissez son nom, par exemple **Town**.

        > [!NOTE]
        >  Chaque classe de domaine à l’exception de la racine du modèle doit être la cible d’au moins une relation d’incorporation, ou il doit hériter d’une classe qui est la cible d’une imbrication. Pour cette raison, il est souvent pratique de créer une classe de domaine à l’aide de l’outil de relation d’incorporation.

    2.  Ajouter une propriété de domaine à la nouvelle classe, par exemple **nom**.

2.  Ajouter une relation de référence entre personne et ville.

    1.  Cliquez sur le **relation de référence** d’outils, cliquez sur une personne et puis cliquez sur Ville.

         ![Fragment de définition DSL : racine d’arbre généalogique](../modeling/media/familyt_root.png)

        > [!NOTE]
        >  Référence représentent des références croisées à partir d’une partie de l’arborescence du modèle vers un autre.

3.  Ajoutez une forme pour représenter des villes sur les diagrammes de modèle.

    1.  Faites glisser un **forme géométrique** à partir de la boîte à outils vers le diagramme et renommez-la, par exemple **TownShape**.

    2.  Dans la fenêtre Propriétés, définissez les champs de l’apparence de la nouvelle forme, telles que la couleur de remplissage et la géométrie.

    3.  Ajoutez un élément décoratif pour afficher le nom de la ville et renommez-le NameDecorator. Définissez sa propriété de Position.

4.  Mapper la classe de domaine de ville à la TownShape.

    1.  Cliquez sur le **mappage d’élément de diagramme** outil, puis cliquez sur la classe de domaine de ville, puis la classe de forme TownShape.

    2.  Dans le **mappages de décorateurs** onglet de la **détails DSL** fenêtre avec le connecteur de la carte sélectionnée, vérifiez NameDecorator et définissez **propriété d’affichage** au nom.

5.  Créer un connecteur pour afficher la relation entre personne et villes.

    1.  Faites glisser un connecteur à partir de la boîte à outils vers le diagramme. Renommez-la et définissez ses propriétés d’apparence.

    2.  Utilisez le **mappage d’élément de diagramme** outil pour lier le nouveau connecteur à la relation entre personne et ville.

         ![Définition d’arbre généalogique avec mappage de forme ajouté](../modeling/media/familyt_shapemap.png)

6.  Créer un outil d’élément pour effectuer une nouvelle ville.

    1.  Dans **Explorateur DSL**, développez **éditeur** puis **onglets de boîte à outils**.

    2.  Avec le bouton droit  *\<votre DSL >* puis cliquez sur **ajouter un nouvel outil élément**.

    3.  Définir le **nom** propriété du nouvel outil et ensemble son **classe** propriété ville.

    4.  Définir le **icône Boîte à outils** propriété. Cliquez sur **[...]**  et dans le **nom de fichier** , sélectionnez un fichier icône.

7.  Créer un outil de connecteur pour effectuer un lien entre les villes et les personnes.

    1.  Avec le bouton droit  *\<votre DSL >* puis cliquez sur **ajouter un nouvel outil de connecteur**.

    2.  Définissez la propriété Name du nouvel outil.

    3.  Dans le **ConnectionBuilder** propriété, sélectionnez le générateur qui contient le nom de la relation de type personne-ville.

    4.  Définir le **icône Boîte à outils**.

8.  Enregistrer la définition DSL, cliquez sur **transformer tous les modèles**, puis appuyez sur **F5**.

9. Dans l’instance expérimentale de Visual Studio, ouvrez un fichier de modèle de test. Utilisez les nouveaux outils pour créer les villes et les liens entre les villes et les personnes. Notez que vous pouvez uniquement créer des liens entre les types d’élément pertinents.

10. Créer du code qui répertorie la ville dans laquelle se trouve chaque personne. Modèles de texte sont les emplacements où vous pouvez exécuter ce code. Par exemple, vous pouvez modifier le fichier Sample.tt existant dans la solution de débogage pour qu’il contienne le code suivant :

    ```
    <#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" debug="true" #>
    <#@ output extension=".txt" #>
    <#@ FamilyTree processor="FamilyTreeDirectiveProcessor" requires="fileName='Sample.ftree'" #>

    <#
      foreach (Person person in this.FamilyTreeModel.People)
      {
    #>
        <#= person.Name #><#if (person.Town != null) {#> of <#= person.Town.Name #> <#}#>

    <#
          foreach (Person child in person.Children)
      {
    #>
                <#= child.Name #>
    <#
      }
      }
    #>

    ```

     Lorsque vous enregistrez le fichier *.tt, il créera un fichier auxiliaire qui contient la liste des personnes et leurs foyers. Pour plus d’informations, consultez [génération du Code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="validation-and-commands"></a>Validation et commandes
 Vous pouvez développer davantage ce DSL en ajoutant des contraintes de validation. Ces contraintes sont des méthodes que vous pouvez définir, assurez-vous que le modèle est dans un état correct. Par exemple, vous pouvez définir une contrainte pour vous assurer que la date de naissance d’un enfant est ultérieure à celle de ses parents. La fonctionnalité de validation affiche un avertissement si l’utilisateur tente d’enregistrer un modèle qui déclenche une des contraintes. Pour plus d’informations, consultez [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md).

 Vous pouvez également définir des commandes de menu que l’utilisateur peut appeler. Commandes peuvent modifier le modèle. Ils peuvent également interagir avec d’autres modèles dans Visual Studio et avec les ressources externes. Pour plus d'informations, voir [Procédure : Modifier une commande de Menu Standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="deploying-the-dsl"></a>Déploiement de la solution DSL
 Pour autoriser d’autres utilisateurs d’utiliser le langage spécifique à un domaine, vous distribuez un fichier d’Extension Visual Studio (VSIX). Il est créé lorsque vous générez la solution DSL.

 Recherchez le fichier .vsix dans le dossier bin de votre solution. Copiez-le sur l’ordinateur sur lequel vous souhaitez l’installer. Sur cet ordinateur, double-cliquez sur le fichier VSIX. La solution DSL peut servir dans toutes les instances de Visual Studio sur cet ordinateur.

 Vous pouvez utiliser la même procédure pour installer la solution DSL sur votre ordinateur afin que vous n’avez pas à utiliser l’instance expérimentale de Visual Studio.

 Pour plus d’informations, consultez [Déploiement de solutions de langage spécifique à un domaine](../modeling/deploying-domain-specific-language-solutions.md).

##  <a name="Reset"></a> Suppression des anciennes DSL expérimental
 Si vous avez créé plusieurs DSL expérimentale que vous ne souhaitez plus, vous pouvez les supprimer à partir de votre ordinateur en réinitialisant l’instance expérimentale de Visual Studio.

 Cela supprimera de votre ordinateur toutes les DSL expérimentale et autres extensions de Visual Studio expérimentales. Il s’agit d’extensions qui ont été exécutées en mode débogage.

 Cette procédure ne supprime pas DSL ou autres extensions de Visual Studio qui ont été entièrement installées en exécutant le fichier VSIX.

#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Pour réinitialiser l’instance expérimentale de Visual Studio

1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, **Microsoft Visual Studio 2010 SDK**, **outils**, puis **réinitialiser Microsoft Instance de Visual Studio 2010 expérimental**.

2.  Reconstruisez tout expérimentale DSL ou autres extensions expérimentales Visual Studio que vous souhaitez toujours utiliser.

## <a name="see-also"></a>Voir aussi

- [Présentation des modèles, des classes et des relations](../modeling/understanding-models-classes-and-relationships.md)
- [Guide pratique pour définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)