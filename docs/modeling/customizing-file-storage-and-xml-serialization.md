---
title: Personnalisation du stockage de fichiers et de la sérialisation XML
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8a21067eab6e55f3fb031e57fa2257b0d40a7eb6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886459"
---
# <a name="customize-file-storage-and-xml-serialization"></a>Personnaliser le stockage de fichiers et la sérialisation XML

Quand l’utilisateur enregistre une instance, ou *modèle*, d’un langage spécifique à un domaine (DSL) dans Visual Studio, un fichier XML est créé ou mis à jour. Le fichier peut être rechargé pour recréer le modèle dans le Store.

Vous pouvez personnaliser le schéma de sérialisation en ajustant les paramètres sous **comportement de sérialisation Xml** dans l’Explorateur DSL. Il existe un nœud sous **comportement de sérialisation Xml** pour chaque classe de domaine, la propriété et la relation. Les relations sont situées sous leurs classes de source. Il existe également des nœuds correspondant à la forme, connecteur et les classes de diagramme.

Vous pouvez également écrire du code de programme pour une personnalisation avancée.

> [!NOTE]
> Si vous souhaitez enregistrer le modèle dans un format particulier, mais vous n’avez pas besoin de le recharger à partir de ce formulaire, envisagez d’utiliser des modèles de texte pour générer la sortie à partir du modèle, au lieu d’un schéma de sérialisation personnalisée. Pour plus d’informations, consultez [génération du Code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="model-and-diagram-files"></a>Fichiers de modèle et diagramme

Chaque modèle est généralement enregistrée dans les deux fichiers :

-   Le fichier de modèle a un nom tel que **Model1.mydsl**. Il stocke les éléments de modèle et les relations et leurs propriétés. L’extension de fichier comme **.mydsl** est déterminée par le **FileExtension** propriété de la **éditeur** nœud dans la définition DSL.

-   Le fichier de diagramme a un nom tel que **Model1.mydsl.diagram**. Il stocke les formes, connecteurs et leurs positions, couleurs, épaisseurs et autres détails de l’apparence du diagramme. Si l’utilisateur supprime un **.diagram** fichier, les informations essentielles dans le modèle ne sont pas perdues. Uniquement à la disposition du diagramme est perdue. Lorsque le fichier de modèle est ouvert, une valeur par défaut définie de formes et connecteurs seront créées.

### <a name="to-change-the-file-extension-of-a-dsl"></a>Pour modifier l’extension de fichier d’une solution DSL

1.  Ouvrez la définition DSL. Dans l’Explorateur DSL, cliquez sur le nœud de l’éditeur.

2.  Dans la fenêtre Propriétés, modifiez le **FileExtension** propriété. N’incluez pas initial «. » de l’extension de nom de fichier.

3.  Dans l’Explorateur de solutions, remplacez le nom des fichiers de modèle de deux éléments dans **DslPackage\ProjectItemTemplates**. Ces fichiers ont des noms qui respectent le format :

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>Le schéma de sérialisation par défaut

Pour créer un exemple de cette rubrique, la définition DSL suivante a été utilisée.

![Diagramme de définition DSL &#45; modèle d’arbre généalogique](../modeling/media/familyt_person.png)

Cette solution DSL a été utilisé pour créer un modèle qui a l’aspect suivant sur l’écran.

![Diagramme d’arbre généalogique, boîte à outils et explorateur](../modeling/media/familyt_instance.png)

Ce modèle a été enregistré et ouvert dans l’éditeur de texte XML :

```xml
<?xml version="1.0" encoding="utf-8"?>
<familyTreeModel xmlns:dm0="http://schemas.microsoft.com/VisualStudio/2008/DslTools/Core" dslVersion="1.0.0.0" Id="f817b728-e920-458e-bb99-98edc469d78f" xmlns="http://schemas.microsoft.com/dsltools/FamilyTree">
  <people>
    <person name="Henry VIII" birthYear="1491" deathYear="1547" age="519">
      <children>
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
        <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Mary" />
      </children>
    </person>
    <person name="Elizabeth I" birthYear="1533" deathYear="1603" age="477" />
    <person name="Mary" birthYear="1515" deathYear="1558" age="495" />
  </people>
</familyTreeModel>
```

Notez les points suivants concernant le modèle sérialisé :

-   Chaque nœud XML a un nom qui est identique à un nom de classe de domaine, à ceci près que la lettre initiale est en minuscule. Par exemple : `familyTreeModel` et `person`.

-   Propriétés de domaine comme le nom et l’année de naissance sont sérialisées en tant qu’attributs dans les nœuds XML. Là encore, du caractère initial de la propriété est converti en minuscules.

-   Chaque relation est sérialisée comme un nœud XML imbriqué à l’intérieur de la fin de la source de la relation. Le nœud a le même nom que la propriété de rôle source, mais avec un caractère initial en minuscules.

     Par exemple, dans la définition DSL, un rôle nommé **personnes** comme source la **FamilyTree** classe.  Dans le code XML, ceci est représenté par le nœud nommé `people` imbriqué dans le `familyTreeModel` nœud.

-   L’extrémité cible de chaque relation d’incorporation est sérialisée en tant que nœud imbriqué sous la relation. Par exemple, le `people` nœud contient plusieurs `person` nœuds.

-   L’extrémité cible de chaque relation de référence est sérialisée comme un *moniker*, qui encode une référence à l’élément cible.

     Par exemple, sous un `person` nœud, il peut y avoir un `children` relation. Ce nœud contient les monikers telles que :

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>Comprendre les Monikers

Monikers sont utilisés pour représenter des références croisées entre les différentes parties des fichiers de modèle et de diagramme. Ils sont également utilisés dans le `.diagram` fichier pour faire référence aux nœuds dans le fichier de modèle. Il existe deux formes de moniker :

-   *Les monikers ID* citer le GUID de l’élément cible. Exemple :

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

-   *Qualifié monikers clés* identifier l’élément cible par la valeur d’une propriété de domaine désignée appelée la clé de moniker. Le moniker de l’élément cible est préfixé par le moniker de son élément parent dans l’arborescence de relations d’incorporation.

     Les exemples suivants sont effectuées à partir d’une solution DSL dans lequel il est une classe de domaine nommée Album, ce qui a une relation d’incorporation à un domaine nommé chanson de classe :

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     Les monikers de clé qualifiés seront utilisés si la classe cible possède une propriété de domaine pour lequel l’option **est la clé de Moniker** a la valeur `true` dans **comportement de sérialisation Xml**. Dans l’exemple, cette option est définie pour les propriétés de domaine nommées « Title » dans les classes de domaine « Album » et « Morceau ».

Monikers clés qualifiés sont plus faciles à lire que les monikers ID. Si vous envisagez le code XML de vos fichiers de modèle pour être lu par des personnes, envisagez d’utiliser des monikers clés qualifiés. Toutefois, il est possible pour l’utilisateur de définir plusieurs éléments pour que la même clé de moniker. Clés dupliquées peut entraîner la recharge du fichier ne pas correctement. Par conséquent, si vous définissez une classe de domaine qui est référencée à l’aide de monikers clés qualifiés, vous devez envisager des façons d’empêcher l’utilisateur d’enregistrer un fichier qui a des monikers en double.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Pour définir une classe de domaine devant être référencé par les monikers ID

1.  Assurez-vous que l’option **est la clé de Moniker** est `false` pour chaque propriété de domaine dans la classe et ses classes de base.

    1.  Dans l’Explorateur DSL, développez **Behavior\Class données de la sérialisation Xml\\\<la classe de domaine > \Element données**.

    2.  Vérifiez que **est la clé de Moniker** est `false` pour chaque propriété de domaine.

    3.  Si la classe de domaine a une classe de base, répétez la procédure décrite dans cette classe.

2.  Définissez **Id de sérialisation**  =  `true` pour la classe de domaine.

     Cette propriété peut être trouvée sous **comportement de sérialisation Xml**.

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Pour définir une classe de domaine devant être référencé par des monikers clés qualifiés

-   Définissez **est la clé de Moniker** pour une propriété de domaine d’une classe de domaine existante. Le type de la propriété doit être `string`.

    1.  Dans l’Explorateur DSL, développez **Behavior\Class données de la sérialisation Xml\\\<la classe de domaine > \Element données**, puis sélectionnez la propriété de domaine.

    2.  Dans la fenêtre Propriétés, définissez **est la clé de Moniker** à `true`.

-   \- ou -

     Créer une nouvelle classe de domaine à l’aide du **nommé la classe de domaine** outil.

     Cet outil crée une nouvelle classe qui possède une propriété de domaine appelée nom. Le **Is Element Name** et **est la clé de Moniker** propriétés de cette propriété de domaine sont initialisées à `true`.

-   \- ou -

     Créer une relation d’héritage à partir de la classe de domaine à une autre classe qui a une propriété de clé de moniker.

### <a name="avoid-duplicate-monikers"></a>Éviter les Monikers en double

Si vous utilisez des monikers clés qualifiés, il est possible que deux éléments dans un modèle utilisateur peut avoir la même valeur dans la propriété de clé. Par exemple, si votre DSL possède une personne qui a une propriété de nom de classe, l’utilisateur peut définir les noms de deux éléments identiques. Bien que le modèle peut être enregistré dans le fichier, il serait recharge pas correctement.

Il existe plusieurs méthodes qui aident à éviter cette situation :

-   Définissez **Is Element Name**  =  `true` pour la propriété de domaine clé. Sélectionnez la propriété de domaine sur le diagramme de définition DSL et définissez la valeur dans la fenêtre Propriétés.

     Lorsque l’utilisateur crée une nouvelle instance de la classe, cette valeur, la propriété de domaine soit attribué automatiquement une valeur différente. Le comportement par défaut ajoute un nombre à la fin du nom de classe. Cela n’empêche pas l’utilisateur de changer le nom à un doublon, mais cela vous permet du cas lorsque l’utilisateur ne définit pas la valeur avant d’enregistrer le modèle.

-   Activer la validation de la solution DSL. Dans l’Explorateur DSL, sélectionnez éditeur\validation et définissez le **utilise...**  propriétés à `true`.

     Il existe une méthode de validation généré automatiquement qui vérifie pour les ambiguïtés. La méthode est dans le `Load` catégorie de validation. Cela permet de s’assurer que l’utilisateur est averti qu’il ne pourrait pas être possible de rouvrir le fichier.

     Pour plus d’informations, consultez [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md).

### <a name="moniker-paths-and-qualifiers"></a>Les qualificateurs et des chemins d’accès du moniker

Moniker qualifié clé se termine par la clé de moniker et est préfixé avec le moniker de son parent dans l’arborescence d’incorporation. Par exemple, si le moniker d’un Album est :

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

Une des morceaux de cet Album peut être :

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

Toutefois, si au lieu de cela, les Albums sont référencées par ID, puis les monikers se présente comme suit :

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

Notez qu’un GUID étant unique, il est jamais préfixé par le moniker de son parent.

Si vous savez qu’une propriété de domaine particulier aura toujours une valeur unique au sein d’un modèle, vous pouvez définir **est un qualificateur de Moniker** à `true` pour cette propriété. Cela entraîne de pouvoir être utilisé en tant que qualificateur, sans utiliser le moniker du parent. Par exemple, si vous définissez à la fois **est un qualificateur de Moniker** et **est la clé de Moniker** pour la propriété de domaine Title de la classe Album, nom ou l’identificateur du modèle n'est pas utilisé dans les monikers pour Album et son embedded enfants :

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>Personnaliser la structure du document XML

Pour effectuer les personnalisations suivantes, développez le **comportement de sérialisation Xml** nœud dans l’Explorateur DSL. Sous une classe de domaine, développez le nœud de données de l’élément pour afficher la liste des propriétés et des relations qui sont générées à cette classe. Sélectionnez une relation, ajuster ses options dans la fenêtre Propriétés.

-   Définissez **omettre un élément** comme « true » pour omettre le nœud de rôle source, en laissant uniquement la liste des éléments cibles. Vous ne devez pas définir cette option s’il existe plusieurs relations entre les classes source et cible.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

-   Définissez **utiliser le formulaire complet** pour incorporer les nœuds cibles dans les nœuds représentant les instances de relation. Cette option est définie automatiquement lorsque vous ajoutez des propriétés de domaine à une relation de domaine.

    ```xml
    <familyTreeModel ...>
      <people>
        <!-- The following node is inserted by using Use Full Form: -->
        <familyTreeModelHasPeople myRelationshipProperty="x1">
          <person name="Henry VIII" .../>
        </familyTreeModelHasPeople>
        <familyTreeModelHasPeople myRelationshipProperty="x2">
          <person name="Elizabeth I" .../>
        </familyTreeModelHasPeople>
      </people>
    </familyTreeModel>
    ```

-   Définissez **représentation** = **élément** pour avoir une propriété de domaine enregistrée en tant qu’élément et non comme valeur d’attribut.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

-   Pour modifier l’ordre dans lequel les attributs et les relations sont sérialisées, cliquez sur un élément sous l’élément de données et utiliser le **monter** ou **Descendre** commandes de menu.

## <a name="major-customization-using-program-code"></a>Personnalisation principales à l’aide de code de programme

Vous pouvez remplacer la partie ou l’ensemble des algorithmes de sérialisation.

Nous vous recommandons de temps d’étudier le code dans **Dsl\Generated Code\Serializer.cs** et **SerializationHelper.cs**.

### <a name="to-customize-the-serialization-of-a-particular-class"></a>Pour personnaliser la sérialisation d’une classe particulière

1.  Définissez **personnalisé est** dans le nœud pour cette classe sous **comportement de sérialisation Xml**.

2.  Transformer tous les modèles, générez la solution et examinez les erreurs de compilation qui en résulte. Commentaires près de chaque erreur expliquent le code que vous devez fournir.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Pour fournir votre propre sérialisation pour l’ensemble du modèle

1.  Substituer des méthodes dans Dsl\GeneratedCode\SerializationHelper.cs

## <a name="options-in-xml-serialization-behavior"></a>Options de comportement de sérialisation Xml

Dans l’Explorateur DSL, le nœud de comportement de sérialisation Xml contient un nœud enfant pour chaque classe de domaine, relation, forme, connecteur et de classe de diagramme. Sous chacune de ces nœuds est une liste de propriétés et relations provenance de cet élément. Les relations sont représentées à la fois dans leur propre droit et sous leurs classes de source.

Le tableau suivant résume les options que vous pouvez définir dans cette section de la définition DSL. Dans chaque cas, sélectionnez un élément dans l’Explorateur DSL et définir les options dans la fenêtre Propriétés.

### <a name="xml-class-data"></a>Données XML (classe)

Ces éléments sont trouvent dans l’Explorateur DSL sous **Behavior\Class données de la sérialisation Xml**.

|||
|-|-|
|Propriété|Description|
|A le schéma d’élément personnalisé|Si la valeur est True, indique que la classe de domaine a un schéma d’élément personnalisé|
|Est personnalisé|Affectez la valeur **True** si vous souhaitez écrire votre propre code de sérialisation et désérialisation pour cette classe de domaine.<br /><br /> Générez la solution et examinez les erreurs pour découvrir des instructions détaillées.|
|Classe de domaine|Classe de domaine à laquelle s’applique ce nœud de données de classe. Lecture seule.|
|Nom de l'élément|Nom du nœud XML pour les éléments de cette classe. La valeur par défaut est une version en minuscules du nom de classe de domaine.|
|Nom d’attribut moniker|Nom de l’attribut utilisé dans les éléments moniker pour contenir la référence. S’il est vierge, le nom de la propriété de clé ou un id est utilisé.<br /><br /> Dans cet exemple, il est « name » :  `<personMoniker name="/Mike Nash"/>`|
|Nom d’élément moniker|Nom de l’élément xml utilisé pour les monikers qui font référence aux éléments de cette classe.<br /><br /> La valeur par défaut est une version en minuscules du nom de classe, suivi du suffixe « Moniker ». Par exemple, `personMoniker`.|
|Nom de Type de moniker|Nom du type xsd généré pour les monikers aux éléments de cette classe. Le schéma XSD est dans **Dsl\Generated Code\\\*Schema.xsd**|
|Sérialiser des Id|Si la valeur est True, le GUID de l’élément est inclus dans le fichier. Cela doit être true s’il n’existe aucune propriété qui est marquée **est la clé de Moniker** et la solution DSL définit les relations de référence à cette classe.|
|Nom de type|Nom du type xml généré dans le xsd à partir de la classe de domaine désigné.|
|Notes|Notes informelles associées à cet élément|

### <a name="xml-property-data"></a>Données de propriété XML

Nœuds de la propriété XML sont trouvent sous les nœuds de la classe.

|||
|-|-|
|Propriété|Description|
|Propriété de domaine|Propriété à laquelle les données de configuration de sérialisation xml s’applique. Lecture seule.|
|Est la clé de Moniker|Si la valeur est True, la propriété est utilisée comme clé pour la création de monikers qui référencent des instances de cette classe de domaine.|
|Qualificateur du Moniker|Si la valeur est True, la propriété est utilisée pour créer le qualificateur dans les monikers. Si la valeur false et si SerializeId n’est pas vrai pour cette classe de domaine, les monikers sont qualifiés par le moniker de l’élément parent dans l’arborescence d’incorporation.|
|Représentation sous forme de|Si l’attribut, la propriété est sérialisée comme un attribut xml ; Si l’élément, il est sérialisé en tant qu’élément ; Si Ignore, elle n’est pas sérialisé.|
|Nom XML|Nom utilisé pour l’élément qui représente la propriété ou un attribut xml. Par défaut, il s’agit d’une version en minuscules du nom de propriété de domaine.|
|Notes|Notes informelles associées à cet élément|

### <a name="xml-role-data"></a>Données de rôle de XML

Les nœuds de données de rôle sont trouvent sous les nœuds de la classe source.

|Propriété|Description|
|-|-|
|A Moniker personnalisé|Définissez cette propriété sur true si vous souhaitez fournir votre propre code pour la génération et la résolution des monikers qui passent par cette relation.<br /><br /> Pour obtenir des instructions détaillées, générez la solution, puis double-cliquez sur les messages d’erreur.|
|Relation de domaine|Spécifie la relation à laquelle ces options s’appliquent. Lecture seule.|
|Omettre l’élément|Si la valeur est true, le nœud XML qui correspond au rôle source est omis à partir du schéma.<br /><br /> S’il existe plusieurs relations entre les classes source et cible, ce nœud de rôle fait la distinction entre les liens qui appartiennent aux deux relations. Par conséquent, nous recommandons que vous ne définissez pas cette option dans ce cas.|
|Nom d’élément de rôle|Spécifie le nom de l’élément XML qui est dérivé du rôle source. La valeur par défaut est le nom de propriété de rôle.|
|Plein écran|Si la valeur est true, chaque élément de la cible ou le moniker est placé dans un nœud XML représentant la relation. Cela doit être défini sur true si la relation a ses propres propriétés de domaine.|

## <a name="see-also"></a>Voir aussi

- [Navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Génération de code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md)