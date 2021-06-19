---
title: Le fichier DslDefinition.dsl
description: En savoir plus sur la structure du fichier DslDefinition. DSL dans le projet DSL d’une solution d’outils DSL, qui définit un langage spécifique à un domaine.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3f2e2ae6e406b8967cb7de49573ce5b26377806e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388631"
---
# <a name="the-dsldefinitiondsl-file"></a>Le fichier DslDefinition.dsl

Cette rubrique décrit la structure du fichier DslDefinition. DSL dans le projet DSL d’une [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] solution, qui définit un *langage spécifique à un domaine*. Le fichier DslDefinition. DSL décrit les classes et les relations d’un langage spécifique à un domaine, ainsi que le diagramme, les formes, les connecteurs, le format de sérialisation et la **boîte à outils** du langage spécifique à un domaine et ses outils d’édition. Dans une solution de langage spécifique à un domaine, le code qui définit ces outils est généré en fonction des informations contenues dans le fichier DslDefinition.dsl.

En règle générale, vous utilisez la *Concepteur Domain-specific language* pour modifier le fichier DslDefinition. DSL. Toutefois, il s'agit dans sa forme brute d'un fichier XML et vous pouvez ouvrir un fichier DslDefinition.dsl dans un éditeur XML. Il peut être utile de bien comprendre les informations contenues dans le fichier et comment elles sont organisées à des fins de débogage et d'extension.

Les exemples dans cette rubrique sont tirés du modèle de solution Diagramme de composant. Pour afficher un exemple, créez une solution de langage spécifique à un domaine basée sur le modèle de solution Modèles de composants. Une fois que vous avez créé la solution, le fichier DslDefinition.dsl apparaît dans le concepteur de langage spécifique à un domaine. Fermez le fichier, cliquez dessus avec le bouton droit dans **Explorateur de solutions**, pointez sur **Ouvrir avec**, cliquez sur **éditeur XML**, puis cliquez sur **OK**.

## <a name="sections-of-the-dsldefinitiondsl-file"></a>Sections du fichier DslDefinition.dsl

L’élément racine est \<Dsl> , et ses attributs identifient le nom du langage spécifique à un domaine, l’espace de noms et les numéros de version majeure et mineure pour le contrôle de version. Le schéma `DslDefinitionModel` définit le contenu et la structure d'un fichier DslDefinition.dsl valide.

Les éléments enfants de l' \<Dsl> élément racine sont les suivants :

### <a name="classes"></a>Classes

Cette section définit chaque classe de domaine qui génère une classe dans le code généré.

### <a name="relationships"></a>Relations

Cette section définit chaque relation dans le modèle. La source et la cible représentent les deux côtés d'une relation.

### <a name="types"></a>Types

Cette section définit chaque type et son espace de noms. Il existe deux types de propriétés de domaine. `DomainEnumerations` sont définis dans le modèle et génèrent des types dans DomainModel. cs. `ExternalTypes` reportez-vous aux types définis ailleurs (tels que `String` ou `Int32` ) et ne générez pas d’éléments.

### <a name="shapes"></a>Formes

Cette section définit les formes qui décrivent comment le modèle apparaît dans un concepteur. Ces formes géométriques sont mappées aux classes dans le modèle, dans la section Diagram.

### <a name="connectors"></a>Connecteurs

Cette section définit l'apparence des connecteurs qui apparaissent dans un concepteur. Ces descriptions de styles géométriques sont mappées à des relations spécifiques dans le modèle, dans la section Diagram.

### <a name="xmlserializationbehavior"></a>XmlSerializationBehavior

Cette section définit un schéma de sérialisation et fournit des informations supplémentaires sur la manière dont chaque classe est enregistrée dans un fichier.

### <a name="explorerbehavior"></a>ExplorerBehavior

Cette section définit la manière dont la fenêtre de l' **Explorateur DSL** s’affiche lorsque l’utilisateur modifie un modèle.

### <a name="connectionbuilders"></a>ConnectionBuilders

Cette section définit un générateur de connexion pour chaque outil connecteur (l'outil de création de liens entre deux classes qui peuvent être connectées). Cette section détermine si vous pouvez connecter une classe source et une classe cible.

### <a name="diagram"></a>Diagramme

Cette section définit un diagramme et vous l'utilisez pour spécifier des propriétés telles que la couleur d'arrière-plan et la classe racine. (La classe racine est la classe de domaine qui est représentée par le diagramme dans son ensemble.) La section Diagram contient également des éléments ShapeMap et ConnectorMap, qui spécifient la forme ou le connecteur représentant chaque classe ou relation de domaine.

### <a name="designer"></a>Designer

Cette section définit un concepteur (éditeur), qui regroupe une **boîte à outils**, des paramètres de validation, un diagramme et un schéma de sérialisation. La section Designer définit également la classe racine du modèle, qui est généralement aussi la classe racine du diagramme.

### <a name="explorer"></a>Explorer

Cette section identifie le comportement de l' **Explorateur DSL** (défini dans la section XmlSerializationBehavior).

## <a name="monikers-in-the-dsldefinitiondsl-file"></a>Monikers dans le fichier DslDefinition.dsl

Dans le fichier DslDefinition.dsl, vous pouvez utiliser des monikers pour créer des références croisées à des éléments spécifiques. Par exemple, chaque définition Relationship contient une sous-section Source et une sous-section Target. Chaque sous-section contient le moniker de la classe d'objet qui peut être lié avec cette relation :

```xml
<DomainRelationship ...        Name="LibraryHasMembers" Namespace="ExampleNamespace" >    <Source>      <DomainRole ...>
       <RolePlayer>
         <DomainClassMoniker Name="Library" />
       </RolePlayer>
     </DomainRole>
   </Source>
```

En général, l'espace de noms de l'élément référencé (dans cet exemple, la classe de domaine `Library`) est identique à l'élément de référencement (dans ce cas, la relation de domaine LibraryHasMembers). Dans ces cas-là, le moniker doit donner uniquement le nom de la classe. Sinon, vous utiliseriez la forme complète /Espace_De_Noms/Nom :

```xml
<DomainClassMoniker Name="/ExampleNameSpace/Library" />
```

Le système moniker exige que les enfants dans l'arborescence XML aient des noms distincts. Pour cette raison, des erreurs de validation se produisent si vous essayez d'enregistrer une définition de langage spécifique à un domaine ayant, par exemple, deux classes du même nom. Vous devez toujours corriger ces erreurs de doublons avant d'enregistrer le fichier DslDefinition.dsl pour pouvoir le recharger ultérieurement.

Chaque type à son propre type de moniker : DomainClassMoniker, DomainRelationshipMoniker, et ainsi de suite.

## <a name="types"></a>Types

La section Types spécifie tous les types contenus dans le fichier DslDefinition.dsl comme types de propriétés. Ces types appartiennent à deux catégories : les types externes, tels que System.String, et les types énumérés.

### <a name="external-types"></a>Types externes

L'exemple Diagramme de composant énumère un ensemble des types primitifs standard, bien que seulement une partie d'entre eux soient utilisés.

Chaque définition de type externe est constituée seulement d'un nom et d'un espace de noms, tels que String et System :

```xml
<ExternalType Name="String" Namespace="System" />
```

Les noms complets des types sont utilisés, au lieu des mots clés de compilateur équivalents tels que « string ».

Les types externes ne sont pas limités aux types de bibliothèques standard.

### <a name="enumerations"></a>Énumérations

Une spécification d'énumération par défaut ressemble à l'exemple suivant :

```xml
<DomainEnumeration IsFlags="true" Name="PageSort"          Namespace="Fabrikam.Wizard">
  <Literals>
    <EnumerationLiteral Name="Start" Value="1"/>
    <EnumerationLiteral Name="Decision" Value="2"/>
  </Literals>
</DomainEnumeration>
```

L'attribut `IsFlags` détermine si le code généré est préfixé de l'attribut CLR (Common Language Runtime) `[Flags]`, qui détermine si les valeurs de l'énumération peuvent être combinées au niveau du bit. Si cet attribut à la valeur True, vous devez spécifier des valeurs égales à une puissance de deux pour les valeurs littérales.

## <a name="classes"></a>Classes

La plupart des éléments d'une définition d'un langage spécifique à un domaine sont des instances directes ou indirectes de `DomainClass`. Parmi les sous-classes de `DomainClass` figurent `DomainRelationship`, `Shape`, `Connector` et `Diagram`. La section `Classes` du fichier DslDefinition.dsl répertorie les classes de domaine.

Chaque classe a un ensemble de propriétés et peut avoir une classe de base. Dans l'exemple Diagramme de composant, `NamedElement` est une classe abstraite ayant une propriété `Name` de type String :

```xml
<DomainClass Id="ee3161ca-2818-42c8-b522-88f50fc72de8"  Name="NamedElement" Namespace="Fabrikam.CmptDsl5"      DisplayName="Named Element"  InheritanceModifier="Abstract">
  <Properties>
    <DomainProperty Id="ef553cf0-33b5-4e34-a30b-cfcfd86f2261"   Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
      <Type>
        <ExternalTypeMoniker Name="/System/String" />
      </Type>
    </DomainProperty>
  </Properties>
</DomainClass>
```

`NamedElement` est la base de plusieurs des autres classes telles que `Component` , qui possède ses propres propriétés en plus de la `Name` propriété, qu’elle a héritée de `NamedElement` . Le nœud enfant BaseClass contient une référence de moniker. La classe référencée étant dans le même espace de noms, seul son nom est nécessaire dans le moniker :

```xml
<DomainClass Name="Component" Namespace="Fabrikam.CmptDsl5"              DisplayName="Component">
  <BaseClass>
    <DomainClassMoniker Name="NamedElement" />
  </BaseClass>
  <Properties>
    <DomainProperty Name="Kind" DisplayName="Kind" >
      <Type>
        <ExternalTypeMoniker Name="/System/String" />
      </Type>
    </DomainProperty>
  </Properties>
```

Chaque classe de domaine (y compris les relations, les formes, les connecteurs et les diagrammes) peut avoir les attributs et nœuds enfants suivants :

- **ID.** Cet attribut est un GUID. Si vous ne spécifiez pas de valeur dans le fichier, le concepteur de langage spécifique à un domaine crée une valeur. (Dans les illustrations de ce document, cet attribut est généralement omis pour des raisons d'espace.)

- **Name et Namespace.**  Ces attributs spécifient le nom et l'espace de noms de la classe dans le code généré. Ensemble, ils doivent être uniques dans le langage spécifique à un domaine.

- **InheritanceModifier.** Cet attribut est « abstract », « sealed » ou aucun.

- **NomComplet.** Cet attribut est le nom qui apparaît dans la fenêtre **Propriétés** . L'attribut DisplayName peut contenir des espaces et autres signes de ponctuation.

- **GeneratesDoubleDerived.**  Si cet attribut à la valeur True, deux classes sont générées et l'une d'elles est une sous-classe de l'autre. Toutes les méthodes générées sont dans la base et les constructeurs sont dans la sous-classe. En définissant cet attribut, vous pouvez substituer toute méthode générée dans le code personnalisé.

- **HasCustomConstructor**. Si cet attribut à la valeur True, le constructeur est omis du code généré pour que vous puissiez écrire votre propre version.

- **Attributs**. Cet attribut contient les attributs CLR de la classe générée.

- **BaseClass**. Si vous spécifiez une classe de base, elle doit être du même type. Par exemple, une classe de domaine doit avoir une autre classe de domaine comme base et une forme de compartiment doit avoir une forme de compartiment. Si vous ne spécifiez pas de classe de base, la classe dans le code généré dérive d'une classe d'infrastructure standard. Par exemple, une classe de domaine dérive de `ModelElement`.

- **Propriétés**. Cet attribut contient les propriétés qui sont tenues à jour sous le contrôle de transaction et conservées lors de l'enregistrement du modèle.

- **ElementMergeDirectives**. Chaque directive de fusion d'élément contrôle comment une instance différente d'une autre classe est ajoutée à une instance de la classe parente. Vous trouverez des détails supplémentaires sur les directives de fusion d'élément plus loin dans cette rubrique.

- Une classe C# est générée pour chaque classe de domaine qui est répertoriée dans la section `Classes`. Les classes C# sont générées dans Dsl\GeneratedCode\DomainClasses.cs.

### <a name="properties"></a>Propriétés

Chaque propriété de domaine a un nom et un type. Le nom doit être unique dans la classe de domaine et ses bases transitives.

Le type doit faire référence à l'un de ceux répertoriés dans la section `Types`. En général, le moniker doit inclure l'espace de noms.

```xml
<DomainProperty Name="Name" DisplayName="Name"  DefaultValue="" Category="" IsElementName="true">
  <Type>
    <ExternalTypeMoniker Name="/System/String" />
  </Type>
</DomainProperty>
```

Chaque propriété de domaine peut aussi avoir les attributs suivants :

- **IsBrowsable**. Cet attribut détermine si la propriété s’affiche dans la fenêtre **Propriétés** quand l’utilisateur clique sur un objet de la classe parente.

- **IsUIReadOnly**. Cet attribut détermine si l’utilisateur peut modifier la propriété dans la fenêtre **Propriétés** ou par le biais d’un élément décoratif dans lequel la propriété est présentée.

- **Genre**. Vous pouvez affecter à cet attribut la valeur Normal, Calculated ou CustomStorage. Si vous lui affectez la valeur Calculated, vous devez fournir du code personnalisé qui détermine la valeur et la propriété sera en lecture seule. Si vous lui affectez la valeur CustomStorage, vous devez fournir du code qui obtient et définit des valeurs.

- **IsElementName**. Si cet attribut à la valeur True, sa valeur est définie automatiquement sur une valeur unique quand une instance de la classe parente est créée. Cet attribut peut prendre la valeur True pour une seule propriété dans chaque classe, qui doit être de type String. Dans l'exemple Diagramme de composant, la propriété `Name` dans `NamedElement` a `IsElementName` définie sur True. Chaque fois qu'un utilisateur crée un élément `Component` (qui hérite de `NamedElement`), le nom est initialisé automatiquement avec une valeur telle que « Component6 ».

- `DefaultValue`. Si vous avez spécifié cet attribut, la valeur que vous avez spécifiée est assignée à cet attribut pour les nouvelles instances de cette classe. Si `IsElementName` est définie, l'attribut DefaultValue spécifie la partie initiale de la nouvelle chaine.

- **Category** est l’en-tête sous lequel la propriété s’affiche dans la fenêtre **Propriétés** .

## <a name="relationships"></a>Relations

La section `Relationships` énumère toutes les relations dans le langage spécifique à un domaine. Chaque `Domain Relationship` est binaire et dirigée. Elle relie les membres d'une classe source aux membres d'une classe cible. Les classes sources et cibles sont généralement des classes de domaine, mais les relations à d'autres relations sont également autorisées.

Par exemple, la relation Connection relie les membres de la classe OutPort aux membres de la classe InPort. Chaque instance de lien de la relation connecte une instance d'un OutPort à une instance d'un InPort. S'agissant d'une relation de type plusieurs-à-plusieurs, chaque OutPort peut avoir de nombreux liens Connections avec des sources dessus et chaque instance InPort peut avoir de nombreux liens Connections qui la ciblent.

### <a name="source-and-target-roles"></a>Rôles sources et cibles

Chaque relation contient des rôles sources et cibles ayant les attributs suivants :

- L'attribut `RolePlayer` fait référence à la classe de domaine des instances liées : OutPort pour la source, InPort pour la cible.

- L'attribut `Multiplicity` a quatre valeurs possibles (ZeroMany, ZeroOne, One et OneMany). Cet attribut fait référence au nombre de liens de cette relation qui peuvent être associés à un auteur de rôle.

- L'attribut `PropertyName` spécifie le nom qui est utilisé dans la classe de rôle actif pour accéder aux objets à l'autre extrémité. Ce nom est utilisé dans le modèle ou le code personnalisé pour traverser la relation. Par exemple, l'attribut `PropertyName` du rôle source prend la valeur `Targets`. Ainsi, le code suivant fonctionne :

    ```
    OutPort op = ...; foreach (InPort ip in op.Targets) ...
    ```

     Par convention, les noms des propriétés sont au pluriel si la multiplicité est ZeroMany ou OneMany.

     La multiplicité d'un rôle fait référence au nombre de rôles opposés qui peuvent être associés à chaque instance de ce rôle. Par exemple, dans la relation ComponentHasPorts, le rôle cible a l'attribut `RolePlayer` défini sur Port, l'attribut `PropertyName` défini sur Component et l'attribut `Multiplicity` défini sur ZeroOne. Ainsi, le code approprié pour utiliser ce rôle est le suivant :

    ```
    ComponentPort p = ...; Component c = p.Component; if (c != null) ...
    ```

- Le `Name` du rôle est le nom utilisé dans la classe Relationship pour faire référence à cette extrémité d'un lien. Par convention, le nom d'un rôle est toujours au singulier car chaque lien possède une seule instance à chaque extrémité. Le code suivant fonctionne :

    ```
    Connection connectionLink = ...; OutPort op = connectionLink.Source;
    ```

- Par défaut, l'attribut `IsPropertyGenerator` a la valeur True. S'il a la valeur False, aucune propriété n'est créée sur la classe Acteur de rôle. (Dans ce cas, `op.Targets`, par exemple, ne fonctionnerait pas.) Cependant, il est toujours possible d'utiliser du code personnalisé pour traverser la relation ou obtenir l'accès aux liens proprement dits si le code personnalisé utilise la relation de manière explicite :

    ```
    OutPort op = ...; foreach (InPort ip in Connection.GetTargets(op)) ...
    foreach (Connection link in Connection.GetLinksToTargets(op)) ...
    ```

### <a name="relationship-attributes"></a>Attributs de relations

Outre les attributs et les nœuds enfants accessibles à toutes les classes, chaque relation possède les attributs suivants :

- **IsEmbedding**. Cet attribut booléen spécifie si la relation fait partie de l'arborescence d'incorporation. Chaque modèle doit former une arborescence avec ses relations d'incorporation. Chaque classe de domaine doit donc être la cible d'au moins une relation d'incorporation, à moins qu'il s'agisse de la racine d'un modèle.

- **AllowsDuplicates**. Cet attribut booléen, qui a la valeur False par défaut, s'applique uniquement aux relations ayant une multiplicité « many » à la source et à la cible. Il détermine si les utilisateurs du langage peuvent connecter une même paire d'éléments source et cible à l'aide de plusieurs liens de la même relation.

## <a name="designer-and-toolbox-tabs"></a>Onglets du concepteur et de la boîte à outils

La partie principale de la section du **Concepteur** du fichier DslDefinition. DSL est l’élément **ToolBoxTab** . Un concepteur peut avoir plusieurs de ces éléments, chacun d’eux représentant une section intitulée dans la **boîte à outils** du concepteur généré. Chaque élément **ToolBoxTab** peut contenir un ou plusieurs éléments **ElementTool** , **ConnectionTool** , ou les deux.

Les outils d'éléments peuvent créer des instances d'une classe de domaine spécifique. Quand l'utilisateur fait glisser un outil d'élément sur le diagramme, le résultat est déterminé par les directives de fusion d'éléments telles que décrites dans la section relative aux directives de fusion d'éléments plus loin dans cette rubrique.

Chaque outil de connexion peut appeler un générateur de connexion spécifique. Un générateur de connexion peut créer plusieurs types de relations en fonction de l'emplacement où l'utilisateur clique sur la souris, comme décrit dans la section relative aux générateurs de connexions.

Aucun de ces types d'outils ne construit directement des formes ou des connecteurs. Chacun instancie une classe de domaine ou une relation de domaine ; les mappages Forme et Connecteur déterminent ensuite comment cette classe de domaine ou cette relation de domaine apparaît.

## <a name="paths"></a>Chemins

Les chemins d'accès de domaine apparaissent à plusieurs emplacements dans le fichier DslDefinition.dsl. Ces chemins d'accès spécifient une série de liens d'un élément du modèle (autrement dit, une instance du langage spécifique à un domaine) à un autre. La syntaxe de chemin d'accès est simple mais détaillée.

Les chemins d'accès apparaissent dans le fichier DslDefinition.dsl dans des balises `<DomainPath>...</DomainPath>`. Bien que les chemins d'accès puissent parcourir plusieurs liens, dans la pratique la plupart ne traversent qu'un seul lien.

Un chemin d'accès est constitué d'une séquence de segments. Chaque segment est un tronçon d'un objet à un lien ou d'un lien à un objet. Ainsi, dans un long chemin d'accès, les tronçons sont généralement alternés. Le premier tronçon va d'un objet à un lien, le second tronçon mène à l'objet à l'autre extrémité du lien, le troisième tronçon va au lien suivant, et ainsi de suite. Il existe une exception occasionnelle à cette séquence : quand une relation est elle-même la source ou la cible d'une autre relation.

Chaque segment commence par le nom d'une relation. Dans un tronçon d'objet à lien, la relation précède un point et le nom de la propriété : « `Relationship . Property` ». Dans un tronçon de lien à objet, la relation précède un point d'exclamation et le nom du rôle : « `Relationship ! Role` ».

L'exemple de diagramme de composant contient un chemin d'accès dans le ParentElementPath du ShapeMap pour InPort. Ce chemin d'accès commence comme suit :

```
    ComponentHasPorts.Component
```

Dans cet exemple, InPort est une sous-classe de ComponentPort et possède une relation ComponentHasPorts. La Propriété se nomme Component.

Lors de l'écriture de code C# selon ce modèle, vous pouvez parcourir un lien en une étape en utilisant la propriété générée par la relation sur chacune des classes qu'elle met en rapport :

```
     InPort port; ...  Component c = port.Component;
```

Toutefois, vous devez effectuer les deux tronçons de manière explicite en syntaxe de chemin d'accès. Cette exigence simplifie l'accès au lien intermédiaire. Le code suivant achève le tronçon du lien au composant :

```
    ComponentHasPorts.Component / ! Component
```

(Vous pouvez omettre le nom de la relation quand il est identique à celui du segment précédent.)

## <a name="element-merge-directives"></a>Directives de fusion d'éléments

Lorsque l’utilisateur du langage fait glisser un élément de la **boîte à outils** vers le diagramme, une instance de la classe de l’outil est construite. De plus, des liens sont créés entre cette instance et les éléments de modèle existants. Certains éléments, tels que les composants ou les commentaires, sont créés lorsque l’utilisateur du langage les fait glisser de la **boîte à outils** vers une partie vide du diagramme. D'autres éléments sont créés quand l'utilisateur du langage les fait glisser sur d'autres éléments hôtes. Par exemple, un OutPort ou InPort est créé quand l'utilisateur du langage le fait glisser sur un composant.

Une classe hôte potentielle, telle que Component, accepte un nouvel élément uniquement si la classe hôte possède une directive de fusion d'élément pour la classe du nouvel élément. Par exemple, le nœud DomainClass avec Name="Component" contient :

```xml
<DomainClass Name="Component" ...> ...
    <ElementMergeDirective>
      <Index>
        <DomainClassMoniker Name="ComponentPort" />
      </Index>
      <LinkCreationPaths>
        <DomainPath>ComponentHasPorts.Ports</DomainPath>
      </LinkCreationPaths>
    </ElementMergeDirective> ...
```

Le moniker de classe qui se trouve sous le nœud Index fait référence à la classe d'élément qui peut être acceptée. Dans ce cas, ComponentPort est la classe de base abstraite de InPort et OutPort. Ainsi, l'un ou l'autre de ces éléments peut être accepté.

ComponentModel, la classe racine du langage, possède des directives de fusion d'éléments pour les composants et les commentaires. L'utilisateur du langage peut faire glisser des éléments pour cette classe directement sur le diagramme, car les parties vierges du diagramme représentent la classe racine. Toutefois, ComponentModel n'a aucune directive de fusion d'élément pour ComponentPort. Ainsi, l'utilisateur du langage ne peut pas faire glisser des InPorts ou des OutPorts directement sur le diagramme.

La directive de fusion d'élément détermine le ou les liens qui sont créés pour que le nouvel élément puisse être intégré ou fusionné dans le modèle existant. Pour un ComponentPort, une instance de ComponentHasPorts est créée. Le DomainPath identifie à la fois la relation et la propriété de la classe parente, Ports, à laquelle le nouvel élément sera ajouté.

Vous pouvez créer plusieurs liens sur une directive de fusion d'élément en incluant plusieurs chemins d'accès de création de liens. L'un des chemins d'accès doit être incorporé.

Vous pouvez utiliser plusieurs segments dans un chemin d'accès de création de lien. Dans ce cas, le dernier segment définit le lien qui doit être créé. Les segments précédents vont de la classe parente à l'objet à partir duquel le nouveau lien doit être créé.

Par exemple, vous pouvez ajouter cette directive de fusion d'élément à la classe Component :

```xml
<DomainClass Name="Component" ...> ...
  <ElementMergeDirective>
    <Index>
       <DomainClassMoniker Name="Comment"/>
    </Index>
    <LinkCreationPaths>
       <DomainPath>          ComponentModelHasComponents . ComponentModel / !ComponentModel         / ComponentModelHasComments.Comments       </DomainPath>
       <DomainPath>CommentsReferenceComponents.Comments</DomainPath>
    </LinkCreationPaths>
  </ElementMergeDirective>
```

Les utilisateurs du langage peuvent ensuite faire glisser un commentaire sur un composant et faire en sorte que le nouveau commentaire soit créé automatiquement avec un lien au composant.

Le premier chemin d'accès de création de lien va du `Component` au `ComponentModel`, puis il crée une instance de la relation d'incorporation `ComponentModelHasComments`. Le second chemin d'accès de création de lien crée un lien de la relation de référence CommentsReferenceComponents du Component hôte au nouveau Comment. Tous les chemins d'accès de création de lien doivent commencer avec la classe hôte et se terminer à un lien qui va vers la classe nouvellement instanciée.

## <a name="xmlclassdata"></a>XmlClassData

Chaque classe de domaine (y compris les relations et autres sous-types) peuvent avoir des informations supplémentaires fournies dans un nœud `XmlClassData`, qui apparaît sous la section `XmlSerializationBehavior` du fichier DslDefinition.dsl. Ces informations traitent de manière spécifique de la façon dont les instances de la classe sont stockées au format sérialisé quand un modèle est enregistré dans un fichier.

Une grande partie du code généré influencé par `XmlSerializationBehavior` se trouve dans `Dsl\GeneratedCode\Serializer.cs`.

Chaque nœud `XmlClassData` comprend les attributs et les nœuds enfants suivants :

- Un nœud de moniker, qui fait référence à la classe à laquelle les données s'appliquent.

- **XmlPropertyData** pour chaque propriété définie sur la classe.

- **XmlRelationshipData** pour chaque relation qui est source au niveau de la classe. (Les relations ont également leurs propres nœuds XmlClassData.)

- Attribut de chaîne **TypeName** , qui détermine le nom de la classe d’assistance de sérialisation dans le code généré.

- **ElementName** String, qui détermine la balise XML des instances sérialisées de cette classe. Par convention, ElementName est généralement identique au nom de la classe, hormis le fait que la première lettre est en minuscule. Par exemple, un exemple de fichier de modèle commence par ce qui suit :

    ```xml
    <componentModel ...
    ```

- **MonikerElementName** dans les fichiers de modèle sérialisés de l’utilisateur. Cet attribut introduit un moniker qui fait référence à cette classe.

- **MonikerAttributeName**, qui identifie le nom de l’attribut XML dans un moniker. Dans ce fragment du fichier sérialisé d’un utilisateur, l’auteur du langage spécifique à un domaine a défini **MonikerElementName** comme « inPortMoniker » et **MonikerAttributeName** comme « Path » :

    ```xml
    <inPortMoniker path="//Component2/InPort1" />
    ```

### <a name="connectionbuilders"></a>ConnectionBuilders

Un générateur de connexion est défini pour chaque outil de connexion. Chaque générateur de connexion est constitué d'un ou plusieurs éléments LinkConnectDirective, chacun contenant un ou plusieurs éléments SourceDirective et un plusieurs éléments TargetDirective. Après avoir cliqué sur un outil de connexion, l'utilisateur peut établir une connexion à partir de n'importe quelle forme mappée à un élément de modèle qui apparaît dans la liste d'éléments SourceDirective. La connexion peut ensuite se terminer sur une forme qui est mappée à un élément qui apparaît dans la liste d'éléments TargetDirective. La classe de relation instanciée dépend de l'élément LinkConnectDirective désigné par l'emplacement où la connexion a commencé.

### <a name="xmlpropertydata"></a>XmlPropertyData

Un attribut **DomainPropertyMoniker** identifie la propriété à laquelle les données font référence. Cet attribut doit être une propriété de la classe ClassData englobante.

L’attribut **XMLName** donne le nom d’attribut correspondant tel qu’il doit apparaître dans le code XML. Par convention, cette chaîne est identique au nom de la propriété, hormis le fait que la première lettre est en minuscule.

Par défaut, l’attribut de **représentation** est défini sur Attribute. Si la **représentation** est définie sur élément, un nœud enfant est créé dans le XML. Si la **représentation** est définie sur ignore, la propriété n’est pas sérialisée.

Les attributs **IsMonikerKey** et **IsMonikerQualifier** donnent à une propriété un rôle dans l’identification des instances de la classe parente. Vous pouvez affecter à **IsMonikerKey** la valeur true pour une propriété qui est définie dans ou héritée par une classe. Cet attribut identifie une instance spécifique de la classe parente. La propriété à laquelle vous avez affecté la valeur `IsMonikerKey` est généralement un nom ou autre identificateur clé. Par exemple, la propriété de type chaîne `Name` est la clé de moniker pour NamedElement et ses classes dérivées. Quand l'utilisateur enregistre un modèle dans un fichier, cet attribut doit contenir des valeurs uniques pour chaque instance parmi ses frères dans l'arborescence de relations incorporées.

Dans le fichier de modèle sérialisé, le moniker complet d'un élément est un chemin d'accès qui va de la racine de modèle vers le bas de l'arborescence de relations d'incorporation et qui cite la clé de moniker à chaque point. Par exemple, les InPorts sont incorporés dans des Components, qui eux-mêmes sont incorporés dans la racine de modèle. Voici un moniker valide :

```xml
<inPortMoniker name="//Component2/InPort1" />
```

Vous pouvez définir l’attribut **IsMonikerQualifier** pour une propriété de type chaîne et fournir un moyen supplémentaire de construire le nom complet d’un élément. Par exemple, dans le fichier DslDefinition. DSL, l' **espace de noms** est un qualificateur de moniker.

### <a name="xmlrelationshipdata"></a>XmlRelationshipData

Dans un fichier de modèle sérialisé, les liens (des relations d'incorporation et de référence) sont représentés par des nœuds enfants de l'extrémité source de la relation. Pour les relations d'incorporation, le nœud enfant contient une sous-arborescence. Pour les relations de référence, le nœud enfant contient un moniker qui fait référence à une autre partie de l'arborescence.

L’attribut **XmlRelationshipData** dans un attribut **XmlClassData** définit exactement comment les nœuds enfants sont imbriqués dans l’élément source. Chaque relation qui est une source sur la classe de domaine a un attribut **XmlRelationshipData** .

L’attribut **DomainRelationshipMoniker** identifie l’une des relations source sur la classe.

L’attribut **RoleElementName** donne le nom de balise XML qui englobe le nœud enfant dans les données sérialisées.

Par exemple, le fichier DslDefinition.dsl contient :

```xml
<XmlClassData ElementName="component" ...>
  <DomainClassMoniker Name="Component" />
  <ElementData>
    <XmlRelationshipData RoleElementName="ports">
      <DomainRelationshipMoniker Name="ComponentHasPorts" />
    </XmlRelationshipData>
```

Ainsi, le fichier sérialisé contient :

```xml
<component name="Component1"> <!-- parent -->
   <ports> <!-- role -->
     <outPort name="OutPort1"> <!-- child element -->
       ...
     </outPort>
   </ports> ...
```

Si l’attribut **UseFullForm** est défini sur true, une couche supplémentaire d’imbrication est introduite. Cette couche représente la relation proprement dite. L'attribut doit avoir la valeur True si la relation possède des propriétés.

```xml
<XmlClassData ElementName="outPort">
   <DomainClassMoniker Name="OutPort" />
   <ElementData>
     <XmlRelationshipData UseFullForm="true" RoleElementName="targets">
       <DomainRelationshipMoniker Name="Connection" />
     </XmlRelationshipData>
   </ElementData>
 </XmlClassData>
```

Le fichier sérialisé contient :

```xml
<outPort name="OutPort1">  <!-- Parent -->
   <targets>  <!-- role -->
     <connection sourceRoleName="X">  <!-- relationship link -->
         <inPortMoniker name="//Component2/InPort1" /> <!-- child -->
     </connection>
    </targets>
  </outPort>
```

(La relation Connection possède ses propres données de classe XML, qui fournissent ses noms d'éléments et d'attributs.)

Si l’attribut **OmitElement** est défini sur true, le nom de rôle de relation est omis, ce qui permet d’abréger le fichier sérialisé et n’est pas ambigu si les deux classes n’ont pas plus d’une relation. Exemple :

```xml
<component name="Component3">
  <!-- only one relationship could get here: -->
  <outPort name="OutPort1">
     <targets> ...
```

### <a name="serialization-of-a-domain-specific-language-definition"></a>Sérialisation d'une définition de langage spécifique à un domaine

Le fichier DslDefinition.dsl est lui-même un fichier sérialisé et il est conforme à une définition de langage spécifique à un domaine. Voici quelques exemples de définition de sérialisation XML :

- **DSL** est le nœud RootClass et la classe du diagramme. DomainClass, DomainRelationship et d'autres éléments sont incorporés sous `Dsl`.

- **Classes** est le **RoleElementName** de la relation entre Domain-Specific Language et DomainClass.

```xml
<Dsl Name="CmptDsl5" ...>
  <Classes>
    <DomainClass Name="NamedElement" InheritanceModifier="Abstract" ...
```

- L’attribut **XmlSerializationBehavior** est incorporé sous l' `Dsl` attribut, mais l’attribut **OmitElement** a été défini sur la relation d’incorporation. Ainsi, aucun attribut `RoleElementName` n'intervient. En revanche, un attribut **ClassData** est l' `RoleElementName` attribut de la relation d’incorporation entre un attribut **XmlSerializationBehavior** et un attribut **XmlClassData** .

```xml
<Dsl Name="CmptDsl5" ...> ...
  <XmlSerializationBehavior Name="ComponentsSerializationBehavior" >
    <ClassData>
      <XmlClassData ...>...</XmlClassData>
      <XmlClassData ...>...</XmlClassData>
```

- ConnectorHasDecorators est la relation d'incorporation entre `Connector` et `Decorator`. `UseFullForm` a été défini de sorte que le nom de la relation apparaisse avec sa liste de propriétés pour chaque lien de l’objet connecteur. Toutefois, `OmitElement` a également été définie pour qu'aucun `RoleElementName` n'englobe les différents liens incorporés dans `Connector` :

```xml
<Connector Name="AssociationLink" ...>
  <ConnectorHasDecorators Position="TargetTop" ...>
    <TextDecorator Name="TargetRoleName"   />
  </ConnectorHasDecorators>
  <ConnectorHasDecorators Position="SourceTop" ...>
    <TextDecorator Name="SourceRoleName"   />
  </ConnectorHasDecorators>
</Connector>
```

## <a name="shapes-and-connectors"></a>Formes et connecteurs

Les définitions de formes et de connecteurs héritent des attributs et des nœuds enfants des classes de domaine, en plus des éléments suivants :

- attributs `Color` et `Line``Style` ;

- **ExposesFillColorAsProperty** et plusieurs attributs similaires. Ces attributs booléens rendent la propriété correspondante variable par l'utilisateur. En règle générale, lorsqu’un utilisateur du langage clique sur une forme sur le diagramme, les propriétés qui s’affichent dans la fenêtre **Propriétés** sont celles de l’instance de classe de domaine à laquelle la forme est mappée. Si `ExposesFillColorAsProperty` a la valeur True, une propriété de la forme elle-même apparaît également.

- **ShapeHasDecorators**. Une instance de cet attribut se produit chaque décorateur de texte, icône ou développement/réduction. (Dans le fichier DslDefinition.dsl, `ShapeHasDecorators` est une relation avec `UseFullForm` définie sur True.)

## <a name="shape-maps"></a>Mappages de formes

Les mappages de formes déterminent comment les instances d'une classe de domaine apparaissent à l'écran, représentées par une forme. Les mappage de formes et de connecteurs apparaissent sous la section `Diagram` du fichier DslDefinition.dsl.

Comme dans l'exemple suivant, les éléments `ShapeMap` ont, au minimum, le moniker d'une classe de domaine, le moniker d'une forme et un élément `ParentElementPath` :

```xml
<ShapeMap>
  <DomainClassMoniker Name="InPort" />
  <ParentElementPath>
    <DomainPath>ComponentHasPorts.Component/!Component</DomainPath>
  </ParentElementPath>
  <PortMoniker Name="InPortShape" />
</ShapeMap>
```

La fonction principale de l'élément `ParentElementPath` est de faire en sorte que la même classe d'objets puisse apparaître en tant que forme différente dans différents contextes. Par exemple, si un `InPort` peut également être incorporé dans un commentaire, l'`InPort` peut apparaître en tant que forme différente à cette fin.

Le chemin d'accès détermine la relation entre la forme et son parent. Aucune structure d'incorporation n'est définie entre les formes dans un fichier DslDefinition.dsl. Vous devez déduire la structure à partir des mappages de formes. Le parent d'une forme est la forme qui est mappée à l'élément de domaine identifié par le chemin d'accès d'élément parent. Dans ce cas, le chemin d'accès identifie le composant auquel l'`InPort` appartient. Dans un autre mappage de forme, la classe Component est mappée à ComponentShape. Ainsi, la nouvelle forme `InPort` devient une forme enfant du `ComponentShape` de son composant.

Si vous attachiez plutôt la forme InPort au diagramme, le chemin d'accès d'élément parent devrait effectuer un pas supplémentaire, jusqu'au modèle de composant, qui est mappé au diagramme :

```
ComponentHasPorts . Component / ! Component /    ComponentModelHasComponents . ComponentModel / ! ComponentModel
```

La racine du modèle ne possède pas de mappage de forme. Au lieu de cela, la racine est référencé directement à partir du diagramme, qui possède un élément `Class` :

```xml
<Diagram Name="ComponentDiagram" >
    <Class>
      <DomainClassMoniker Name="ComponentModel" />
    </Class>...
```

### <a name="decorator-maps"></a>Mappages de décorateurs

Un mappage de décorateur associe une propriété dans la classe mappée à un décorateur sur la forme. Si la propriété est de type énuméré ou booléen, sa valeur peut déterminer si le décorateur est visible. Si le décorateur est un décorateur de texte, la valeur de la propriété peut apparaître et l'utilisateur peut la modifier.

### <a name="compartment-shape-maps"></a>Mappages de formes de compartiments

Les mappages de formes de compartiments sont des sous-types de mappages de formes.

## <a name="connector-maps"></a>Mappages de connecteurs

Le mappage de connecteur minimal fait référence à un connecteur et à une relation :

```xml
<ConnectorMap>
  <ConnectorMoniker Name="CommentLink" />
  <DomainRelationshipMoniker Name="CommentsReferenceComponents" />
</ConnectorMap>
```

Les mappages de connecteurs peuvent aussi contenir des mappages de décorateurs.

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](/previous-versions/bb126564(v=vs.100))
- [Guide pratique pour définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md)
- [Présentation des modèles, des classes et des relations](../modeling/understanding-models-classes-and-relationships.md)