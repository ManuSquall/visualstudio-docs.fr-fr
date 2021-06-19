---
title: Personnalisation du stockage de fichiers et de la sérialisation XML
description: En savoir plus sur le fichier XML créé ou mis à jour lorsque vous enregistrez une instance, ou un modèle, d’un langage spécifique à un domaine (DSL) dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.xmlbehavior
helpviewer_keywords:
- Domain-Specific Language, serialization
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: be19b3026010e37108ca1b19096d48a3c8d88ab6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389369"
---
# <a name="customize-file-storage-and-xml-serialization"></a>Personnaliser le stockage de fichiers et la sérialisation XML

Quand l’utilisateur enregistre une instance, ou un *modèle*, d’un langage spécifique à un domaine (DSL) dans Visual Studio, un fichier XML est créé ou mis à jour. Le fichier peut être rechargé pour recréer le modèle dans le magasin.

Vous pouvez personnaliser le schéma de sérialisation en ajustant les paramètres sous **comportement de sérialisation XML** dans l’Explorateur DSL. Il existe un nœud sous le **comportement de sérialisation XML** pour chaque classe de domaine, propriété et relation. Les relations sont situées sous leurs classes sources. Il y a également des nœuds correspondant aux classes de formes, de connecteurs et de diagrammes.

Vous pouvez également écrire du code de programme pour une personnalisation plus avancée.

> [!NOTE]
> Si vous souhaitez enregistrer le modèle dans un format particulier, mais que vous n’avez pas besoin de le recharger à partir de ce formulaire, envisagez d’utiliser des modèles de texte pour générer la sortie à partir du modèle, au lieu d’un schéma de sérialisation personnalisé. Pour plus d’informations, consultez [génération de code à partir d’un langage de Domain-Specific](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="model-and-diagram-files"></a>Fichiers de modèle et de diagramme

Chaque modèle est généralement enregistré dans deux fichiers :

- Le fichier de modèle a un nom tel que **Model1. MyDSL**. Elle stocke les éléments de modèle et les relations, ainsi que leurs propriétés. L’extension de fichier telle que **. MyDSL** est déterminée par la propriété **FileExtension** du nœud de l' **éditeur** dans la définition DSL.

- Le fichier de diagramme a un nom tel que **Model1. MyDSL. Diagram**. Elle stocke les formes, les connecteurs et leurs positions, couleurs, épaisseurs de trait et d’autres détails sur l’apparence du diagramme. Si l’utilisateur supprime un fichier **. Diagram** , les informations essentielles dans le modèle ne sont pas perdues. Seule la disposition du diagramme est perdue. Une fois le fichier de modèle ouvert, un ensemble de formes et de connecteurs par défaut est créé.

### <a name="to-change-the-file-extension-of-a-dsl"></a>Pour modifier l’extension de fichier d’un DSL

1. Ouvrez la définition DSL. Dans l’Explorateur DSL, cliquez sur le nœud Éditeur.

2. Dans la Fenêtre Propriétés, modifiez la propriété **FileExtension** . N’incluez pas le « . » initial de l’extension de nom de fichier.

3. Dans Explorateur de solutions, modifiez le nom des deux fichiers de modèle d’élément dans **DslPackage\ProjectItemTemplates**. Les noms de ces fichiers respectent le format suivant :

     `myDsl.diagram`

     `myDsl.myDsl`

## <a name="the-default-serialization-scheme"></a>Schéma de sérialisation par défaut

Pour créer un exemple pour cette rubrique, la définition DSL suivante a été utilisée.

![Diagramme de définition DSL &#45; modèle d’arbre généalogique](../modeling/media/familyt_person.png)

Ce DSL a été utilisé pour créer un modèle qui a l’apparence suivante à l’écran.

![Diagramme d'arbre généalogique, boîte à outils et explorateur](../modeling/media/familyt_instance.png)

Ce modèle a été enregistré puis rouvert dans l’éditeur de texte XML :

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

Notez les points suivants sur le modèle sérialisé :

- Chaque nœud XML a un nom qui est identique à un nom de classe de domaine, sauf que la lettre initiale est en minuscules. Par exemple, `familyTreeModel` et `person`.

- Les propriétés de domaine, telles que Name et Annéenaissance, sont sérialisées en tant qu’attributs dans les nœuds XML. Là encore, le premier caractère du nom de la propriété est converti en minuscules.

- Chaque relation est sérialisée sous la forme d’un nœud XML imbriqué à l’intérieur de la terminaison source de la relation. Le nœud porte le même nom que la propriété du rôle source, mais avec un caractère initial en minuscules.

     Par exemple, dans la définition DSL, un rôle nommé **People** est issu de la classe **FamilyTree** .  Dans le XML, il est représenté par le nœud appelé `people` imbriqué dans le `familyTreeModel` nœud.

- La terminaison cible de chaque relation d’incorporation est sérialisée comme un nœud imbriqué sous la relation. Par exemple, le `people` nœud contient plusieurs `person` nœuds.

- La terminaison cible de chaque relation de référence est sérialisée comme *moniker*, qui encode une référence à l’élément cible.

     Par exemple, sous un `person` nœud, il peut y avoir une `children` relation. Ce nœud contient des monikers tels que :

    ```xml
    <personMoniker name="/f817b728-e920-458e-bb99-98edc469d78f/Elizabeth I" />
    ```

## <a name="understand-monikers"></a>Comprendre les monikers

Les monikers sont utilisés pour représenter des références croisées entre les différentes parties des fichiers de modèle et de diagramme. Ils sont également utilisés dans le `.diagram` fichier pour faire référence aux nœuds dans le fichier de modèle. Il existe deux formes de moniker :

- Les *monikers d’ID* guillemets du GUID de l’élément cible. Exemple :

    ```xml
    <personShapeMoniker Id="f79734c0-3da1-4d72-9514-848fa9e75157" />
    ```

- Les *monikers de clé qualifiée* identifient l’élément cible par la valeur d’une propriété de domaine désignée appelée clé de moniker. Le moniker de l’élément cible est préfixé par le moniker de son élément parent dans l’arborescence des relations d’incorporation.

     Les exemples suivants proviennent d’un DSL dans lequel il existe une classe de domaine nommée album, qui a une relation d’incorporation avec une classe de domaine nommée Song :

    ```xml
    <albumMoniker title="/My Favorites/Jazz after Teatime" />
    <songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
    ```

     Les monikers de clé qualifiée seront utilisés si la classe cible a une propriété de domaine pour laquelle l’option **est la clé de moniker** est définie sur `true` dans le **comportement de sérialisation XML**. Dans l’exemple, cette option est définie pour les propriétés de domaine nommées « Title » dans les classes de domaine « album » et « chanson ».

Les monikers de clé qualifiés sont plus faciles à lire que les monikers d’ID. Si vous envisagez de lire le code XML de vos fichiers de modèle par des personnes, envisagez d’utiliser des monikers de clé qualifiés. Toutefois, il est possible pour l’utilisateur de définir plusieurs éléments pour qu’ils aient la même clé de moniker. Des clés dupliquées peuvent empêcher le rechargement correct du fichier. Par conséquent, si vous définissez une classe de domaine qui est référencée à l’aide de monikers de clé qualifiés, vous devez prendre en compte les moyens d’empêcher l’utilisateur d’enregistrer un fichier qui a des monikers en double.

### <a name="to-set-a-domain-class-to-be-referenced-by-id-monikers"></a>Pour définir une classe de domaine à référencer par des monikers d’ID

1. Assurez-vous que la **clé de moniker** est `false` pour chaque propriété de domaine dans la classe et ses classes de base.

    1. Dans l’Explorateur DSL, développez **sérialisation XML données Behavior\Class données \\ \<the domain class> \Element**.

    2. Vérifiez que la **clé de moniker** est `false` pour chaque propriété de domaine.

    3. Si la classe de domaine a une classe de base, répétez la procédure dans cette classe.

2. Définissez   =  `true` l’ID de sérialisation de la classe de domaine.

     Cette propriété se trouve sous **comportement de sérialisation XML**.

### <a name="to-set-a-domain-class-to-be-referenced-by-qualified-key-monikers"></a>Pour définir une classe de domaine à référencer par des monikers de clé qualifiés

- Set **est une clé de moniker** pour une propriété de domaine d’une classe de domaine existante. Le type de la propriété doit être `string` .

    1. Dans l’Explorateur DSL, développez **sérialisation XML Behavior\Class données \\ \<the domain class> \Element données**, puis sélectionnez la propriété de domaine.

    2. Dans la Fenêtre Propriétés, définissez la **clé de moniker** sur `true` .

- \- ou -

     Créez une classe de domaine à l’aide de l’outil de **classe de domaine nommé** .

     Cet outil crée une classe qui a une propriété de domaine nommée Name. Le **est le nom d’élément** et les propriétés de **clé de moniker** de cette propriété de domaine sont initialisées à `true` .

- \- ou -

     Créez une relation d’héritage de la classe de domaine vers une autre classe qui a une propriété de clé de moniker.

### <a name="avoid-duplicate-monikers"></a>Éviter les monikers en double

Si vous utilisez des monikers de clé qualifiés, il est possible que deux éléments dans le modèle d’un utilisateur aient la même valeur dans la propriété de clé. Par exemple, si votre DSL a une personne de classe qui a un nom de propriété, l’utilisateur peut définir les noms de deux éléments de la même façon. Bien que le modèle puisse être enregistré dans un fichier, il ne se recharge pas correctement.

Il existe plusieurs méthodes qui permettent d’éviter cette situation :

- Set **est**  =  `true` le nom d’élément de la propriété de domaine Key. Sélectionnez la propriété de domaine dans le diagramme de définition DSL, puis définissez la valeur dans la Fenêtre Propriétés.

     Lorsque l’utilisateur crée une nouvelle instance de la classe, cette valeur entraîne l’attribution automatique d’une valeur différente à la propriété de domaine. Le comportement par défaut ajoute un nombre à la fin du nom de la classe. Cela n’empêche pas l’utilisateur de changer le nom en un doublon, mais il aide dans le cas où l’utilisateur ne définit pas la valeur avant d’enregistrer le modèle.

- Activez la validation pour le DSL. Dans l’Explorateur DSL, sélectionnez Editor\Validation et définissez les propriétés **uses...** sur `true` .

     Il existe une méthode de validation générée automatiquement qui vérifie les ambiguïtés. La méthode figure dans la `Load` catégorie validation. Cela permet de s’assurer que l’utilisateur est averti qu’il n’est pas possible de rouvrir le fichier.

     Pour plus d’informations, consultez [validation dans un langage de Domain-Specific](../modeling/validation-in-a-domain-specific-language.md).

### <a name="moniker-paths-and-qualifiers"></a>Chemins d’accès et qualificateurs de moniker

Un moniker de clé qualifié se termine par la clé de moniker et est préfixé avec le moniker de son parent dans l’arborescence d’incorporation. Par exemple, si le moniker d’un album est :

```xml
<albumMoniker title="/My Favorites/Jazz after Teatime" />
```

L’une des chansons de cet album peut être :

```xml
<songMoniker title="/My Favorites/Jazz after Teatime/Hot tea" />
```

Toutefois, si les albums sont référencés par un ID à la place, les monikers se présentent comme suit :

```xml
<albumMoniker Id="77472c3a-9bf9-4085-976a-d97a4745237c" />
<songMoniker title="/77472c3a-9bf9-4085-976a-d97a4745237c/Hot tea" />
```

Notez qu’étant donné qu’un GUID est unique, il n’est jamais préfixé par le moniker de son parent.

Si vous savez qu’une propriété de domaine particulière aura toujours une valeur unique dans un modèle, vous pouvez définir le **qualificateur de moniker** à `true` pour cette propriété. Cela entraînera son utilisation en tant que qualificateur, sans utiliser le moniker du parent. Par exemple, si vous définissez à la fois le **qualificateur de moniker** et la **clé de moniker** pour la propriété de domaine title de la classe album, le nom ou l’identificateur du modèle n’est pas utilisé dans les monikers pour l’album et ses enfants incorporés :

```xml
<albumMoniker name="Jazz after Teatime" />
<songMoniker title="/Jazz after Teatime/Hot tea" />
```

## <a name="customize-the-structure-of-the-xml"></a>Personnaliser la structure du code XML

Pour effectuer les personnalisations suivantes, développez le nœud **comportement de sérialisation XML** dans l’Explorateur DSL. Sous une classe de domaine, développez le nœud données d’élément pour afficher la liste des propriétés et des relations qui sont issues de cette classe. Sélectionnez une relation et ajustez ses options dans le Fenêtre Propriétés.

- Affectez la valeur true à l' **élément omit** pour omettre le nœud du rôle source, en laissant uniquement la liste des éléments cibles. Vous ne devez pas définir cette option s’il existe plusieurs relations entre les classes source et cible.

    ```xml
    <familyTreeModel ...>
      <!-- The following node is omitted by using Omit Element: -->
      <!-- <people> -->
        <person name="Henry VIII" .../>
        <person name="Elizabeth I" .../>
      <!-- </people> -->
    </familyTreeModel>
    ```

- Définissez **utiliser le formulaire complet** pour incorporer les nœuds cibles dans les nœuds représentant les instances de relation. Cette option est définie automatiquement lorsque vous ajoutez des propriétés de domaine à une relation de domaine.

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

- Définissez   =  l'**élément** de représentation pour qu’une propriété de domaine soit enregistrée en tant qu’élément et non en tant que valeur d’attribut.

    ```xml
    <person name="Elizabeth I" birthYear="1533">
      <deathYear>1603</deathYear>
    </person>
    ```

- Pour modifier l’ordre dans lequel les attributs et les relations sont sérialisés, cliquez avec le bouton droit sur un élément sous données d’élément, puis utilisez les commandes du menu **monter** ou **descendre** .

## <a name="major-customization-using-program-code"></a>Personnalisation importante à l’aide de code de programme

Vous pouvez remplacer des parties ou l’ensemble des algorithmes de sérialisation.

Nous vous recommandons d’étudier le code dans **Dsl\Generated Code\Serializer.cs** et **SerializationHelper. cs**.

### <a name="to-customize-the-serialization-of-a-particular-class"></a>Pour personnaliser la sérialisation d’une classe particulière

1. Set **est personnalisé** dans le nœud de cette classe sous le **comportement de sérialisation XML**.

2. Transformez tous les modèles, générez la solution et examinez les erreurs de compilation qui en résultent. Les commentaires situés près de chaque erreur expliquent quel code vous devez fournir.

### <a name="to-provide-your-own-serialization-for-the-whole-model"></a>Pour fournir votre propre sérialisation pour l’ensemble du modèle

1. Substituer les méthodes dans Dsl\GeneratedCode\SerializationHelper.cs

## <a name="options-in-xml-serialization-behavior"></a>Options de comportement de sérialisation XML

Dans l’Explorateur DSL, le nœud comportement de sérialisation XML contient un nœud enfant pour chaque classe de domaine, relation, forme, connecteur et classe de diagramme. Sous chacun de ces nœuds se trouve une liste de propriétés et de relations source au niveau de cet élément. Les relations sont représentées à la fois dans leur propre droit et sous leurs classes sources.

Le tableau suivant récapitule les options que vous pouvez définir dans cette section de la définition DSL. Dans chaque cas, sélectionnez un élément dans l’Explorateur DSL et définissez les options dans l’Fenêtre Propriétés.

### <a name="xml-class-data"></a>Données de classe XML

Ces éléments se trouvent dans l’Explorateur DSL sous **sérialisation XML Behavior\Class données**.

|Propriété|Description|
|-|-|
|A un schéma d’élément personnalisé|Si la valeur est true, indique que la classe de domaine a un schéma d’élément personnalisé|
|Est personnalisé|Affectez la valeur **true** si vous souhaitez écrire votre propre code de sérialisation et de désérialisation pour cette classe de domaine.<br /><br /> Générez la solution et examinez les erreurs pour découvrir des instructions détaillées.|
|Classe de domaine|Classe de domaine à laquelle ce nœud de données de classe s’applique. Lecture seule.|
|Nom de l’élément|Nom de nœud XML pour les éléments de cette classe. La valeur par défaut est une version en minuscules du nom de classe de domaine.|
|Nom d’attribut de moniker|Nom de l’attribut utilisé dans les éléments moniker pour contenir la référence. Si vide, le nom de la propriété ou l'identificateur de clé est utilisé.<br /><br /> Dans cet exemple, il s’agit de « Name » :  `<personMoniker name="/Mike Nash"/>`|
|Nom de l’élément moniker|Nom de l’élément XML utilisé pour les monikers qui font référence aux éléments de cette classe.<br /><br /> La valeur par défaut est une version en minuscules du nom de classe avec le suffixe « moniker ». Par exemple : `personMoniker`.|
|Nom de type de moniker|Nom du type XSD généré pour les monikers aux éléments de cette classe. Le schéma XSD se trouve dans **Dsl\Generated code \\ \* Schema. xsd**|
|ID de sérialisation|Si la valeur est true, le GUID de l’élément est inclus dans le fichier. Cela doit avoir la valeur true s’il n’y a aucune propriété marquée comme **clé de moniker** et que la DSL définit des relations de référence à cette classe.|
|Nom de type|Nom du type XML généré dans XSD à partir de la classe de domaine indiquée.|
|Notes|Notes informelles associées à cet élément|

### <a name="xml-property-data"></a>Données de propriété XML

Les nœuds de propriété XML se trouvent sous les nœuds de classe.

|Propriété|Description|
|-|-|
|Propriété de domaine|Propriété à laquelle les données de configuration de sérialisation XML s'appliquent. Lecture seule.|
|Est une clé de moniker|Si la valeur est true, la propriété est utilisée comme clé pour créer des monikers qui référencent des instances de cette classe de domaine.|
|Qualificateur de moniker|Si la valeur est True, la propriété est utilisée pour créer le qualificateur dans les monikers. Si la valeur est false et si SerializeId n’a pas la valeur true pour cette classe de domaine, les monikers sont qualifiés par le moniker de l’élément parent dans l’arborescence d’incorporation.|
|Représentation|Si Attribute, la propriété est sérialisée en tant qu'attribut XML ; si Element, elle est sérialisée en tant qu'élément ; si Ignore, elle n'est pas sérialisée.|
|Nom XML|Nom utilisé pour l'attribut ou l'élément XML représentant la propriété. Par défaut, il s’agit d’une version en minuscules du nom de la propriété de domaine.|
|Notes|Notes informelles associées à cet élément|

### <a name="xml-role-data"></a>Données de rôle XML

Les nœuds de données de rôle se trouvent sous les nœuds de la classe source.

|Propriété|Description|
|-|-|
|A un moniker personnalisé|Affectez la valeur true si vous souhaitez fournir votre propre code pour générer et résoudre les monikers qui parcourent cette relation.<br /><br /> Pour obtenir des instructions détaillées, générez la solution, puis double-cliquez sur les messages d’erreur.|
|Relation de domaine|Spécifie la relation à laquelle ces options s’appliquent. Lecture seule.|
|Omit, élément|Si la valeur est true, le nœud XML qui correspond au rôle source est omis du schéma.<br /><br /> S’il existe plusieurs relations entre les classes source et cible, ce nœud de rôle fait la distinction entre les liens qui appartiennent aux deux relations. Nous vous recommandons donc de ne pas définir cette option dans ce cas.|
|Nom de l’élément de rôle|Spécifie le nom de l’élément XML dérivé du rôle source. La valeur par défaut est le nom de la propriété de rôle.|
|Utiliser la forme complète|Si la valeur est true, chaque élément ou moniker cible est placé dans un nœud XML représentant la relation. Elle doit avoir la valeur true si la relation a ses propres propriétés de domaine.|

## <a name="see-also"></a>Voir aussi

- [Navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Génération de code à partir d’un langage spécifique à un domaine](../modeling/generating-code-from-a-domain-specific-language.md)
