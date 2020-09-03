---
title: Référence de schéma des extraits de code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- schema reference [Visual Studio]
- snippets [Visual Studio], schema reference
- code snippets [Visual Studio], schema reference
- IntelliSense Code Snippets, XML Schema
ms.assetid: 58a60621-725f-4763-93b7-62ea5424ef88
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67bc1a18b4e4cbfdf69fe917c0d0fdff09832983
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545026"
---
# <a name="code-snippets-schema-reference"></a>Référence de schéma des extraits de code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les extraits de code IntelliSense sont des parties de code précréées et prêtes à être insérées dans votre application avec [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Vous pouvez augmenter la productivité en fournissant des extraits de code qui réduisent le nombre d'heures passées à taper un code répétitif ou à rechercher des exemples. Vous pouvez utiliser le schéma XML des extraits de code IntelliSense pour créer vos propres extraits de code et les ajouter aux extraits de code que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] contient déjà.

## <a name="intellisense-code-snippets-schema-elements"></a>Éléments du schéma des extraits de code IntelliSense

|Élément|Élément|Élément|
|-|-|-|
|[Élément Assembly](../ide/code-snippets-schema-reference.md#assembly)|[Élément HelpUrl,](../ide/code-snippets-schema-reference.md#helpurl)|[References, élément](../ide/code-snippets-schema-reference.md#references)|
|[Élément Author](../ide/code-snippets-schema-reference.md#author)|[ID, élément](../ide/code-snippets-schema-reference.md#id)|[Shortcut, élément](../ide/code-snippets-schema-reference.md#shortcut)|
|[Élément de code](../ide/code-snippets-schema-reference.md#code)|[Élément Import](../ide/code-snippets-schema-reference.md#import)|[Élément Snippet](../ide/code-snippets-schema-reference.md#snippet)|
|[CodeSnippet, élément](../ide/code-snippets-schema-reference.md#codesnippet)|[Imports, élément](../ide/code-snippets-schema-reference.md#imports)|[SnippetType, élément](../ide/code-snippets-schema-reference.md#snippettype)|
|[Élément CodeSnippets,](../ide/code-snippets-schema-reference.md#codesnippets)|[Keyword, élément](../ide/code-snippets-schema-reference.md#keyword)|[Élément SnippetTypes,](../ide/code-snippets-schema-reference.md#snippettypes)|
|[Declarations, élément](../ide/code-snippets-schema-reference.md#declarations)|[Keywords, élément](../ide/code-snippets-schema-reference.md#keywords)|[Title, élément](../ide/code-snippets-schema-reference.md#title)|
|[Default, élément](../ide/code-snippets-schema-reference.md#default)|[Élément Literal](../ide/code-snippets-schema-reference.md#literal)|[ToolTip, élément](../ide/code-snippets-schema-reference.md#tooltip)|
|[Description, élément](../ide/code-snippets-schema-reference.md#description)|[Namespace, élément](../ide/code-snippets-schema-reference.md#namespace)|[Élément type](../ide/code-snippets-schema-reference.md#type)|
|[Function, élément](../ide/code-snippets-schema-reference.md#function)|[Object, élément](../ide/code-snippets-schema-reference.md#object)|[Élément URL](../ide/code-snippets-schema-reference.md#url)|
|[Header, élément](../ide/code-snippets-schema-reference.md#header)|[Reference, élément](../ide/code-snippets-schema-reference.md#reference)||

## <a name="assembly-element"></a><a name="assembly"></a> Assembly (élément)
 Spécifie le nom de l'assembly référencé par l'extrait de code.

> [!NOTE]
> L'élément `Assembly` n'est pris en charge que par les extraits de code Visual Basic.

 La valeur du texte de l’élément **Assembly** correspond soit au nom convivial de l’assembly, comme `System.dll`, soit à son nom fort, comme `System,Version=1.0.0.1,Culture=neutral,PublicKeyToken=9b35aa323c18d4fb1`.

```xml
<Assembly>
    AssemblyName
</Assembly>
```

|Élément parent|Description|
|--------------------|-----------------|
|[Reference, élément](../ide/code-snippets-schema-reference.md#reference)|Contient des informations à propos des références d'assembly requises par l'extrait de code.|

 Une valeur texte est requise. Ce texte spécifie l'assembly auquel l'extrait de code fait référence.

## <a name="author-element"></a><a name="author"></a> Author, élément
 Spécifie le nom de l'auteur de l'extrait de code. Le **Gestionnaire des extraits de code** affiche le nom stocké dans l’élément `Author` de l’extrait de code.

```xml
<Author>
   Code Snippet Author
</Author>

```

|Élément parent|Description|
|--------------------|-----------------|
|[Header, élément](../ide/code-snippets-schema-reference.md#header)|Contient des informations générales sur l'extrait de code.|

 Une valeur texte est requise. Ce texte spécifie l'auteur de l'extrait de code.

## <a name="code-element"></a><a name="code"></a> Élément Code
 Fournit de petits blocs d'extraits de code à un conteneur.

 Deux mots réservés peuvent être utilisés dans le texte de l'élément `Code` : `$end$` et `$selected$`. `$end$` marque l'emplacement pour placer le curseur après insertion de l'extrait de code. `$selected$` représente le texte sélectionné dans le document qui sera inséré dans l'extrait de code lorsqu'il est appelé. Par exemple, étant donné un extrait de code qui inclut :

```xml
$selected$ is a great color.
```

 et que le mot « Blue » est sélectionné lorsque l'utilisateur appelle le modèle, le résultat est le suivant :

```xml
Blue is a great color.
```

 Vous ne pouvez pas utiliser `$end$` ou `$selected$` plus d'une fois dans un extrait de code. Si vous le faites, seule la deuxième instance est reconnue. Étant donné un extrait de code qui inclut :

```
$selected$ is a great color. I love $selected$.
```

 si le mot « Blue » est sélectionné, le résultat est le suivant :

```
is a great color. I love Blue.
```

 L'espace initial s'affiche car il y a un espace entre `$selected$` et `is`.

 Tous les autres mots clés `$` sont définis dynamiquement dans les balises `<Literal>` et `<Object>`.

```xml
<Code Language="Language"
    Kind="method body/method decl/type decl/page/file/any"
    Delimiter="Delimiter">
    Code to insert
</Code>
```

|Attribut|Description|
|---------------|-----------------|
|`Delimiter`|Attribut facultatif. Spécifie le délimiteur utilisé pour décrire les littéraux et les objets contenus dans le code. Par défaut, le délimiteur est `$`.|
|`Kind`|Attribut facultatif. Spécifie le type de code que l'extrait de code contient et l'emplacement auquel un extrait de code doit être inséré pour que l'extrait de code puisse être compilé. Les valeurs disponibles sont `method body`, `method decl`, `type decl`, `file` et `any`.|
|`Language`|Attribut requis. Spécifie le langage de l'extrait de code.|

|Valeur d'attribut, type|Description|
|--------------------------|-----------------|
|`method body`|Spécifie que l'extrait de code est un corps de méthode, et par conséquent, qu'il doit être inséré à l'intérieur d'une déclaration de méthode.|
|`method decl`|Spécifie que l'extrait de code est une méthode, et par conséquent, qu'il doit être inséré à l'intérieur d'une classe ou d'un module.|
|`type decl`|Spécifie que l'extrait de code est un type, et par conséquent, qu'il doit être inséré à l'intérieur d'une classe, d'un module ou d'un espace de noms.|
|`file`|Spécifie que l'extrait de code est un fichier de code complet. Ces extraits de code peuvent être insérés seuls dans un fichier de code, ou à l'intérieur d'un espace de noms.|
|`any`|Spécifie que l'extrait de code peut être inséré n'importe où. Cette balise est utilisée pour les extraits de code indépendants du contexte, comme les commentaires.|

|Attribut Language, valeur|Description|
|------------------------------|-----------------|
|`VB`|Identifie un extrait de code Visual Basic.|
|`CSharp`|Identifie un extrait de code C#.|
|`CPP`|Identifie un extrait de code C++.|
|`XML`|Identifie un extrait de code XML.|
|`JavaScript`|Identifie un extrait de code JavaScript.|
|`SQL`|Identifie un extrait de code SQL.|
|`HTML`|Identifie un extrait de code HTML.|

|Élément parent|Description|
|--------------------|-----------------|
|[Élément Snippet](../ide/code-snippets-schema-reference.md#snippet)|Contient les références, importations, déclarations et code de l'extrait de code.|

 Une valeur texte est requise. Ce texte spécifie le code, avec les littéraux et les objets, que vous pouvez utiliser lorsque cet extrait de code est inséré dans un projet.

## <a name="codesnippet-element"></a><a name="codesnippet"></a> Élément CodeSnippet
 Vous permet de spécifier un titre et plusieurs extraits de code IntelliSense que vous pouvez insérer dans des fichiers de Visual Studio Code.

```xml
<CodeSnippet Format="x.x.x">
    <Header>... </Header>
    <Snippet>... </Snippet>
</CodeSnippet>

```

|Attribut|Description|
|---------------|-----------------|
|`Format`|Attribut requis. Spécifie la version de schéma de l'extrait de code. L'attribut Format doit être une chaîne dont la syntaxe est x.x.x, où chaque "x" représente une valeur numérique du numéro de version. Visual Studio ignore les extraits de code dont il ne comprend pas les attributs `Format`.|

|Élément enfant|Description|
|-------------------|-----------------|
|[Header, élément](../ide/code-snippets-schema-reference.md#header)|Élément requis. Contient des informations générales sur l'extrait de code. Il doit y avoir un seul élément `Header` dans un extrait de code.|
|[Élément Snippet](../ide/code-snippets-schema-reference.md#snippet)|Élément requis. Contient le code qui sera inséré par Visual Studio. Il doit y avoir un seul élément `Snippet` dans un extrait de code.|

|Élément parent|Description|
|--------------------|-----------------|
|[Élément CodeSnippets,](../ide/code-snippets-schema-reference.md#codesnippets)|Élément racine du schéma XML de l'extrait de code.|

## <a name="codesnippets-element"></a><a name="codesnippets"></a> Élément CodeSnippets,
 Regroupe les éléments [CodeSnippet](../ide/code-snippets-schema-reference.md#codesnippet). L'élément `CodeSnippets` est l'élément racine du schéma XML de l'extrait de code.

```xml
<CodeSnippets>
    <CodeSnippet>... </CodeSnippet>
</CodeSnippets>

```

|Élément enfant|Description|
|-------------------|-----------------|
|[CodeSnippet, élément](../ide/code-snippets-schema-reference.md#codesnippet)|Élément facultatif. Élément parent pour toutes les données d'extrait de code. Un élément `CodeSnippet` peut ne contenir aucun élément `CodeSnippets` ou en contenir plusieurs.|

## <a name="declarations-element"></a><a name="declarations"></a> Declarations, élément
 Spécifie les littéraux et les objets qui composent un extrait de code que vous pouvez modifier.

```xml
<Declarations>
    <Literal>... </Literal>
    <Object>... </Object>
</Declarations>

```

|Élément enfant|Description|
|-------------------|-----------------|
|[Élément Literal](../ide/code-snippets-schema-reference.md#literal)|Élément facultatif. Définit les littéraux de l'extrait de code que vous pouvez modifier. Un élément `Literal` peut ne contenir aucun élément `Declarations` ou en contenir plusieurs.|
|[Object, élément](../ide/code-snippets-schema-reference.md#object)|Élément facultatif. Définit les objets de l'extrait de code que vous pouvez modifier. Un élément `Object` peut ne contenir aucun élément `Declarations` ou en contenir plusieurs.|

|Élément parent|Description|
|--------------------|-----------------|
|[Élément Snippet](../ide/code-snippets-schema-reference.md#snippet)|Contient les références, importations, déclarations et code de l'extrait de code.|

## <a name="default-element"></a><a name="default"></a> Élément par défaut
 Spécifie la valeur par défaut du littéral ou de l'objet d'un extrait de code IntelliSense.

```xml
<Default>
    Default value
</Default>

```

|Élément parent|Description|
|--------------------|-----------------|
|[Élément Literal](../ide/code-snippets-schema-reference.md#literal)|Définit les champs littéraux de l'extrait de code que vous pouvez modifier.|
|[Object, élément](../ide/code-snippets-schema-reference.md#object)|Définit les champs objet de l'extrait de code que vous pouvez modifier.|

 Une valeur texte est requise. Ce texte spécifie la valeur par défaut du littéral ou de l'objet qui remplit les champs de l'extrait de code que vous pouvez modifier.

## <a name="description-element"></a><a name="description"></a> Description, élément
 Spécifie des informations relatives à la description du contenu d'un extrait de code IntelliSense.

```xml
<Description>
    Code Snippet Description
</Description>
```

|Élément parent|Description|
|--------------------|-----------------|
|[Header, élément](../ide/code-snippets-schema-reference.md#header)|Contient des informations générales sur l'extrait de code.|

 Une valeur texte est requise. Ce texte décrit l'extrait de code.

## <a name="function-element"></a><a name="function"></a> Function, élément
 Spécifie une fonction à exécuter lorsque le littéral ou l'objet reçoit le focus dans Visual Studio.

> [!NOTE]
> L’élément `Function` n’est pris en charge que par les extraits de code Visual C#.

```xml
<Function>
    FunctionName
</Function>
```

|Élément parent|Description|
|--------------------|-----------------|
|[Élément Literal](../ide/code-snippets-schema-reference.md#literal)|Définit les champs littéraux de l'extrait de code que vous pouvez modifier.|
|[Object, élément](../ide/code-snippets-schema-reference.md#object)|Définit les champs objet de l'extrait de code que vous pouvez modifier.|

 Une valeur texte est requise. Ce texte spécifie une fonction à exécuter lorsque le littéral ou le champ objet reçoit le focus dans Visual Studio.

## <a name="header-element"></a><a name="header"></a> Header, élément
 Spécifie des informations d'ordre général sur l'extrait de code IntelliSense.

```xml
<Header>
    <Title>... </Title>
    <Author>... </Author>
    <Description>... </Description>
    <HelpUrl>... </HelpUrl>
    <SnippetTypes>... </SnippetTypes>
    <Keywords>... </Keywords>
    <Shortcut>... </Shortcut>
</Header>

```

|Élément enfant|Description|
|-------------------|-----------------|
|[Élément Author](../ide/code-snippets-schema-reference.md#author)|Élément facultatif. Nom de la personne ou de la société qui a créé l'extrait de code. Il peut y avoir zéro ou un élément `Author` dans un élément `Header`.|
|[Description, élément](../ide/code-snippets-schema-reference.md#description)|Élément facultatif. Description de l'extrait de code. Il peut y avoir zéro ou un élément `Description` dans un élément `Header`.|
|[Élément HelpUrl,](../ide/code-snippets-schema-reference.md#helpurl)|Élément facultatif. URL contenant plus d'informations sur l'extrait de code. Il peut y avoir zéro ou un élément `HelpURL` dans un élément . **Remarque** : Visual Studio n’utilise pas l’élément `HelpUrl`. L'élément fait partie du schéma XML des extraits de code IntelliSense et tout extrait de code contenant l'élément est validé mais la valeur de l'élément n'est jamais utilisée.|
|[Keywords, élément](../ide/code-snippets-schema-reference.md#keywords)|Élément facultatif. Groupe les éléments `Keyword`. Il peut y avoir zéro ou un élément `Keywords` dans un élément `Header`.|
|[Shortcut, élément](../ide/code-snippets-schema-reference.md#shortcut)|Élément facultatif. Spécifie le texte du raccourci qui peut être utilisé pour insérer l'extrait de code. Il peut y avoir zéro ou un élément `Shortcut` dans un élément `Header`.|
|[Élément SnippetTypes,](../ide/code-snippets-schema-reference.md#snippettypes)|Élément facultatif. Groupe les éléments `SnippetType`. Il peut y avoir zéro ou un élément `SnippetTypes` dans un élément `Header`. S'il n'y a pas d'éléments `SnippetTypes`, l'extrait de code est toujours valide.|
|[Title, élément](../ide/code-snippets-schema-reference.md#title)|Élément requis. Nom convivial de l'extrait de code. Un élément `Title` doit contenir exactement un élément `Header`.|

|Élément parent|Description|
|--------------------|-----------------|
|[CodeSnippet, élément](../ide/code-snippets-schema-reference.md#codesnippet)|Élément parent pour toutes les données d'extrait de code.|

## <a name="helpurl-element"></a><a name="helpurl"></a> Élément HelpUrl,
 Spécifie une URL qui fournit des informations supplémentaires sur un extrait de code.

> [!NOTE]
> Visual Studio n'utilise pas l'élément `HelpUrl`. L'élément fait partie du schéma XML des extraits de code IntelliSense et tout extrait de code contenant l'élément est validé mais la valeur de l'élément n'est jamais utilisée.

```xml
<HelpUrl>
    www.microsoft.com
</HelpUrl>

```

|Élément parent|Description|
|--------------------|-----------------|
|[Header, élément](../ide/code-snippets-schema-reference.md#header)|Contient des informations générales sur l'extrait de code.|

 Une valeur texte est facultative. Ce texte spécifie l'URL à visiter pour plus d'informations sur un extrait de code.

## <a name="id-element"></a><a name="id"></a> ID, élément
 Spécifie l'identificateur unique d'un élément `Literal` ou `Object`. Deux objets ou littéraux d'un même extrait de code ne peuvent avoir la même valeur texte dans leurs éléments `ID`. Les littéraux et objets ne peuvent pas contenir d'élément `ID` avec une valeur de fin. La valeur `$end$` est réservée et utilisée pour marquer l'emplacement du curseur après que l'extrait de code a été inséré.

```xml
<ID>
    Unique Identifier
</ID>

```

|Élément parent|Description|
|--------------------|-----------------|
|[Élément Literal](../ide/code-snippets-schema-reference.md#literal)|Définit les champs littéraux de l'extrait de code que vous pouvez modifier.|
|[Object, élément](../ide/code-snippets-schema-reference.md#object)|Définit les champs objet de l'extrait de code que vous pouvez modifier.|

 Une valeur texte est requise. Ce texte spécifie l'identificateur unique de l'objet ou du littéral.

## <a name="import-element"></a><a name="import"></a> Élément Import
 Spécifie les espaces de noms importés et utilisés par un extrait de code IntelliSense.

> [!NOTE]
> L'élément `Import` est uniquement pris en charge pour les projets Visual Basic.

```xml
<Import>
    <Namespace>... </Namespace>
</Import>

```

|Élément enfant|Description|
|-------------------|-----------------|
|[Namespace, élément](../ide/code-snippets-schema-reference.md#namespace)|Élément requis. Spécifie l'espace de noms utilisé par l'extrait de code. Un élément `Namespace` doit contenir exactement un élément `Import`.|

|Élément parent|Description|
|--------------------|-----------------|
|[Imports, élément](../ide/code-snippets-schema-reference.md#imports)|Élément grouping pour les éléments **Import**.|

## <a name="imports-element"></a><a name="imports"></a> Élément Imports
 Groupe des éléments `Import` individuels.

> [!NOTE]
> L'élément `Imports` est uniquement pris en charge pour les projets Visual Basic.

```xml
<Imports>
    <Import>... </Import>
<Imports>
```

|Élément enfant|Description|
|-------------------|-----------------|
|[Élément Import](../ide/code-snippets-schema-reference.md#import)|Élément facultatif. Contient les espaces de noms importés pour l'extrait de code. Un élément **Import** peut ne contenir aucun élément `Imports` ou en contenir plusieurs.|

|Élément parent|Description|
|--------------------|-----------------|
|[Élément Snippet](../ide/code-snippets-schema-reference.md#snippet)|Contient les références, importations, déclarations et code de l'extrait de code.|

## <a name="keyword-element"></a><a name="keyword"></a> Keyword, élément
 Spécifie un mot clé personnalisé pour l'extrait de code. Les mots clés d'extrait de code sont utilisés par Visual Studio et représentent une manière standard pour les fournisseurs de contenu en ligne d'ajouter des mots clés personnalisés pour les recherches ou la catégorisation.

```xml
<Keyword>
    Code Snippet Keyword
</Keyword>
```

|Élément parent|Description|
|--------------------|-----------------|
|[Keywords, élément](../ide/code-snippets-schema-reference.md#keywords)|Groupe des éléments `Keyword` individuels.|

 Une valeur texte est requise. Mot clé pour l'extrait de code.

## <a name="keywords-element"></a><a name="keywords"></a> Keywords, élément
 Groupe des éléments `Keyword` individuels. Les mots clés d'extrait de code sont utilisés par Visual Studio et représentent une manière standard pour les fournisseurs de contenu en ligne d'ajouter des mots clés personnalisés pour les recherches ou la catégorisation.

```xml
<Keywords>
    <Keyword>... </Keyword>
    <Keyword>... </Keyword>
<Keywords>
```

|Élément enfant|Description|
|-------------------|-----------------|
|[Keyword, élément](../ide/code-snippets-schema-reference.md#keyword)|Élément facultatif. Contient les mots clés de l'extrait de code. Un élément `Keyword` peut ne contenir aucun élément `Keywords` ou en contenir plusieurs.|

|Élément parent|Description|
|--------------------|-----------------|
|[Header, élément](../ide/code-snippets-schema-reference.md#header)|Contient des informations générales sur l'extrait de code.|

## <a name="literal-element"></a><a name="literal"></a> Élément Literal
 Définit les littéraux de l'extrait de code que vous pouvez modifier. L'élément `Literal` est utilisé pour identifier le remplacement d'une partie de code entièrement contenue dans l'extrait de code, mais qui sera probablement personnalisée après avoir été insérée dans le code. Par exemple, les chaînes littérales, les valeurs numériques et certains noms de variables doivent être déclarés comme des littéraux.

 Les littéraux et les objets ne peuvent pas contenir d’élément **ID** avec la valeur selected ou end. La valeur `$selected$` représente le texte sélectionné dans le document qui sera inséré dans l'extrait de code lorsqu'il est appelé. `$end$` marque l'emplacement pour placer le curseur après insertion de l'extrait de code.

```xml
<Literal Editable="true/false">
   <ID>... </ID>
   <ToolTip>... </ToolTip>
   <Default>... </Default>
   <Function>... </Function>
</Literal>
```

|Attribut|Description|
|---------------|-----------------|
|`Editable`|Attribut `Boolean` facultatif. Spécifie si vous pouvez modifier ou non le littéral une fois l'extrait de code inséré. La valeur par défaut de cet attribut est `true`.|

|Élément enfant|Description|
|-------------------|-----------------|
|[Default, élément](../ide/code-snippets-schema-reference.md#default)|Élément requis. Spécifie la valeur par défaut du littéral lorsque vous insérez l'extrait de code. Un élément `Default` doit contenir exactement un élément `Literal`.|
|[Function, élément](../ide/code-snippets-schema-reference.md#function)|Élément facultatif. Spécifie une fonction à exécuter lorsque le littéral reçoit le focus dans Visual Studio. Il peut y avoir zéro ou un élément `Function` dans un élément `Literal`.|
|[ID, élément](../ide/code-snippets-schema-reference.md#id)|Élément requis. Spécifie l'identificateur unique du littéral. Un élément `ID` doit contenir exactement un élément `Literal`.|
|[ToolTip, élément](../ide/code-snippets-schema-reference.md#tooltip)|Élément facultatif. Décrit la valeur attendue et l'utilisation du littéral. Un élément ** peut contenir zéro ou un élément **Tooltip`Literal`.|

|Élément parent|Description|
|--------------------|-----------------|
|[Declarations, élément](../ide/code-snippets-schema-reference.md#declarations)|Contient les littéraux et les objets d'un extrait de code que vous pouvez modifier.|

## <a name="namespace-element"></a><a name="namespace"></a> Namespace, élément
 Spécifie l'espace de noms qui doit être importé pour compiler l'extrait de code et l'exécuter. L'espace de noms spécifié dans l'élément `Namespace` est ajouté automatiquement au début du code à une instruction `Imports`, s'il n'y figure pas déjà.

> [!NOTE]
> L'élément `Namespace` est uniquement pris en charge pour les projets Visual Basic.

```xml
<Namespace>
    Namespace
</Namespace>
```

|Élément parent|Description|
|--------------------|-----------------|
|[Élément Import](../ide/code-snippets-schema-reference.md#import)|Importe l'espace de noms spécifié.|

 Une valeur texte est requise. Ce texte spécifie un espace de noms que l'extrait de code considère comme importé.

## <a name="object-element"></a><a name="object"></a> Élément Object
 Définit les objets de l'extrait de code que vous pouvez modifier. L'élément `Object` est utilisé pour identifier un élément qui est requis par l'extrait de code, mais qui est vraisemblablement en dehors de l'extrait de code lui-même. Par exemple, les contrôles Windows Forms, les contrôles ASP.NET, les instances d'objet et les instances de type doivent être déclarées comme objets. Les déclarations d'objet requièrent qu'un type soit spécifié, ce qui est fait avec l'élément `Type`.

```xml
<Object Editable="true/false">
    <ID>... </ID>
    <Type>... </Type>
    <ToolTip>... </ToolTip>
    <Default>... </Default>
    <Function>... </Function>
</Object>
```

|Attribut|Description|
|---------------|-----------------|
|`Editable`|Attribut `Boolean` facultatif. Spécifie si vous pouvez modifier ou non le littéral une fois l'extrait de code inséré. La valeur par défaut de cet attribut est `true`.|

|Élément enfant|Description|
|-------------------|-----------------|
|[Default, élément](../ide/code-snippets-schema-reference.md#default)|Élément requis. Spécifie la valeur par défaut du littéral lorsque vous insérez l'extrait de code. Un élément `Default` doit contenir exactement un élément `Literal`.|
|[Function, élément](../ide/code-snippets-schema-reference.md#function)|Élément facultatif. Spécifie une fonction à exécuter lorsque le littéral reçoit le focus dans Visual Studio. Il peut y avoir zéro ou un élément `Function` dans un élément `Literal`.|
|[ID, élément](../ide/code-snippets-schema-reference.md#id)|Élément requis. Spécifie l'identificateur unique du littéral. Un élément `ID` doit contenir exactement un élément `Literal`.|
|[ToolTip, élément](../ide/code-snippets-schema-reference.md#tooltip)|Élément facultatif. Décrit la valeur attendue et l'utilisation du littéral. Un élément ** peut contenir zéro ou un élément **Tooltip`Literal`.|
|[Élément type](../ide/code-snippets-schema-reference.md#type)|Élément requis. Spécifie le type de l'objet. Un élément `Type` doit contenir exactement un élément `Object`.|

|Élément parent|Description|
|--------------------|-----------------|
|[Declarations, élément](../ide/code-snippets-schema-reference.md#declarations)|Contient les littéraux et les objets d'un extrait de code que vous pouvez modifier.|

## <a name="reference-element"></a><a name="reference"></a> Reference, élément
 Spécifie des informations sur les références d'assembly requises par l'extrait de code.

> [!NOTE]
> L'élément `Reference` est uniquement pris en charge pour les projets Visual Basic.

```xml
<Reference>
    <Assembly>... </Assembly>
    <Url>... </Url>
</Reference>
```

|Élément enfant|Description|
|-------------------|-----------------|
|[Élément Assembly](../ide/code-snippets-schema-reference.md#assembly)|Élément requis. Spécifie le nom de l'assembly référencé par l'extrait de code. Un élément `Assembly` doit contenir exactement un élément `Reference`.|
|[Élément URL](../ide/code-snippets-schema-reference.md#url)|Élément facultatif. Contient une URL qui fournit plus d'informations sur l'assembly référencé. Il peut y avoir zéro ou un élément `Url` dans un élément `Reference`.|

|Élément parent|Description|
|--------------------|-----------------|
|[References, élément](../ide/code-snippets-schema-reference.md#references)|Élément de regroupement pour les éléments `Reference`.|

## <a name="references-element"></a><a name="references"></a> References, élément
 Groupe des éléments `Reference` individuels.

> [!NOTE]
> L'élément `References` est uniquement pris en charge pour les projets Visual Basic.

```xml
<References>
    <Reference>... </Reference>
</References>
```

|Élément enfant|Description|
|-------------------|-----------------|
|[Reference, élément](../ide/code-snippets-schema-reference.md#reference)|Élément facultatif. Contient des informations à propos des références d'assembly de l'extrait de code. Un élément `Reference` peut ne contenir aucun élément `References` ou en contenir plusieurs.|

|Élément parent|Description|
|--------------------|-----------------|
|[Élément Snippet](../ide/code-snippets-schema-reference.md#snippet)|Contient les références, importations, déclarations et code de l'extrait de code.|

## <a name="shortcut-element"></a><a name="shortcut"></a> Shortcut, élément
 Spécifie le texte de raccourci utilisé pour insérer l'extrait de code. La valeur texte d'un élément `Shortcut` peut contenir uniquement des signes alphanumériques, des traits d'union (-) et des traits de soulignement (_).

> [!CAUTION]
> _ et – ne sont pas des caractères pris en charge dans les raccourcis de l'extrait de code C++.

```xml
<Shortcut>
    Shortcut Text
</Shortcut>
```

|Élément parent|Description|
|--------------------|-----------------|
|[Header, élément](../ide/code-snippets-schema-reference.md#header)|Contient des informations générales sur l'extrait de code.|

 Une valeur texte est facultative. Ce texte est utilisé comme raccourci pour insérer l'extrait de code.

## <a name="snippet-element"></a><a name="snippet"></a> Élément Snippet
 Spécifie les références, les importations, les déclarations et le code de l'extrait de code.

```xml
<Snippet>
    <References>... </References>
    <Imports>... </Imports>
    <Declarations>... </Declarations>
    <Code>... </Code>
</Snippet>

```

|Élément enfant|Description|
|-------------------|-----------------|
|[Élément de code](../ide/code-snippets-schema-reference.md#code)|Élément requis. Spécifie le code que vous souhaitez insérer dans un fichier documentation. Un élément `Code` doit contenir exactement un élément `Snippet`.|
|[Declarations, élément](../ide/code-snippets-schema-reference.md#declarations)|Élément facultatif. Spécifie les littéraux et les objets qui composent un extrait de code que vous pouvez modifier. Il peut y avoir zéro ou un élément `Declarations` dans un élément `Snippet`.|
|[Imports, élément](../ide/code-snippets-schema-reference.md#imports)|Élément facultatif. Groupe des éléments `Import` individuels. Il peut y avoir zéro ou un élément `Imports` dans un élément `Snippet`.|
||Élément facultatif. Groupe des éléments `Reference` individuels. Il peut y avoir zéro ou un élément `References` dans un élément `Snippet`.|

|Élément parent|Description|
|--------------------|-----------------|
|[CodeSnippet, élément](../ide/code-snippets-schema-reference.md#codesnippet)|Vous permet de spécifier un titre et plusieurs extraits de code IntelliSense que vous pouvez insérer dans des fichiers de Visual Studio Code.|

## <a name="snippettype-element"></a><a name="snippettype"></a> SnippetType, élément
 Spécifie la manière dont Visual Studio insère l'extrait de code.

```xml
<SnippetType>
    SurroundsWith/Expansion
<SnippetType>
```

|Élément parent|Description|
|--------------------|-----------------|
|[Élément SnippetTypes,](../ide/code-snippets-schema-reference.md#snippettypes)|Groupe les éléments `SnippetType`.|

 Le texte doit avoir l'une des valeurs suivantes :

- `SurroundsWith` : autorise à placer l'extrait de code autour d'une partie de code sélectionnée.

- `Expansion` : autorise à insérer l'extrait de code au curseur.

- `Refactoring` : spécifie que l'extrait de code est utilisé pendant la refactorisation Visual C#. `Refactoring` ne peut pas être utilisé dans les extraits de code personnalisés.

## <a name="snippettypes-element"></a><a name="snippettypes"></a> SnippetTypes, élément
 Groupe des éléments `SnippetType` individuels. Si l'élément `SnippetTypes` est absent, l'extrait de code peut être inséré n'importe où dans le code.

```xml
<SnippetTypes>
    <SnippetType>... </SnippetType>
    <SnippetType>... </SnippetType>
<SnippetTypes>
```

|Élément enfant|Description|
|-------------------|-----------------|
|[SnippetType, élément](../ide/code-snippets-schema-reference.md#snippettype)|Élément facultatif. Spécifie la manière dont Visual Studio insère l'extrait de code dans le code. Un élément `SnippetType` peut ne contenir aucun élément `SnippetTypes` ou en contenir plusieurs.|

|Élément parent|Description|
|--------------------|-----------------|
|[Header, élément](../ide/code-snippets-schema-reference.md#header)|Spécifie des informations générales sur l'extrait de code.|

## <a name="title-element"></a><a name="title"></a> Title, élément
 Spécifie le titre de l'extrait de code. Le titre stocké dans l’élément `Title` de l’extrait de code apparaît dans le **Sélecteur d’extraits de code**, ainsi que dans la description de l’extrait de code située dans le **Gestionnaire des extraits de code**.

```xml
<Title>
    Code Snippet Title
<Title>
```

|Élément parent|Description|
|--------------------|-----------------|
|[Header, élément](../ide/code-snippets-schema-reference.md#header)|Spécifie des informations générales sur l'extrait de code.|

 Une valeur texte est requise. Ce texte spécifie le titre de l'extrait de code.

## <a name="tooltip-element"></a><a name="tooltip"></a> ToolTip, élément
 Décrit la valeur attendue et l'utilisation d'un littéral ou d'un objet d'extrait de code que Visual Studio affiche dans une info-bulle lorsqu'il insère l'extrait de code dans un projet. Le texte d'Info-bulle est affiché lorsque la souris pointe sur le littéral ou sur l'objet après que l'extrait de code a été inséré.

```xml
<ToolTip>
    ToolTip description
</ToolTip>
```

|Élément parent|Description|
|--------------------|-----------------|
|[Élément Literal](../ide/code-snippets-schema-reference.md#literal)|Définit les champs littéraux de l'extrait de code que vous pouvez modifier.|
|[Object, élément](../ide/code-snippets-schema-reference.md#object)|Définit les champs objet de l'extrait de code que vous pouvez modifier.|

 Une valeur texte est requise. Ce texte spécifie la description de l'info-bulle à associer à l'objet ou au littéral dans l'extrait de code.

## <a name="type-element"></a><a name="type"></a> Élément type
 Spécifie le type de l'objet. L'élément `Object` est utilisé pour identifier un élément qui est requis par l'extrait de code, mais qui est vraisemblablement en dehors de l'extrait de code lui-même. Par exemple, les contrôles Windows Forms, les contrôles ASP.NET, les instances d'objet et les instances de type doivent être déclarées comme objets. Les déclarations d'objet requièrent qu'un type soit spécifié, ce qui est fait avec l'élément `Type`.

```xml
<Type>
    Type
</Type>
```

|Élément parent|Description|
|--------------------|-----------------|
|[Object, élément](../ide/code-snippets-schema-reference.md#object)|Définit les champs objet de l'extrait de code que vous pouvez modifier.|

 Une valeur texte est requise. Ce texte spécifie le type de l'objet.

## <a name="url-element"></a><a name="url"></a> Élément URL
 Spécifie une URL qui fournit des informations supplémentaires sur l'assembly référencé.

> [!NOTE]
> L'élément `Url` est uniquement pris en charge pour les projets Visual Basic.

```xml
<Url>
    www.microsoft.com
</Url>
```

|Élément parent|Description|
|--------------------|-----------------|
|[Reference, élément](../ide/code-snippets-schema-reference.md#reference)|Spécifie les références d'assembly requises par l'extrait de code.|

 Une valeur texte est requise. Ce texte spécifie une URL avec plus d'informations sur l'assembly référencé. Cette URL est affichée lorsque la référence ne peut pas être ajoutée au projet.

## <a name="see-also"></a>Voir aussi
 [Code Snippets](../ide/code-snippets.md) [Procédures pas à pas des extraits de code : création d’un extrait de code](../ide/walkthrough-creating-a-code-snippet.md)
