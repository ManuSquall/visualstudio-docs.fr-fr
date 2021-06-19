---
title: Personnaliser des cartes de code en modifiant les fichiers DGML
description: Découvrez comment personnaliser une carte de code en modifiant son fichier. DGML (Directed Graph Markup Language).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency graphs, creating path aliases
- dependency graphs, linking items to nodes
- graph documents, creating path aliases
- dependency graphs, grouping nodes
- graph documents, editing
- graph documents, linking items to nodes
- graph documents, customizing
- graph documentings, assigning categories and properties
- dependency graphs, editing
- dependency graphs, customizing
- graph documents, grouping nodes
- dependency graphs, assigning categories and properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5b7c94834aeb6aa82efdb53dead97e26daa667c0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389486"
---
# <a name="customize-code-maps-by-editing-the-dgml-files"></a>Personnaliser des cartes de code en modifiant les fichiers DGML

Pour personnaliser une carte de code, vous pouvez modifier son fichier. DGML (Directed Graph Markup Language). Par exemple, vous pouvez modifier des éléments pour spécifier des styles personnalisés, affecter des propriétés et des catégories à des éléments de code et des liens, ou lier des documents ou des URL à des éléments de code ou des liens. Pour plus d’informations sur les éléments DGML, consultez informations de référence sur le [langage DGML (Directed Graph Markup Language)](../modeling/directed-graph-markup-language-dgml-reference.md).

Modifiez le fichier .dgml de la carte de code dans un éditeur de texte ou un éditeur XML. Si le mappage fait partie de votre solution Visual Studio, sélectionnez-le dans **Explorateur de solutions**, ouvrez le menu contextuel, puis choisissez **Ouvrir avec**, **éditeur XML (texte)**.

> [!NOTE]
> Pour créer des cartes de code, vous devez disposer de l’édition Visual Studio Enterprise. Quand vous modifiez une carte de code dans Visual Studio, il nettoie tous les attributs et éléments DGML inutilisés en les supprimant lorsque vous enregistrez le fichier .dgml. Il crée aussi des éléments de code automatiquement quand vous ajoutez manuellement de nouveaux liens. Lorsque vous enregistrez le fichier .dgml, tous les attributs que vous avez ajoutés à un élément peuvent être réorganisés par ordre alphabétique.

## <a name="group-code-elements"></a><a name="OrganizeNodes"></a> Grouper les éléments de code
 Vous pouvez ajouter de nouveaux groupes ou convertir des nœuds existants dans un groupe.

1. Dans un éditeur XML ou un éditeur de texte, ouvrez le fichier .dgml.

2. Pour convertir un élément de code en groupe, recherchez l'élément `<Node/>` correspondant à cet élément de code.

    \- ou -

    Pour ajouter un nouveau groupe, recherchez la section `<Nodes>`. Ajoutez un nouvel élément `<Node/>`.

3. Dans l’élément `<Node/>`, ajoutez un attribut `Group` pour spécifier si le groupe apparaît développé ou réduit. Exemple :

   ```xml
   <Nodes>
      <Node Id="MyFirstGroup" Group="Expanded" />
      <Node Id="MySecondGroup" Group="Collapsed" />
   </Nodes>
   ```

4. Dans la section `<Links>`, vérifiez qu'un élément `<Link/>` ayant les attributs suivants existe pour chaque relation entre un élément de code de groupe et ses éléments de code enfants :

   - un attribut `Source` qui spécifie l'élément de code de groupe ;

   - un attribut `Target` qui spécifie l'élément de code enfant ;

   - un attribut `Category` qui spécifie une relation `Contains` entre l'élément de code de groupe et son élément de code enfant.

     Exemple :

   ```xml
   <Links>
      <Link Category="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildOne" />
      <Link Category ="Contains" Source="MyFirstNewGroup" Target="FirstGroupChildTwo" />
      <Link Category ="Contains" Source="MySecondNewGroup" Target="SecondGroupChildOne" />
      <Link Category="Contains" Source="MySecondNewGroup" Target="SecondGroupChildTwo" />
   </Links>
   ```

    Pour plus d’informations sur l' `Category` attribut, consultez [assigner des catégories aux éléments de code et aux liens](#AssignCategories).

## <a name="change-the-style-of-the-map"></a><a name="ChangeGraphStyle"></a> Modifier le style de la carte
 Vous pouvez changer la couleur de l'arrière-plan et de la bordure de la carte en modifiant son fichier .dgml. Pour modifier le style des éléments de code et des liens, consultez [modifier le style des éléments de code et des liens](#Highlight).

1. Dans un éditeur XML ou un éditeur de texte, ouvrez le fichier .dgml.

2. Dans l'élément `<DirectedGraph>`, ajoutez l'un des attributs suivants pour modifier son style :

     Couleur d’arrière-plan

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     Couleur de la bordure

    ```xml
    Stroke="StrokeValue"
    ```

     Exemple :

    ```xml
    <DirectedGraph Background="Green" xmlns="http://schemas.microsoft.com/vs/2009/dgml" >
       ...
       ...
    </DirectedGraph>
    ```

## <a name="change-the-style-of-code-elements-and-links"></a><a name="Highlight"></a> Modifier le style des éléments de code et des liens

### <a name="CreateCustomStyles"></a>
 Vous pouvez appliquer des styles personnalisés aux éléments de code suivants :

- liens et éléments de code uniques ;

- groupes d'éléments de code et liens ;

- groupes d'éléments de code et liens selon certaines conditions.

> [!TIP]
> Si vous avez répété des styles sur de nombreux éléments de code ou liens, vous pouvez appliquer une catégorie à ces éléments de code ou à ces liens, puis appliquer un style à cette catégorie. Pour plus d’informations, consultez [assigner des catégories aux éléments de code et aux liens](#AssignCategories) et [assigner des propriétés aux éléments de code et aux liens](#AssignProperties).

##### <a name="to-apply-a-custom-style-to-a-single-code-element"></a>Pour appliquer un style personnalisé à un seul élément de code

1. Dans un éditeur XML ou un éditeur de texte, ouvrez le fichier .dgml.

2. Recherchez l'élément `<Node/>` de l'élément de code. Ajoutez l'un de ces attributs pour personnaliser son style :

     Couleur d’arrière-plan

    ```xml
    Background="ColorNameOrHexadecimalValue"
    ```

     Plan

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     Épaisseur du contour

    ```xml
    StrokeThickness="StrokeValue"
    ```

     Couleur du texte

    ```xml
    Foreground="ColorNameOrHexadecimalValue"
    ```

     Icône

    ```xml
    Icon="IconFilePathLocation"
    ```

     Taille du texte

    ```xml
    FontSize="FontSizeValue"
    ```

     Type Texte

    ```xml
    FontFamily="FontFamilyName"
    ```

     Épaisseur de police du texte

    ```xml
    FontWeight="FontWeightValue"
    ```

     Style de texte

    ```xml
    FontStyle="FontStyleName"
    ```

     Par exemple, vous pouvez spécifier `Italic` comme style de texte.

     Texture

    ```xml
    Style="Glass"
    ```

     - ou -

    ```xml
    Style="Plain"
    ```

     Graphique à base de formes

     Pour remplacer la forme par une icône, définissez la propriété `Shape` avec la valeur `None` et affectez la propriété `Icon` au chemin d'accès du fichier icône.

    ```xml
    Shape="ShapeFilePathLocation"
    ```

     Exemple :

    ```xml
    <Nodes>
       <Node Id="MyNode" Background="#FF008000" Stroke="#FF000000"
       Foreground="#FFFFFFFF" Icon="...\Icons\Globe.png"/>
    </Nodes>
    ```

##### <a name="to-apply-a-custom-style-to-a-single-link"></a>Pour appliquer un style personnalisé à un seul lien

1. Dans un éditeur XML ou un éditeur de texte, ouvrez le fichier .dgml.

2. Recherchez l'élément `<Link/>` qui contient à la fois les noms de l'élément de code source et de l'élément de code cible.

3. Dans l'élément `<Link/>`, ajoutez l'un des attributs suivants pour personnaliser son style :

     Couleur du contour et de la pointe de flèche

    ```xml
    Stroke="ColorNameOrHexadecimalValue"
    ```

     Épaisseur du contour

    ```xml
    StrokeThickness="StrokeValue"
    ```

     Style de contour

    ```xml
    StrokeDashArray="StrokeArrayValues"
    ```

     Exemple :

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Background="Green" Stroke="#FF000000" StrokeDashArray="2,2"/>
    </Links>
    ```

##### <a name="to-apply-custom-styles-to-a-group-of-code-elements-or-links"></a>Pour appliquer des styles personnalisés à un groupe d'éléments de code ou à des liens

1. Dans un éditeur XML ou un éditeur de texte, ouvrez le fichier .dgml.

2. S'il n'existe pas d'élément `<Styles></Styles>`, ajoutez-en un sous l'élément `<DirectedGraph></DirectedGraph>`, après l'élément `<Links></Links>`.

3. Dans l'élément `<Styles></Styles>`, sous l'élément `<Style/>`, spécifiez les attributs suivants :

   - `TargetType="Node` &#124; `Link | Graph"`

   - `GroupLabel="`*NameInLegendBox*`"`

   - `ValueLabel="`*NameInStylePickerBox*`"`

     Pour appliquer un style personnalisé à tous les types cibles, n'utilisez pas de condition.

##### <a name="to-apply-a-conditional-style-to-groups-of-code-elements-or-links"></a>Pour appliquer un style conditionnel à des groupes d'éléments de code ou des liens

1. Dans un éditeur XML ou un éditeur de texte, ouvrez le fichier .dgml.

2. Dans l'élément `<Style/>`, ajoutez un élément `<Condition/>` contenant un attribut `Expression` pour spécifier une expression qui retourne une valeur booléenne.

    Exemple :

   ```xml
   <Condition Expression="MyCategory"/>
   ```

    - ou -

   ```xml
   <Condition Expression="MyCategory > 100"/>
   ```

    - ou -

   ```xml
   <Condition Expression="HasCategory('MyCategory')"/>
   ```

    Cette expression utilise la syntaxe de notation BNF (Backus-Naur) suivante :

    \<Expression> :: = \<BinaryExpression> &#124; \<UnaryExpression> &#124; "(" \<Expression> ")" &#124; \<MemberBindings> &#124; \<Literal> &#124; \<Number>

    \<BinaryExpression>::= \<Expression> \<Operator>\<Expression>

    \<UnaryExpression> ::= "!" \<Expression> &#124; « + » \<Expression> &#124; « - » \<Expression>

    \<Operator> :: = "<" &#124; " \<=" &#124; "=" &#124; "> =" &#124; ">" &#124; " ! =" &#124; "ou" &#124; "et" &#124; "+" &#124; "*" &#124; "/" &#124; "-"

    \<MemberBindings> :: = \<MemberBindings> &#124; \<MemberBinding> "." \<MemberBinding>

    \<MemberBinding> :: = \<MethodCall> &#124; \<PropertyGet>

    \<MethodCall> ::= \<Identifier> "(" \<MethodArgs> ")"

    \<PropertyGet> :: = Identificateur

    \<MethodArgs> :: = \<Expression> &#124; \<Expression> "," \<MethodArgs> &#124; \<empty>

    \<Identifier> ::= [^. ]*

    \<Literal> :: = littéral de chaîne entre guillemets simples ou doubles

    \<Number> :: = chaîne de chiffres avec une virgule décimale facultative

    Vous pouvez spécifier plusieurs `<Condition/>` éléments, qui doivent tous avoir la valeur true pour appliquer le style.

3. Sur la ligne suivante, après l'élément `<Condition/>`, ajoutez un ou plusieurs éléments `<Setter/>` pour spécifier un attribut `Property` et un attribut `Value` fixe ou un attribut `Expression` calculé à appliquer à la carte, aux éléments de code ou aux liens qui remplissent la condition.

    Exemple :

   ```xml
   <Setter Property="BackGround" Value="Green"/>
   ```

   À titre d'exemple simple et complet, la condition suivante spécifie qu'un élément de code apparaît en vert ou en rouge selon que sa catégorie `Passed` a la valeur `True` ou `False` :

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
   <Nodes>
      <Node Id="MyFirstNode" Passed="True" />
      <Node Id="MySecondNode" Passed="False" />
   </Nodes>
   <Links>
   </Links>
   <Styles>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="True">
         <Condition Expression="Passed='True'"/>
         <Setter Property="Background" Value="Green"/>
      </Style>
      <Style TargetType="Node" GroupLabel="Passed" ValueLabel="False">
         <Condition Expression="Passed='False'"/>
         <Setter Property="Background" Value="Red"/>
      </Style>
   </Styles>
</DirectedGraph>
```

 Le tableau suivant inclut des conditions d'exemple que vous pouvez utiliser :

 Définir la taille de police en fonction du nombre de lignes de code, qui modifie également la taille de l'élément de code. Cet exemple utilise une expression conditionnelle unique pour définir plusieurs propriétés : `FontSize` et `FontFamily`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" LinesOfCode ="200" />
   <Node Id="Class2" LinesOfCode ="1000" />
   <Node Id="Class3" LinesOfCode ="20" />
</Nodes>
<Properties>
   <Property Id="LinesOfCode" Label="LinesOfCode" Description="LinesOfCode" DataType="System.Int32" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="LinesOfCode" ValueLabel="Function">
      <Condition Expression="LinesOfCode > 0" />
      <Setter Property="FontSize" Expression="Math.Max(9,Math.Sqrt(LinesOfCode))" />
      <Setter Property="FontFamily" Value="Papyrus" />
   </Style>
</Styles>
</DirectedGraph>
```

 Définir la couleur d'arrière-plan d'un élément de code en fonction de la propriété `Coverage`. Les styles sont évalués dans leur ordre d'apparition, comme les instructions `if-else`.

 Dans cet exemple :

1. Si `Coverage` est > 80, affectez la valeur `Background` Green à la propriété.

2. Sinon `Coverage` , si est > 50, affectez `Background` à la propriété une nuance d’orange en fonction de la valeur de la `Coverage` propriété.

3. Sinon, affectez une nuance rouge à la propriété `Background` en fonction de la valeur de la propriété `Coverage`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Class1" Coverage="58" />
   <Node Id="Class2" Coverage="95" />
   <Node Id="Class3" Coverage="32" />
</Nodes>
<Properties>
   <Property Id="Coverage" Label="Coverage" Description="Code coverage as a percentage of blocks" DataType="Double" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Good">
      <Condition Expression="Coverage > 80" />
      <Setter Property="Background" Value="Green" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="OK">
      <Condition Expression="Coverage > 50" />
      <Setter Property="Background" Expression="Color.FromRgb(180 * Math.Max(1, (80 - Coverage) / 30), 180, 0)" />
   </Style>
   <Style TargetType="Node" GroupLabel="Coverage" ValueLabel="Bad">
      <Setter Property="Background" Expression="Color.FromRgb(180, 180 * Coverage / 50, 0)" />
   </Style>
</Styles>
</DirectedGraph>
```

 Affecter à la propriété `Shape` la valeur `None` afin que l'icône remplace la forme. Utilisez la propriété `Icon` pour spécifier l'emplacement de l'icône.

```xml
<DirectedGraph xmlns="http://schemas.microsoft.com/vs/2009/dgml">
<Nodes>
   <Node Id="Automation" Category="Test" Label="Automation" />
   <Node Id="C# Provider" Category="Provider" Label="C# Provider" />
</Nodes>
<Categories>
   <Category Id="Provider" Icon="...\Icons\Module.png" Shape="None" />
   <Category Id="Test" Icon="...\Icons\Page.png" Shape="None" />
</Categories>
<Properties>
   <Property Id="Icon" DataType="System.String" />
   <Property Id="Label" Label="Label" Description="Displayable label of an Annotatable object" DataType="System.String" />
   <Property Id="Shape" DataType="System.String" />
</Properties>
<Styles>
   <Style TargetType="Node" GroupLabel="Group" ValueLabel="Has category">
      <Condition Expression="HasCategory('Group')" />
      <Setter Property="Background" Value="#80008080" />
   </Style>
   <Style TargetType="Node">
      <Setter Property="HorizontalAlignment" Value="Center" />
   </Style>
</Styles>
</DirectedGraph>
```

## <a name="assign-properties-to-code-elements-and-links"></a><a name="AssignProperties"></a> Assigner des propriétés aux éléments de code et aux liens
 Vous pouvez organiser des éléments de code et des liens en leur assignant des propriétés. Par exemple, vous pouvez sélectionner des éléments de code ayant des propriétés spécifiques pour pouvoir les regrouper, modifier leur style ou les masquer.

#### <a name="to-assign-a-property-to-a-code-element"></a>Pour assigner une propriété à un élément de code

1. Dans un éditeur XML ou un éditeur de texte, ouvrez le fichier .dgml.

2. Recherchez l'élément `<Node/>` pour cet élément de code. Spécifiez le nom de la propriété et sa valeur. Exemple :

    ```xml
    <Nodes>
       <Node Id="MyNode" MyPropertyName="PropertyValue" />
    </Nodes>
    ```

3. Ajoutez un élément `<Property/>` à la section `<Properties>` pour spécifier des attributs, tels que ses nom visible et type de données :

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property" DataType="System.DataType"/>
    </Properties>
    ```

#### <a name="to-assign-a-property-to-a-link"></a>Pour assigner une propriété à un lien

1. Dans un éditeur XML ou un éditeur de texte, ouvrez le fichier .dgml.

2. Recherchez l'élément `<Link/>` qui contient à la fois les noms de l'élément de code source et de l'élément de code cible.

3. Dans l'élément `<Node/>`, spécifiez le nom de la propriété et sa valeur. Exemple :

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" MyPropertyName="PropertyValue" />
    </Links>
    ```

4. Ajoutez un élément `<Property/>` à la section `<Properties>` pour spécifier des attributs, tels que ses nom visible et type de données :

    ```xml
    <Properties>
       <Property Id="MyPropertyName" Label="My Property Name" DataType="System.DataType"/>
    </Properties>
    ```

## <a name="assign-categories-to-code-elements-and-links"></a><a name="AssignCategories"></a> Assigner des catégories aux éléments de code et aux liens
 Les sections suivantes expliquent comment organiser des éléments de code en leur assignant des catégories et comment créer des catégories hiérarchiques qui vous aident à organiser les éléments de code et ajouter des attributs aux catégories enfants à l'aide de l'héritage.

#### <a name="to-assign-a-category-to-a-code-element"></a>Pour assigner une catégorie à un élément de code

- Dans un éditeur XML ou un éditeur de texte, ouvrez le fichier .dgml.

- Recherchez l'élément `<Node/>` pour l'élément de code souhaité.

- Dans l'élément `<Node/>`, ajoutez un attribut `Category` pour spécifier le nom de la catégorie. Exemple :

    ```xml
    <Nodes>
       <Node Id="MyNode" Category="MyCategory" />
    </Nodes>
    ```

     Ajoutez un élément `<Category/>` à la section `<Categories>` afin de pouvoir utiliser l'attribut `Label` pour spécifier le texte affiché de la catégorie :

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-assign-a-category-to-a-link"></a>Pour assigner une catégorie à un lien

1. Dans un éditeur XML ou un éditeur de texte, ouvrez le fichier .dgml.

2. Recherchez l'élément `<Link/>` qui contient à la fois les noms de l'élément de code source et de l'élément de code cible.

3. Dans l'élément `<Link/>`, ajoutez un attribut `Category` pour spécifier le nom de la catégorie. Exemple :

    ```xml
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" Category="MyCategory"
    </Links>
    ```

4. Ajoutez un élément `<Category/>` à la section `<Categories>` afin de pouvoir utiliser l'attribut `Label` pour spécifier le texte affiché de la catégorie :

    ```xml
    <Categories>
       <Category Id="MyCategory" Label="My Category" />
    </Categories>
    ```

#### <a name="to-create-hierarchical-categories"></a>Pour créer des catégories hiérarchiques

1. Dans un éditeur XML ou un éditeur de texte, ouvrez le fichier .dgml.

2. Ajoutez d'abord un élément `<Category/>` pour la catégorie parente, puis l'attribut `BasedOn` à l'élément `<Category/>` de la catégorie enfant.

     Exemple :

    ```xml
    <Nodes>
       <Node Id="MyFirstNode" Label="My First Node" Category= "MyCategory" />
       <Node Id="MySecondNode" Label="My Second Node" />
    </Nodes>
    <Links>
       <Link Source="MyFirstNode" Target="MySecondNode" />
    </Links>
    <Categories>
       <Category Id="MyCategory" Label="My Category" BasedOn="MyParentCategory"/>
       <Category Id="MyParentCategory" Label="My Parent Category" Background="Green"/>
    </Categories>
    ```

     Dans cet exemple, l'arrière-plan de `MyFirstNode` est vert car son attribut `Category` hérite de l'attribut `Background` de `MyParentCategory`.

## <a name="link-documents-or-urls-to-code-elements-and-links"></a><a name="AddReferences"></a> Lier des documents ou des URL à des éléments de code et des liens
 Vous pouvez lier des éléments ou des URL à des éléments de code ou à des liens en modifiant le fichier .dgml de la carte et en ajoutant un attribut `Reference` à l'élément `<Node/>` d'un élément de code ou bien l'élément `<Link/>` pour un lien. Vous pouvez ensuite ouvrir et afficher ce contenu à partir de l'élément de code ou du lien. L’attribut `Reference` spécifie le chemin d’accès de ce contenu. Il peut s’agir d’un chemin d’accès relatif par rapport à l’emplacement du fichier .dgml ou d’un chemin d’accès absolu.

> [!CAUTION]
> Si vous utilisez des chemins d'accès relatifs, et si le fichier .dgml est déplacé vers un emplacement différent, ces chemins d'accès ne seront plus résolus. Lorsque vous essayez d'ouvrir et d'afficher le contenu lié, une erreur indiquant que le contenu ne peut pas être affiché se produit.

 Par exemple, vous souhaiterez peut-être lier les éléments de code suivants :

- Pour décrire les modifications apportées à une classe, vous pouvez lier l'URL d'un élément de code de travail, d'un document ou d'un autre fichier .dgml à l'élément de code d'une classe.

- Vous pouvez lier un diagramme de dépendance à un élément de code de groupe qui représente une couche dans l’architecture logique du logiciel.

- Pour afficher davantage d'informations sur le composant qui expose une interface, vous pouvez lier un diagramme de composant à l'élément de code de cette interface.

- Lier un élément de code à un bogue ou à un élément de travail Team Foundation Server, ou à d'autres informations qui lui sont liées.

#### <a name="to-link-a-document-or-url-to-a-code-element"></a>Pour lier un document ou une URL à un élément de code

1. Dans un éditeur XML ou un éditeur de texte, ouvrez le fichier .dgml.

2. Recherchez l'élément `<Node/>` pour l'élément de code souhaité.

3. Effectuez l'une des tâches présentées dans le tableau suivant :

    Un élément de code unique

   - Dans l'élément `<Node/>` ou `<Link/>`, ajoutez un attribut `Reference` pour spécifier l'emplacement de l'élément de code.

     > [!NOTE]
     > Il ne peut exister qu'un seul attribut `Reference` par élément.

     Exemple :

   ```xml
   <Nodes>
      <Node Id="MyNode" Reference="MyDocument.txt" />
   </Nodes>
   <Properties>
      <Property Id="Reference" Label="My Document" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    Plusieurs éléments de code

   1. Dans l'élément `<Node/>` ou `<Link/>`, ajoutez un nouvel attribut pour spécifier l'emplacement de chaque référence.

   2. Dans la section `<Properties>` :

      1. Ajoutez un élément `<Property/>` pour chaque nouveau type de référence.

      2. Définissez l'attribut `Id` au nom du nouvel attribut de référence.

      3. Ajoutez l' `IsReference` attribut et affectez-lui la valeur `True` pour faire apparaître la référence dans le menu contextuel **atteindre la référence** de l’élément de code.

      4. Utilisez l' `Label` attribut pour spécifier le texte à afficher dans le menu contextuel **atteindre la référence** de l’élément de code.

      Exemple :

   ```xml
   <Nodes>
      <Node Id="MyNode" SequenceDiagram="MySequenceDiagram.sequencediagram" ActiveBugs="MyActiveBugs.wiq"/>
   </Nodes>
   <Properties>
      <Property Id="SequenceDiagram" Label="My Sequence Diagram" DataType="System.String" IsReference="True" />
      <Property Id="ActiveBugs" Label="Active Bugs" DataType="System.String" IsReference="True" />
   </Properties>
   ```

    Sur la carte, le nom de l'élément de code apparaît souligné. Lorsque vous ouvrez le menu contextuel de l’élément de code ou du lien, vous voyez s’afficher un menu contextuel **atteindre la référence** qui contient les éléments de code liés que vous pouvez choisir.

4. Utilisez l'attribut `ReferenceTemplate` pour spécifier une chaîne commune, telle qu'une URL, qui est utilisée par plusieurs références au lieu de répéter cette chaîne dans la référence.

    L'attribut `ReferenceTemplate` spécifie un espace réservé pour la valeur de la référence. Dans l'exemple suivant, l'espace réservé `{0}` de l'attribut `ReferenceTemplate` sera remplacé par les valeurs des attributs `MyFirstReference` et `MySecondReference` de l'élément `<Node/>` pour produire un chemin d'accès complet :

   ```xml
   <Nodes>
      <Node Id="MyNode" MyFirstReference="MyFirstDocument" MySecondReference="MySecondDocument"/>
      <Node Id="MySecondNode" MyFirstReference="AnotherFirstDocument" MySecondReference="AnotherSecondDocument"/>
   </Nodes>
   <Properties>
      <Property Id="MyFirstReference" Label="My First Document" DataType="System.String" IsReference="True" ReferenceTemplate="http://www.Fabrikam.com/FirstDocuments/{0}.asp"/>
      <Property Id="MySecondReference" Label="My Second Document" DataType="System.String" IsReference="True" ReferenceTemplate=" http://www.Fabrikam.com/SecondDocuments/{0}.asp"/>
   </Properties>
   ```

5. Pour afficher le ou les éléments de code référencés à partir de la carte, ouvrez le menu contextuel de l'élément de code ou du lien. Choisissez **atteindre la référence** , puis l’élément de code.

## <a name="see-also"></a>Voir aussi

- [Mapper les dépendances à travers vos solutions](../modeling/map-dependencies-across-your-solutions.md)
- [Utiliser des cartes du code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)
- [Rechercher des problèmes potentiels à l’aide des analyseurs de carte du code](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Parcourir et réorganiser des cartes de code](../modeling/browse-and-rearrange-code-maps.md)
- [Informations de référence sur le langage DGML (Directed Graph Markup Language)](../modeling/directed-graph-markup-language-dgml-reference.md)
