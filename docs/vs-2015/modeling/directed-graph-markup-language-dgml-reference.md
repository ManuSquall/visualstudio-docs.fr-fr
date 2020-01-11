---
title: Informations de référence sur le langage DGML (Directed Graph Markup Language) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: cc3e4ae7-60fa-4e22-9227-98020b480b73
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c676c57d6e6e6008611133235df8d525752f16b5
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849504"
---
# <a name="directed-graph-markup-language-dgml-reference"></a>Informations de référence sur le langage DGML (Directed Graph Markup Language)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le langage DGML (Directed Graph Markup Language) décrit les informations utilisées pour la visualisation et l'analyse de complexité. Il s'agit du format utilisé pour faire persister des cartes de code dans Visual Studio. Il utilise le langage XML simple pour décrire des graphiques orientés à la fois cycliques et acycliques. Un graphique orienté est un ensemble de nœuds reliés par des liens (ou bords). Les nœuds et les liens peuvent être utilisés pour représenter des structures interconnectées, telles que les éléments d'un projet logiciel.

 Notez que certaines versions de Visual Studio ne prennent en charge qu’un sous-ensemble de fonctionnalités DGML, consultez [prise en charge des versions pour les outils d’architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Lorsque vous modifiez un fichier .dgml, IntelliSense vous aide à identifier les attributs qui sont disponibles pour chaque élément, ainsi que leurs valeurs. Pour spécifier la couleur dans un attribut, utilisez le nom des couleurs courantes (« Bleu », par exemple) ou des valeurs hexadécimales ARVB (« #ffa0b1c3 », par exemple). Le langage DGML utilise un sous-ensemble réduit de formats de définition de couleur WPF (Windows Presentation Foundation). Pour plus d’informations, consultez [Color, classe](https://msdn.microsoft.com/library/system.windows.media.colors.aspx).

## <a name="DGML"></a>Syntaxe DGML
 Le tableau suivant décrit les types d'éléments utilisés en langage DGML :

- `<DirectedGraph></DirectedGraph>`

   Cet élément est l'élément racine du document de carte de code (.dgml). Tous les autres éléments DGML s'inscrivent dans la portée de cet élément.

   La liste suivante décrit des attributs facultatifs que vous pouvez inclure :

   `Background`-la couleur de l’arrière-plan de la carte

   `BackgroundImage` : emplacement d’un fichier image à utiliser comme arrière-plan de la carte.

   `GraphDirection`-lorsque la carte est définie sur disposition de l’arborescence (`Sugiyama`), réorganisez les nœuds de sorte que la plupart des liens circulent dans la direction spécifiée : `TopToBottom`, `BottomToTop`, `LeftToRight`ou `RightToLeft`. Consultez [modifier la disposition de la carte](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `Layout`-définissez la carte sur les dispositions suivantes : `None`, `Sugiyama` (disposition en arborescence), `ForceDirected` (clusters rapides) ou `DependencyMatrix`. Consultez [modifier la disposition de la carte](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   `NeighborhoodDistance`-lorsque la carte est définie sur disposition de l’arborescence ou sur clusters rapides, Affichez uniquement les nœuds qui sont un nombre spécifié (1-7) de liens hors des nœuds sélectionnés. Consultez [modifier la disposition de la carte](../modeling/browse-and-rearrange-code-maps.md#Selecting).

   Exemple :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" Background="Blue" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        ...
     </Nodes>
     <Links>
        ...
     </Links>
     <Categories>
        ...
     </Categories>
     <Properties>
        ...
     </Properties>
  </DirectedGraph>
  ```

- `<Nodes></Nodes>`

   Cet élément facultatif contient une liste d'éléments `<Node/>` qui définissent des nœuds sur la carte. Pour plus d'informations, consultez l'élément `<Node/>`.

  > [!NOTE]
  > Quand vous faites référence à un nœud non défini dans un élément `<Link/>`, la carte crée automatiquement un élément `<Node/>`.

   Exemple :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node ... />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Node/>`

   Cet élément définit un nœud unique. Il figure dans la liste des éléments `<Nodes><Nodes/>`.

   Cet élément doit inclure les attributs suivants :

   `Id` : nom unique du nœud et valeur par défaut de l’attribut `Label`, si aucun attribut `Label` distinct n’est spécifié. Ce nom doit correspondre à l'attribut `Source` ou `Target` du lien qui y fait référence.

   La liste suivante décrit certains des attributs facultatifs que vous pouvez inclure :

   `Label` : nom d’affichage du nœud.

   Attributs Style. Consultez [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category`-le nom d’une catégorie qui identifie les éléments qui partagent cet attribut. Pour plus d'informations, consultez l'élément `<Category/>`.

   `Property`-le nom d’une propriété qui identifie les éléments qui ont la même valeur de propriété. Pour plus d'informations, consultez l'élément `<Property/>`.

   `Group` - Si le nœud contient d'autres nœuds, affectez à cet attribut la valeur `Expanded` ou `Collapsed` pour respectivement en afficher ou en masquer le contenu. Un élément `<Link/>` doit inclure l'attribut `Category="Contains"` et spécifier le nœud parent en tant que nœud source et le nœud enfant en tant que nœud cible. Consultez [regrouper des éléments de code](../modeling/customize-code-maps-by-editing-the-dgml-files.md#OrganizeNodes).

   `Visibility`-définissez cet attribut sur `Visible`, `Hidden`ou `Collapsed`. Utilise `System.Windows.Visibility`. Consultez [masquer ou afficher les nœuds et les liens](../modeling/browse-and-rearrange-code-maps.md#HidingShowing).

   `Reference` - Définissez cet attribut pour le lier à un document ou une URL. Consultez [lier des documents ou des URL à des éléments de code et des liens](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AddReferences).

   Exemple :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Link ... />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
     </Categories>
  </DirectedGraph>
  ```

- `<Links></Links>`

   Cet élément contient la liste des éléments `<Link>` qui définissent des liens entre des nœuds. Pour plus d'informations, consultez l'élément `<Link/>`.

   Exemple :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Links>
        <Link ... />
     </Links>
  </DirectedGraph>
  ```

- `<Link/>`

   Cet élément définit un lien unique qui relie un nœud source à un nœud cible. Il figure dans la liste des éléments `<Links></Links>`.

  > [!NOTE]
  > Si cet élément fait référence à un nœud non défini, le document de la carte crée automatiquement un nœud qui possède les attributs spécifiés, le cas échéant.

   Cet élément doit inclure les attributs suivants :

   `Source` : nœud source du lien

   `Target` - Nœud cible du lien.

   La liste suivante décrit certains des attributs facultatifs que vous pouvez inclure :

   `Label` : nom d’affichage du lien

   Attributs Style. Consultez [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   `Category`-le nom d’une catégorie qui identifie les éléments qui partagent cet attribut. Pour plus d'informations, consultez l'élément `<Category/>`.

   `Property`-le nom d’une propriété qui identifie les éléments qui ont la même valeur de propriété. Pour plus d'informations, consultez l'élément `<Property/>`.

   Exemple :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Student" Category="Person" />
        <Node Id="Passenger" Label="Instructor" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
     </Nodes>
     <Links>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Link Source="Driver" Target="Car" Label="Passed" Stroke="Black" Background="Green" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Stroke="Black" Background="Red" Category="PassedTest" />
     </Links>
  </DirectedGraph>
  ```

- `<Categories></Categories>`

   Cet élément contient la liste des éléments `<Category/>`. Pour plus d'informations, consultez l'élément `<Category/>`.

   Exemple :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Categories>
         <Category ... />
     </Categories>
  </DirectedGraph>
  ```

- `<Category/>`

   Cet élément définit un attribut `Category` qui permet d'identifier les éléments qui partagent cet attribut. Un attribut `Category` peut être utilisé pour organiser des éléments de carte, proposer des attributs partagés par héritage ou définir d'autres métadonnées.

   Cet élément doit inclure les attributs suivants :

   `Id` - Nom unique de la catégorie et valeur par défaut de l'attribut `Label`, lorsqu'aucun attribut `Label` séparé n'est spécifié.

   La liste suivante décrit certains des attributs facultatifs que vous pouvez inclure :

   `Label` - Nom convivial de la catégorie.

   `BasedOn` : catégorie parente dont l' `<Category/>` de l’élément actuel hérite.

   Dans l'exemple donné pour cet élément, la catégorie `FailedTest` hérite de son attribut `Stroke` à partir de la catégorie `PassedTest`. Consultez « pour créer des catégories hiérarchiques » dans [personnaliser les cartes de code en modifiant les fichiers dgml](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   Les catégories proposent également un comportement de modèle de base qui contrôle l'apparence des nœuds et des liens lorsqu'ils s'affichent sur une carte. Consultez [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

   Exemple :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" />
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
  </DirectedGraph>
  ```

- `<Properties></Properties>`

   Cet élément contient la liste des éléments `<Property/>`. Pour plus d'informations, consultez l'élément `<Property/>`.

   Exemple :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Properties>
         <Property ... />
     </Properties>
  </DirectedGraph>
  ```

- `<Property/>`

   Cet élément définit un attribut `Property` que vous pouvez utiliser pour assigner une valeur à tout attribut ou élément DGML, y compris des catégories et autres propriétés.

   Cet élément doit inclure les attributs suivants :

  - `Id`-le nom unique de la propriété et la valeur par défaut de l’attribut `Label`, si aucun attribut `Label` distinct n’est spécifié.

  - `DataType`-le type de données stockées par la propriété

    Si vous souhaitez que la propriété s’affiche dans la fenêtre **Propriétés** , utilisez la propriété `Label` pour spécifier le nom d’affichage de la propriété.

    Consultez [assigner des catégories aux éléments de code et aux liens](../modeling/customize-code-maps-by-editing-the-dgml-files.md#AssignCategories).

    Exemple :

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <DirectedGraph Title="DrivingTest" xmlns="http://schemas.microsoft.com/vs/2009/dgml">
     <Nodes>
        <Node Id="Driver" Label="Driver" Category="Person" DrivingAge="18"/>
        <Node Id="Car" Label="Car" Category="Automobile" />
        <Node Id="Truck" Label="Truck" Category="Automobile" />
        <Node Id="Passenger" Category="Person" />
     </Nodes>
     <Links>
        <Link Source="Driver" Target="Car" Label="Passed" Category="PassedTest" />
        <Link Source="Driver" Target="Truck" Label="Failed" Category="FailedTest" />
     </Links>
     <Categories>
        <Category Id="Person" Background="Orange" />
        <Category Id="Automobile" Background="Yellow"/>
        <Category Id="PassedTest" Label="Passed" Stroke="Black" Background="Green" />
        <Category Id="FailedTest" Label="Failed" BasedOn="PassedTest" Background="Red" />
     </Categories>
     <Properties>
         <Property Id="DrivingAge" Label="Driving Age" DataType="System.Int32" />
     </Properties>
  </DirectedGraph>
  ```

### <a name="AddAlias"></a>Alias pour les chemins d’accès fréquemment utilisés
 Lorsque vous remplacez des chemins d'accès fréquemment utilisés par des alias, vous réduisez la taille du fichier .dgml, ainsi que la durée nécessaire au téléchargement et à l'enregistrement du fichier. Pour créer un alias, ajoutez une section `<Paths></Paths>` à la fin du fichier .dgml. Dans cette section, ajoutez un élément `<Path/>` pour définir un alias pour le chemin d'accès :

```xml
<Paths>
   <Path Id="MyPathAlias" Value="C:\...\..." />
</Paths>
```

 Pour référencer l’alias à partir d’un élément dans le fichier. dgml, mettez l' `Id` de l’élément \<Path/> avec un signe dollar ($) et des parenthèses (()) :

```xml
<Nodes>
   <Node Id="MyNode" Reference="$(MyPathAlias)MyDocument.txt" />
</Nodes>
<Properties>
   <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
</Properties>
```

## <a name="see-also"></a>Voir aussi
 [Mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md) [utiliser des cartes de code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md) [Rechercher des problèmes potentiels à l’aide d’analyseurs de carte de code](../modeling/find-potential-problems-using-code-map-analyzers.md)
